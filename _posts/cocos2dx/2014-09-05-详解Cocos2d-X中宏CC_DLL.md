---
layout: post
title: 详解Cocos2d-X中宏CC_DLL
category: 游戏技术
tags: cocos2dx
keywords:
description: 
---
cocos2d-x的源码中，经常可以看到宏CC_DLL的使用，比如在类CCScene的定义中：

    class CC_DLL CCScene : public CCNode
    {public:
        CCScene();
        virtual ~CCScene();
        bool init();

        static CCScene *create(void);
    };

在cocos2d-x中，根据不同的平台，宏CC_DLL的定义是不同的，在iOS/Android/Blackberry/Mac平台上，CC_DLL代表“空”：

    #define CC_DLL
在win32平台上，CC_DLL的定义为：

    #if defined(_USRDLL)
    #define CC_DLL     __declspec(dllexport)#else         /* use a DLL library */
    #define CC_DLL     __declspec(dllimport)#endif
在linux平台上，CC_DLL的定义为：

    #if defined(_USRDLL)#define CC_DLL __attribute__ ((visibility ("default")))#else         /* use a DLL library */#define CC_DLL __attribute__ ((visibility ("default")))#endif
对于win32，需要明白__declspec(dllexport)和__declspec(dllimport)的功能。

__declspec(dllexport)

声明一个导出函数，是说这个函数要从本DLL导出。我要给别人用。一般用于dll中省掉在DEF文件中手工定义导出哪些函数的一个方法。当然，如果你的DLL里全是C++的类的话，你无法在DEF里指定导出的函数，只能用__declspec(dllexport)导出类。


     //SimpleDLLClass.h  #ifdef SIMPLEDLL_EXPORT#define DLL_EXPORT     __declspec(dllexport)#else #define DLL_EXPORT#endif class DLL_EXPORT     
    SimpleDLLClass {
    public: 
    SimpleDLLClass(); 
    virtual ~SimpleDLLClass(); 
    virtual getValue() { return m_nValue;};private: 
    int m_nValue;
    };

    //SimpleDLLClass.cpp  #include "SimpleDLLClass.h"     
    SimpleDLLClass::SimpleDLLClass()
    { 
        m_nValue=0;
    }

    SimpleDLLClass::~SimpleDLLClass()
    {
    }

对于上述代码，如果定义了SIMPLEDLL_EXPORT，那上述代码会被编译生成dll文件，此dll文件会向其他程序模块提供类SimpleDLLClass的函数和变量调用。

 

__declspec(dllimport)

声明一个导入函数，是说这个函数是从别的DLL导入。我要用。一般用于使用某个dll的exe中 。

不使用 __declspec(dllimport) 也能正确编译代码，但使用 __declspec(dllimport) 使编译器可以生成更好的代码。编译器之所以能够生成更好的代码，是因为它可以确定函数是否存在于 DLL 中，这使得编译器可以生成跳过间接寻址级别的代码，而这些代码通常会出现在跨 DLL 边界的函数调用中。但是，必须使用 __declspec(dllimport) 才能导入 DLL 中使用的变量。

在Windows DLL编程时，可使用__declspec(dllimport)关键字导入函数或者变量。

函数的导入
    当你需要使用DLL中的函数时，往往不需要显示地导入函数，编译器可自动完成。但如果你显示地导入函数，编译器会产生质量更好的代码。由于编译器确切地知道了一个函数是否在一个DLL中，它就可以产生更好的代码，不再需要间接的调用转接。
 
 	Win32的PE格式（Portable Executable Format）把所有导入地址放在一个导入地址表中。下面用一个具体实例说明使用__declspec(dllimport)导入函数和不使用的区别：
 
 	假设func是一个DLL中的函数，现在在要生成的.exe的main函数中调用func函数，并且不显示地导入func函数（即没有：__declspec(dllimport)），代码示例如下：
 	
    int main()
    {
        func();
    }
编译器将产生类似这样的调用代码：

    call func
然后，链接器把该调用翻译为类似这样的代码：

    call 0x40000001; //0x40000001是func的地址
并且，链接器将产生一个Thunk，形如：

    0x40000001: jmp DWORD PTR __imp_func
这里的imp_func是func函数在.exe的导入地址表中的函数槽的地址。然后，加载器只需要在加载时更新.exe的导入地址表即可。
 
    而如果使用了__declspec(dllimport)显示地导入函数，那么链接器就不会产生Thunk（如果不被要求的话），而直接产生一个间接调用。因此，下面的代码：

    __declspec(dllimport) void func1(void);void main(void) 
    {
        func1();
    }
将调用如下调用指令：

    call DWORD PTR __imp_func1
因此，显示地导入函数能有效减少目标代码（因为不产生Thunk）。另外，在DLL中使用DLL外的函数也可以这样做，从而提高空间和时间效率。

变量的导入
    与函数不同的是，在使用DLL中的变量时，需要显示地导入变量。使用__declspec(dllimport)关键字导入变量。若在DLL中使用.def导出变量，则应使用DATA修饰变量，而不是使用已经被遗弃的CONSTANT。因为CONSTANT可能需要使用指针间接访问变量，不确定什么时候会出问题。
 我相信写WIN32程序的人，做过DLL，都会很清楚__declspec(dllexport)的作用，它就是为了省掉在DEF文件中手工定义导出哪些 函数的一个方法。当然，如果你的DLL里全是C++的类的话，你无法在DEF里指定导出的函数，只能用__declspec(dllexport)导出 类。但是，MSDN文档里面，对于__declspec(dllimport)的说明让人感觉有点奇怪，先来看看MSDN里面是怎么说的： 

不使用 __declspec(dllimport) 也能正确编译代码，但使用 __declspec(dllimport) 使编译器可以生成更好的代码。编译器之所以能够生成更好的代码，是因为它可以确定函数是否存在于 DLL 中，这使得编译器可以生成跳过间接寻址级别的代码，而这些代码通常会出现在跨 DLL 边界的函数调用中。但是，必须使用 __declspec(dllimport) 才能导入 DLL 中使用的变量。

初看起来，这段话前面的意思是，不用它也可以正常使用DLL的导出库，但最后一句话又说，必须使用 __declspec(dllimport) 才能导入 DLL 中使用的变量这个是什么意思？？

那我就来试验一下，假定，你在DLL里只导出一个简单的类，我们在下面的代码中导入使用这个DLL中的类，注意，我假定你已经在项目属性中定义了 SIMPLEDLL_EXPORT。

    //SimpleDLLClass.h #ifdef SIMPLEDLL_EXPORT
    #define DLL_EXPORT __declspec(dllexport)
    #else
    #define DLL_EXPORT
    #endif

    class DLL_EXPORT SimpleDLLClass
    {
    public: 
        SimpleDLLClass(); 
        virtual ~SimpleDLLClass(); 
        virtual getValue() { return m_nValue;};
    private: 
        int m_nValue;
    };

    //SimpleDLLClass.cpp

    #include "SimpleDLLClass.h"

    SimpleDLLClass::SimpleDLLClass()
    { 
        m_nValue=0;
    }

    SimpleDLLClass::~SimpleDLLClass()
    {
    }
然后你再使用这个DLL类，在你的APP中include SimpleDLLClass.h时，你的APP的项目不用定义 SIMPLEDLL_EXPORT 所以，DLL_EXPORT 就不会存在了，这个时候，你在APP中，不会遇到问题。这正好对应MSDN上说的__declspec(dllimport)定义与否都可以正常使用。但我们也没有遇到变量不能正常使用呀。 那好，我们改一下SimpleDLLClass,把它的m_nValue改成static,然后在cpp文件中加一行int SimpleDLLClass::m_nValue=0;如果你不知道为什么要加这一行，那就回去看看C++的基础。

改完之后，再去LINK一下，你的APP，看结果如何， 结果是LINK告诉你找不到这个m_nValue。明明已经定义了，为什么又没有了？？ 肯定是因为我把m_nValue定义为static的原因。但如果我一定要使用Singleton的Design Pattern的话，那这个类肯定是要有一个静态成员，每次LINK都没有，那不是完了？ 如果你有Platform SDK，用里面的Depend程序看一下，DLL中又的确是有这个m_nValue导出的呀。

再回去看看我引用MSDN的那段话的最后一句。 那我们再改一下SimpleDLLClass.h，把那段改成下面的样子:

    #ifdef SIMPLEDLL_EXPORT#define DLL_EXPORT __declspec(dllexport)#else #define DLL_EXPORT __declspec(dllimport)#endif
再LINK，一切正常。原来dllimport是为了更好的处理类中的静态成员变量的，如果没有静态成员变量，那么这个__declspec(dllimport)无所谓。

 关于__declspec(dllexport)和__declspec(dllimport)的使用，参考了这篇博文：[http://www.cnblogs.com/xd502djj/archive/2010/09/21/1832493.html](http://www.cnblogs.com/xd502djj/archive/2010/09/21/1832493.html)

 关于linux平台上的CC_DLL解释有待下次添加。
#Reference
* [http://www.cnblogs.com/mingfish/archive/2013/07/09/3180652.html](http://www.cnblogs.com/mingfish/archive/2013/07/09/3180652.html)






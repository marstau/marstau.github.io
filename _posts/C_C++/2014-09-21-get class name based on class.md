---
layout: post
title: get class name based on class
category: 编程开发
tags: Ｃ／Ｃ＋＋
keywords: 
description: 
---

You can display the name of a variable by using the preprocessor. For instance

```
# include <iostream>
# define quote(x) #x
class one {};
int main(){
    one A;
    std::cout<<typeid(A).name()<<"\t"<< quote(A) <<"\n";
    return 0;
}
```
outputs

```
3one    A
```
on my machine. The # changes a token into a string, after preprocessing the line is

```
std::cout<<typeid(A).name()<<"\t"<< "A" <<"\n";
```
Of course if you do something like

```
void foo(one B){
    std::cout<<typeid(B).name()<<"\t"<< quote(B) <<"\n";
}
int main(){
    one A;
    foo(A);
    return 0;
}
```
you will get

```
3one B
```
as the compiler doesn't keep track of all of the variable's names.

As it happens in gcc the result of typeid().name() is the mangled class name, to get the demangled version use

```
# include <iostream>
# include <cxxabi.h>
# define quote(x) #x
template <typename foo,typename bar> class one{ };
int main(){
    one<int,one<double, int> > A;
    int status;
    char * demangled = abi::__cxa_demangle(typeid(A).name(),0,0,&status);
    std::cout<<demangled<<"\t"<< quote(A) <<"\n";
    free(demangled);
    return 0;
}
```
which gives me

```
one<int, one<double, int> > A
```
Other compilers may use different naming schemes.


```
# define quote(x) #x
template<typename T1, typename T2>
void GameManager::changeState(T1 *oldState, T2 *newState){
    GLOG(GDEBUG,"changeState");
    CHECK(_curScene != nullptr);
    
    CCASSERT(_curScene != nullptr, "parent shouldn't have to be nil");
    
    oldState->removeFromParentAndCleanup(true);
    
    int status;
    
    char * demangled = abi::__cxa_demangle(typeid(*newState).name(),0,0,&status);
    free(demangled);
    
    GLOG(GDEBUG,"typeid name=" << typeid(*newState).name() << ", macro=" << quote(T2) << ", demangled=" << demangled);
    cocos2d::Node *newCCBNode = registerCCBNode<T2>("StartScene", "loading.ccbi");
    
    _curScene->addChild(newCCBNode);
}
```
output:

```
 [typeid name=N7NewWing10NWRegisterE, macro=T2, demangled=NewWing::NWRegister]
```

## Reference
* <http://stackoverflow.com/questions/3649278/how-can-i-get-the-class-name-from-a-c-object>
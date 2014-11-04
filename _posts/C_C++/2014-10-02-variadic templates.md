---
layout: post
title: variadic templates
category: 游戏技术
tags: Ｃ／Ｃ＋＋
keywords: variadic templates
description: 
---

I'll describe some caution when using variadic templates, just see below codes:

```
void print (){
    cout << "print" << endl;}
void print(int a){
    cout << "int=" << a << endl;
}

void print(const string &a){
    cout << "string=" << a << endl;
}

void print(const double a){
    cout << "double=" << a << endl;
}
template <typename T, typename... Types>void print (const T& firstArg, const Types&... args){
    print(firstArg);    print(args...);}
```
useage:

```
print(1);
/*
int=1
*/
     
print(1, 2, 1.0);
/*
int=1
int=2
double=1
*/
```

However, when pass string type, the problem exposes.

```
print("d");
/*
error: stack overflow.
*/

```
*****

So, you should avoid to invoke print(firstArg), which overrides print variadic template function, just modify to below solving the problem:

```

template<typename T>
void print(const T &a){
    int status;
    
    char * demangled = abi::__cxa_demangle(typeid(T).name(),0,0,&status);

    cout << "T=" << a << ", demangled=" << demangled << endl;
    free(demangled);
}
template <typename T, typename... Types>void print (const T& firstArg, const Types&... args){
    print(firstArg);    print(args...);}

void print2(){
    cout << "print2" << endl;
}
template <typename T, typename... Types>void print2 (const T& firstArg, const Types&... args){
    cout << "firstArg=" << firstArg << endl;    print2(args...);}
```


```
print("d");
print2("d");
/*
T=d, demangled=char [2]
firstArg=d
print2
*/
```

可见,先解析通用的模板参数,若找到最合适的则不会去解析不定模板参数,而之前因为"d"必须先隐式转换为string才能调用之前的print,所以会去解析不定模板参数的函数.

*****
关于

```
void print(){
    cout << "print" << endl;
}
```
定义的必须性的问题：

```
void print(){
    cout << "print" << endl;
}

void print(const int val){
    cout << "int=" << val << endl;
}
template <typename T, typename... Types>void print (const T& firstArg, const Types&... args){
    cout << "firstArg=" << firstArg << endl;    print(args...);}
```

```
print("d", 1);

cout << "-" << endl;
print("c");
    
/*
firstArg=d
int=1
-
firstArg=c
print
*/
    
```
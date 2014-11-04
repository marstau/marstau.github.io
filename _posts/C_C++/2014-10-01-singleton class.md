---
layout: post
title: singleton class
category: 游戏技术
tags: Ｃ／Ｃ＋＋
keywords: singleton
description: 
---

I'll describe my singleton class, a template singleton. Explain some details.
##SingletonProtocol.h

```
#pragma once
#include "STDHeader.h"
#include "g3log.hpp"

template<typename SingletonClass>
class SingletonProtocol{
public:
    static SingletonClass *GetInstance(){
        if (_Instance == nullptr){
            _Instance = new (std::nothrow) SingletonClass;
            CHECK( _Instance != nullptr );
            
            LOG(GINFO, "_Garbo=" << &_Garbo); // Use _Garbo, In case of compiler optimization
            SingletonProtocol *singleton = _Instance; // Declare a temporary Up-conversion, ensure return _Instance statement is ok.
            singleton->init();
        }
        return _Instance;
    }
    
protected:
    SingletonProtocol(){}
    virtual void init() = 0;
private:
    /** \brief prohibit operation*/
    SingletonProtocol( const SingletonProtocol<SingletonClass> & ) = delete;
    
    /** \brief prohibit operation*/
    SingletonProtocol& operator=(const SingletonProtocol<SingletonClass> &) = delete;
    
public:
    class Garbo{
    public:
        Garbo(){} // If delete. show error Default initialization of an object of const type 'const typename SingletonProtocol<ResourceManager>::Garbo' requires a user-provided default constructor.
        ~Garbo(){
            GLOG(GDEBUG, "-");
            
            delete SingletonClass::_Instance, SingletonClass::_Instance = nullptr;
        }
    };
private:
    static SingletonClass *_Instance;
    
    static const Garbo _Garbo;
    
};

#include "SingletonProtocol.hpp"
```

##SingletonProtocol.hpp

```
template<typename T>
const typename SingletonProtocol<T>::Garbo SingletonProtocol<T>::_Garbo;

template<typename T>
T *SingletonProtocol<T>::_Instance;
```

##Usage

```
class ResourceManager :
public SingletonProtocol<ResourceManager>
{
protected:
    void init() override;
};
```

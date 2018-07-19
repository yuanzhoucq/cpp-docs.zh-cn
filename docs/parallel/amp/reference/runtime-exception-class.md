---
title: runtime_exception 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- runtime_exception
- AMPRT/runtime_exception
- AMPRT/Concurrency::runtime_exception
- AMPRT/Concurrency::runtime_exception::get_error_code
dev_langs:
- C++
helpviewer_keywords:
- runtime_exception class
ms.assetid: 8fe3ce2c-3d4c-4b9c-95e8-e592f37adefd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ff10cb3958ffa82e3ef2bb70d8370d1a52c4a929
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33695741"
---
# <a name="runtimeexception-class"></a>runtime_exception 类
C++ Accelerated Massive Parallelism (AMP) 库中的异常的基类型。  
  
### <a name="syntax"></a>语法  
  
```  
class runtime_exception : public std::exception;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[runtime_exception 构造函数](#ctor)|初始化 `runtime_exception` 类的新实例。|  
|[~ runtime_exception 析构函数](#dtor)|销毁`runtime_exception`对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[get_error_code](#runtime_exception__get_error_code)|返回导致异常的错误代码。|  

  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[operator=](#operator_eq)|将指定的内容复制`runtime_exception`到此对象。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `exception`  
  
 `runtime_exception`  
  
## <a name="requirements"></a>要求  
 **标头：** amprt.h  
  
 **命名空间：** 并发  

## <a name="runtime_exception__ctor"></a>  runtime_exception 构造函数  
初始化类的新实例。  
  
### <a name="syntax"></a>语法  
  
```  
runtime_exception(  
    const char * _Message,  
    HRESULT _Hresult ) throw();  
  
explicit runtime_exception(  
    HRESULT _Hresult ) throw();  
  
runtime_exception(  
    const runtime_exception & _Other ) throw();  
```  
  
### <a name="parameters"></a>参数  
 `_Message`  
 导致异常的错误说明。  
  
 `_Hresult`  
 导致异常的错误的 HRESULT。  
  
 `_Other`  
 `runtime_exception`要复制的对象。  
  
### <a name="return-value"></a>返回值  
 `runtime_exception` 对象。  

## <a name="dtor"></a>  ~ runtime_exception 析构函数  
销毁对象。  
  
### <a name="syntax"></a>语法  
  
```  
virtual ~runtime_exception() throw();  
```  
  
## <a name="runtime_exception__get_error_code"></a>  get_error_code   
返回导致异常的错误代码。  
  
### <a name="syntax"></a>语法  
  
```  
HRESULT get_error_code() const throw();  
```  
  
### <a name="return-value"></a>返回值  
 导致异常的错误的 HRESULT。  
  
## <a name="runtime_exception__operator_eq"></a>operator=   
  将指定的内容复制`runtime_exception`到此对象。  
  
### <a name="syntax"></a>语法  
  
```  
runtime_exception & operator= (    const runtime_exception & _Other ) throw();  
```  
  
### <a name="parameters"></a>参数  
 `_Other`  
 `runtime_exception`要复制的对象。  
  
### <a name="return-value"></a>返回值  
 对此引用`runtime_exception`对象。  
  

  
## <a name="see-also"></a>请参阅  
 [并发命名空间 (C++ AMP)](concurrency-namespace-cpp-amp.md)

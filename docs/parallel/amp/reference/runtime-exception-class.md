---
title: runtime_exception 类
ms.date: 03/27/2019
f1_keywords:
- runtime_exception
- AMPRT/runtime_exception
- AMPRT/Concurrency::runtime_exception
- AMPRT/Concurrency::runtime_exception::get_error_code
helpviewer_keywords:
- runtime_exception class
ms.assetid: 8fe3ce2c-3d4c-4b9c-95e8-e592f37adefd
ms.openlocfilehash: ff54357055d373db98f469b071edc75fce75e0b4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336794"
---
# <a name="runtime_exception-class"></a>runtime_exception 类

C++ Accelerated Massive Parallelism (AMP) 库中的异常的基类型。

### <a name="syntax"></a>语法

```cpp
class runtime_exception : public std::exception;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[runtime_exception构造函数](#ctor)|初始化 `runtime_exception` 类的新实例。|
|[*runtime_exception析构器](#dtor)|销毁`runtime_exception`对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[get_error_code](#get_error_code)|返回导致异常的错误代码。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[运算符*](#operator_eq)|将指定`runtime_exception`对象的内容复制到此对象中。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`exception`

`runtime_exception`

## <a name="requirements"></a>要求

**标题：** amprt.h

**命名空间：** 并发

## <a name="runtime_exception-constructor"></a><a name="ctor"></a>runtime_exception构造函数

初始化此类的新实例。

### <a name="syntax"></a>语法

```cpp
runtime_exception(
    const char * _Message,
    HRESULT _Hresult ) throw();

explicit runtime_exception(
    HRESULT _Hresult ) throw();

runtime_exception(
    const runtime_exception & _Other ) throw();
```

### <a name="parameters"></a>参数

*_Message*<br/>
导致异常的错误的说明。

*_Hresult*<br/>
导致异常的错误的 HRESULT。

*_Other*<br/>
要复制的 `runtime_exception` 对象。

### <a name="return-value"></a>返回值

`runtime_exception` 对象。

## <a name="runtime_exception-destructor"></a><a name="dtor"></a>*runtime_exception析构器

销毁对象。

### <a name="syntax"></a>语法

```cpp
virtual ~runtime_exception() throw();
```

## <a name="get_error_code"></a><a name="get_error_code"></a>get_error_code

返回导致异常的错误代码。

### <a name="syntax"></a>语法

```cpp
HRESULT get_error_code() const throw();
```

### <a name="return-value"></a>返回值

导致异常的错误的 HRESULT。

## <a name="operator"></a><a name="operator_eq"></a>运算符*

将指定`runtime_exception`对象的内容复制到此对象中。

### <a name="syntax"></a>语法

```cpp
runtime_exception & operator= (    const runtime_exception & _Other ) throw();
```

### <a name="parameters"></a>参数

*_Other*<br/>
要复制的 `runtime_exception` 对象。

### <a name="return-value"></a>返回值

对此`runtime_exception`对象的引用。

## <a name="see-also"></a>另请参阅

[Concurrency 命名空间 (C++ AMP)](concurrency-namespace-cpp-amp.md)

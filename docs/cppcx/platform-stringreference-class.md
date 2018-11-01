---
title: Platform::StringReference 类
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::StringReference::StringReference
- VCCORLIB/Platform::StringReference::Data
- VCCORLIB/Platform::StringReference::Length
- VCCORLIB/Platform::StringReference::GetHSTRING
- VCCORLIB/Platform::StringReference::GetString
ms.assetid: 2d09c7ec-0f16-458e-83ed-7225a1b9221e
ms.openlocfilehash: 09b15a1530661ce537c9d2aab333a1a17fa52ff9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50498379"
---
# <a name="platformstringreference-class"></a>Platform::StringReference 类

可以用于通过最少复制操作将字符串数据从 `Platform::String^` 输入参数传递到其他方法的优化类型。

## <a name="syntax"></a>语法

```cpp
class StringReference
```

### <a name="remarks"></a>备注

### <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[StringReference::StringReference](#ctor)|两个用于创建 `StringReference`实例的构造函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[StringReference::Data](#data)|返回 char16 值数组形式的字符串数据。|
|[StringReference::Length](#length)|返回字符串中的字符数。|
|[StringReference::GetHSTRING](#gethstring)|返回 HSTRING 形式的字符串数据。|
|[StringReference::GetString](#getstring)|返回 `Platform::String^`形式的字符串数据。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[StringReference::operator=](#operator-assign)|将 `StringReference` 分配给新 `StringReference` 实例。|
|[StringReference::operator()](#operator-call)|将 `StringReference` 转换为 `Platform::String^`。|

### <a name="requirements"></a>要求

**支持的最低客户端：** Windows 8

**支持的最低服务器：** Windows Server 2012

**命名空间：** Platform

**标头：** vccorlib.h

## <a name="data"></a>  Stringreference:: Data 方法

以 char16 值数组形式返回此 `StringReference` 的内容。

### <a name="syntax"></a>语法

```cpp
const ::default::char16 * Data() const;
```

### <a name="return-value"></a>返回值

char16 UNICODE 文本字符的数组。

## <a name="gethstring"></a>  Stringreference:: Gethstring 方法

以 `__abi_HSTRING` 形式返回字符串内容。

### <a name="syntax"></a>语法

```cpp
__abi_HSTRING GetHSTRING() const;
```

### <a name="return-value"></a>返回值

一个包含字符串数据的 `__abi_HSTRING`。

### <a name="remarks"></a>备注

## <a name="getstring"></a>  Stringreference:: Getstring 方法

以 `Platform::String^` 形式返回字符串内容。

### <a name="syntax"></a>语法

```cpp
__declspec(no_release_return) __declspec(no_refcount)
    ::Platform::String^ GetString() const;
```

### <a name="return-value"></a>返回值

一个包含字符串数据的 `Platform::String^`。

## <a name="length"></a>  Stringreference:: Length 方法

返回字符串中的字符数。

### <a name="syntax"></a>语法

```cpp
unsigned int Length() const;
```

### <a name="return-value"></a>返回值

指定字符串中字符数的无符号整数。

### <a name="remarks"></a>备注

## <a name="operator-assign"></a>  Stringreference:: Operator = 运算符

将指定对象分配给当前 `StringReference` 对象。

### <a name="syntax"></a>语法

```cpp
StringReference& operator=(const StringReference& __fstrArg);
StringReference& operator=(const ::default::char16* __strArg);
```

### <a name="parameters"></a>参数

*__fstrArg*<br/>
用于初始化当前 `StringReference` 对象的 `StringReference` 对象的地址。

*__strArg*<br/>
指向用于初始化当前 `StringReference` 对象的 char16 值数组的指针。

### <a name="return-value"></a>返回值

对类型为 `StringReference` 的对象的引用。

### <a name="remarks"></a>备注

因为`StringReference`是标准 c + + 类而不是 ref 类，它不会出现在**对象浏览器**。

## <a name="operator-call"></a>  StringReference::operator() 运算符

将 `StringReference` 对象转换为 `Platform::String^` 对象。

### <a name="syntax"></a>语法

```cpp
__declspec(no_release_return) __declspec(no_refcount)
         operator ::Platform::String^() const;
```

### <a name="return-value"></a>返回值

`Platform::String` 类型的对象的句柄。

## <a name="ctor"></a>  StringReference::StringReference 构造函数

初始化 `StringReference` 类的新实例。

### <a name="syntax"></a>语法

```cpp
StringReference();
StringReference(const StringReference& __fstrArg);
StringReference(const ::default::char16* __strArg);
StringReference(const ::default::char16* __strArg, size_t __lenArg);
```

### <a name="parameters"></a>参数

*__fstrArg*<br/>
其数据用于初始化新实例的 `StringReference`。

*__strArg*<br/>
指向用于初始化新实例的 char16 值数组的指针。

*__lenArg*<br/>
`__strArg` 中的元素数。

### <a name="remarks"></a>备注

此构造函数的第一个版本是默认构造函数。 第二个版本从 `StringReference` 参数指定的对象初始化新 `__fstrArg` 实例类。 第三和第四个重载从 char16 值数组初始化新 `StringReference` 实例。 char16 表示 16 位 UNICODE 文本字符。

## <a name="see-also"></a>请参阅

[Platform::StringReference 类](../cppcx/platform-stringreference-class.md)
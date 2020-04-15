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
ms.openlocfilehash: 4748eecdf67ae5a60ddf97783a934a05e80b406c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374660"
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

|名称|说明|
|----------|-----------------|
|[字符串引用：：字符串引用](#ctor)|两个用于创建 `StringReference`实例的构造函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[字符串参考：:D](#data)|返回 char16 值数组形式的字符串数据。|
|[字符串参考：长度](#length)|返回字符串中的字符数。|
|[字符串参考：：获取HSTRING](#gethstring)|返回 HSTRING 形式的字符串数据。|
|[字符串引用：：获取String](#getstring)|返回 `Platform::String^`形式的字符串数据。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[字符串参考：：运算符*](#operator-assign)|将 `StringReference` 分配给新 `StringReference` 实例。|
|[字符串引用：：运算符（）](#operator-call)|将 `StringReference` 转换为 `Platform::String^`。|

### <a name="requirements"></a>要求

**受支持的最小客户端：** 视窗 8

**受支持的服务器最少：** 视窗服务器 2012

**命名空间：** Platform

**标头：** vccorlib.h

## <a name="stringreferencedata-method"></a><a name="data"></a>字符串参考：:Data 方法

以 char16 值数组形式返回此 `StringReference` 的内容。

### <a name="syntax"></a>语法

```cpp
const ::default::char16 * Data() const;
```

### <a name="return-value"></a>返回值

char16 UNICODE 文本字符的数组。

## <a name="stringreferencegethstring-method"></a><a name="gethstring"></a>字符串引用：getHSTRING 方法

以 `__abi_HSTRING` 形式返回字符串内容。

### <a name="syntax"></a>语法

```cpp
__abi_HSTRING GetHSTRING() const;
```

### <a name="return-value"></a>返回值

一个包含字符串数据的 `__abi_HSTRING`。

### <a name="remarks"></a>备注

## <a name="stringreferencegetstring-method"></a><a name="getstring"></a>字符串引用：：获取字符串方法

以 `Platform::String^` 形式返回字符串内容。

### <a name="syntax"></a>语法

```cpp
__declspec(no_release_return) __declspec(no_refcount)
    ::Platform::String^ GetString() const;
```

### <a name="return-value"></a>返回值

一个包含字符串数据的 `Platform::String^`。

## <a name="stringreferencelength-method"></a><a name="length"></a>字符串引用：长度方法

返回字符串中的字符数。

### <a name="syntax"></a>语法

```cpp
unsigned int Length() const;
```

### <a name="return-value"></a>返回值

指定字符串中字符数的无符号整数。

### <a name="remarks"></a>备注

## <a name="stringreferenceoperator-operator"></a><a name="operator-assign"></a>字符串参考：：：运算符= 运算符

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

因为它是`StringReference`标准C++类，而不是 ref 类，所以它不出现在**对象浏览器**中。

## <a name="stringreferenceoperator--operator"></a><a name="operator-call"></a>字符串参考：：运算符（） 运算符

将 `StringReference` 对象转换为 `Platform::String^` 对象。

### <a name="syntax"></a>语法

```cpp
__declspec(no_release_return) __declspec(no_refcount)
         operator ::Platform::String^() const;
```

### <a name="return-value"></a>返回值

`Platform::String` 类型的对象的句柄。

## <a name="stringreferencestringreference-constructor"></a><a name="ctor"></a>字符串引用：：字符串引用构造函数

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

## <a name="see-also"></a>另请参阅

[平台：字符串引用类](../cppcx/platform-stringreference-class.md)

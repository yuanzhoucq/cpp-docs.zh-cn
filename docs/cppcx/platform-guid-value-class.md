---
title: Platform::Guid 值类
ms.date: 01/15/2019
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Guid
helpviewer_keywords:
- Platform::Guid Struct
ms.assetid: 25c0bfb2-7f93-44d8-bdf4-ef4fbac3424a
ms.openlocfilehash: 64c70b619380d7c2ed4aaaecad3ee01a1d0f79c7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383316"
---
# <a name="platformguid-value-class"></a>Platform::Guid 值类

代表 Windows 运行时类型系统中的 [GUID](https://msdn.microsoft.com/library/windows/desktop/aa373931) 类型。

## <a name="syntax"></a>语法

```cpp
public value struct Guid
```

### <a name="members"></a>成员

`Platform::Guid` 具有`Equals()`， `GetHashCode()`，并`ToString()`方法派生自[platform:: object 类](../cppcx/platform-object-class.md)，并且`GetTypeCode()`方法派生自[platform:: type 类](../cppcx/platform-type-class.md)。 `Platform::Guid` 此外具有以下成员。

|成员|描述|
|------------|-----------------|
|[Guid](#ctor)|初始化 `Platform::Guid` 的新实例。|
|[operator==](#operator-equality)|等于运算符。|
|[operator!=](#operator-inequality)|不等于运算符。|
|[operator&lt;](#operator-less)|小于运算符。|
|[operator()](#operator-call)|将 `Platform::Guid` 转换为 `GUID`。|

### <a name="remarks"></a>备注

若要生成一个新`Platform::Guid`，使用[Windows::Foundation::GuidHelper::CreateNewGuid](/uwp/api/windows.foundation.guidhelper.createnewguid#Windows_Foundation_GuidHelper_CreateNewGuid)静态方法。

### <a name="requirements"></a>要求

**支持的最低客户端：** Windows 8

**支持的最低服务器：** Windows Server 2012

**命名空间：** Platform

**元数据：** platform.winmd

## <a name="ctor"></a> Guid:: guid 构造函数

初始化 `Platform::Guid` 的新实例。

### <a name="syntax"></a>语法

```cpp
Guid(
    unsigned int a,
    unsigned short b,
    unsigned short c,
    unsigned char d,
    unsigned char e,
    unsigned char f,
    unsigned char g,
    unsigned char h,
    unsigned char i,
    unsigned char j,
    unsigned char k );

Guid(GUID m);

Guid(
    unsigned int a,
    unsigned short b,
    unsigned short c,
    Array<unsigned char>^ n );
```

### <a name="parameters"></a>参数

*a*<br/>
前 4 个字节的`GUID`。

*b*<br/>
接下来的 2 个字节的`GUID`。

*c*<br/>
接下来的 2 个字节的`GUID`。

*d*<br/>
下一个字节`GUID`。

*e*<br/>
下一个字节`GUID`。

*f*<br/>
下一个字节`GUID`。

*g*<br/>
下一个字节`GUID`。

*h*<br/>
下一个字节`GUID`。

*i*<br/>
下一个字节`GUID`。

*j*<br/>
下一个字节`GUID`。

*k*<br/>
下一个字节`GUID`。

*m*<br/>
一个`GUID`形式[GUID 结构](https://msdn.microsoft.com/library/windows/desktop/aa373931)。

*n*<br/>
其余 8 个字节`GUID`。

## <a name="operator-equality"></a> Guid::operator = = 运算符

比较两个 `Platform::Guid` 实例是否相等。

### <a name="syntax"></a>语法

```cpp
static bool Platform::Guid::operator==(Platform::Guid guid1, Platform::Guid guid2);
```

### <a name="parameters"></a>参数

*guid1*<br/>
要比较的第一个 `Platform::Guid`。

*guid2*<br/>
要比较的第二个 `Platform::Guid`。

### <a name="return-value"></a>返回值

如果两个`Platform::Guid`实例是否相等。

### <a name="remarks"></a>备注

更倾向于使用`==`而不是运算符[Windows::Foundation::GuidHelper::Equals](/uwp/api/windows.foundation.guidhelper.equals)静态方法。

## <a name="operator-inequality"></a> Guid::operator ！ = 运算符

比较两个`Platform::Guid`实例是否不相等。

### <a name="syntax"></a>语法

```cpp
static bool Platform::Guid::operator!=(Platform::Guid guid1, Platform::Guid guid2);
```

### <a name="parameters"></a>参数

*guid1*<br/>
要比较的第一个 `Platform::Guid`。

*guid2*<br/>
要比较的第二个 `Platform::Guid`。

### <a name="return-value"></a>返回值

如果两个`Platform::Guid`实例是否不相等。

## <a name="operator-less"></a> Guid::operator&lt;运算符

比较两个`Platform::Guid`实例进行排序。

### <a name="syntax"></a>语法

```cpp
static bool Platform::Guid::operator<(Platform::Guid guid1, Platform::Guid guid2);
```

### <a name="parameters"></a>参数

*guid1*<br/>
要比较的第一个 `Platform::Guid`。

*guid2*<br/>
要比较的第二个 `Platform::Guid`。

### <a name="return-value"></a>返回值

则为 true *guid1*进行排序之前*guid2*。 将每个后的顺序是按字典顺序`Platform::Guid`像它是四个 32 位无符号值的数组。 这不是由 SQL Server 或.NET Framework 中，使用的顺序也不是按字典编辑顺序排序的字符串表示形式相同。

提供此运算符，以便`Guid`对象可以更轻松地使用C++标准库。

## <a name="operator-call"></a> Guid::operator() 运算符

将隐式转换`Platform::Guid`到[GUID 结构](https://msdn.microsoft.com/library/windows/desktop/aa373931)。

### <a name="syntax"></a>语法

```cpp
const GUID& Platform::Guid::operator();
```

### <a name="return-value"></a>返回值

一个[GUID 结构](https://msdn.microsoft.com/library/windows/desktop/aa373931)。

## <a name="see-also"></a>请参阅

[Platform 命名空间](../cppcx/platform-namespace-c-cx.md)

---
title: Platform::Guid 值类
ms.date: 01/15/2019
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Guid
helpviewer_keywords:
- Platform::Guid Struct
ms.assetid: 25c0bfb2-7f93-44d8-bdf4-ef4fbac3424a
ms.openlocfilehash: f63b2bb4fd5f809861622a4f6b255ee3725564b6
ms.sourcegitcommit: 4517932a67bbf2db16cfb122d3bef57a43696242
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2019
ms.locfileid: "71816593"
---
# <a name="platformguid-value-class"></a>Platform::Guid 值类

代表 Windows 运行时类型系统中的 [GUID](/previous-versions/cc317743(v%3dmsdn.10)) 类型。

## <a name="syntax"></a>语法

```cpp
public value struct Guid
```

### <a name="members"></a>成员

@no__t 的 @no__t 具有从[platform：： Object 类](../cppcx/platform-object-class.md)派生的1、`GetHashCode()` 和 @no__t 3 方法，以及派生自[Platform：： Type 类](../cppcx/platform-type-class.md)的 `GetTypeCode()` 方法。 `Platform::Guid` 也具有以下成员。

|成员|描述|
|------------|-----------------|
|[Guid](#ctor)|初始化 `Platform::Guid` 的新实例。|
|[operator==](#operator-equality)|等于运算符。|
|[operator!=](#operator-inequality)|不等于运算符。|
|[operator&lt;](#operator-less)|小于运算符。|
|[operator()](#operator-call)|将 `Platform::Guid` 转换为 `GUID`。|

### <a name="remarks"></a>备注

若要生成新的 `Platform::Guid`，请使用[Windows：： Foundation：： GuidHelper：： CreateNewGuid](/uwp/api/windows.foundation.guidhelper.createnewguid#Windows_Foundation_GuidHelper_CreateNewGuid)静态方法。

### <a name="requirements"></a>要求

**支持的最低客户端：** Windows 8

**支持的最低服务器：** Windows Server 2012

**命名空间：** 平台

**元数据：** platform.winmd

## <a name="ctor"></a>Guid：： Guid 构造函数

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

### <a name="parameters"></a>Parameters

*a*<br/>
@No__t 的前4个字节。

*b*<br/>
@No__t 的下2个字节。

*c*<br/>
@No__t 的下2个字节。

*d*<br/>
@No__t 的下一个字节。

*e*<br/>
@No__t 的下一个字节。

*f*<br/>
@No__t 的下一个字节。

*g*<br/>
@No__t 的下一个字节。

*h*<br/>
@No__t 的下一个字节。

*i*<br/>
@No__t 的下一个字节。

*j*<br/>
@No__t 的下一个字节。

*k*<br/>
@No__t 的下一个字节。

*m*<br/>
形式为的 @no__t 0，格式为[GUID 结构](/previous-versions/cc317743(v%3dmsdn.10))。

*n*<br/>
@No__t 的其余8个字节。

## <a name="operator-equality"></a>Guid：： operator = = 运算符

比较两个 `Platform::Guid` 实例是否相等。

### <a name="syntax"></a>语法

```cpp
static bool Platform::Guid::operator==(Platform::Guid guid1, Platform::Guid guid2);
```

### <a name="parameters"></a>Parameters

*guid1*<br/>
要比较的第一个 `Platform::Guid`。

*guid2*<br/>
要比较的第二个 `Platform::Guid`。

### <a name="return-value"></a>返回值

如果两个 `Platform::Guid` 实例相等，则为 True。

### <a name="remarks"></a>备注

首选使用 `==` 运算符而不是[Windows：： Foundation：： GuidHelper：： Equals](/uwp/api/windows.foundation.guidhelper.equals)静态方法。

## <a name="operator-inequality"></a>Guid：： operator！ = 运算符

比较两个 @no__t 0 个实例是否不相等。

### <a name="syntax"></a>语法

```cpp
static bool Platform::Guid::operator!=(Platform::Guid guid1, Platform::Guid guid2);
```

### <a name="parameters"></a>Parameters

*guid1*<br/>
要比较的第一个 `Platform::Guid`。

*guid2*<br/>
要比较的第二个 `Platform::Guid`。

### <a name="return-value"></a>返回值

如果两个 `Platform::Guid` 实例不相等，则为 True。

## <a name="operator-less"></a>Guid：： operator @ no__t-1 运算符

比较两个 @no__t 0 个实例进行排序。

### <a name="syntax"></a>语法

```cpp
static bool Platform::Guid::operator<(Platform::Guid guid1, Platform::Guid guid2);
```

### <a name="parameters"></a>Parameters

*guid1*<br/>
要比较的第一个 `Platform::Guid`。

*guid2*<br/>
要比较的第二个 `Platform::Guid`。

### <a name="return-value"></a>返回值

如果在*guid2*之前对*guid1*进行排序，则为 True。 将每个 @no__t 视为 4 32 位无符号值的数组之后，排序将为字典。 这并不是 SQL Server 或 .NET Framework 使用的顺序，也不是按字符串表示形式按字典排序的顺序。

提供此运算符是为了使C++标准库能够更轻松地使用 `Guid` 对象。

## <a name="operator-call"></a>Guid：： operator （）运算符

将 @no__t 0 隐式转换为[GUID 结构](/previous-versions/cc317743(v%3dmsdn.10))。

### <a name="syntax"></a>语法

```cpp
const GUID& Platform::Guid::operator();
```

### <a name="return-value"></a>返回值

[GUID 结构](/previous-versions/cc317743(v%3dmsdn.10))。

## <a name="see-also"></a>请参阅

[Platform 命名空间](../cppcx/platform-namespace-c-cx.md)

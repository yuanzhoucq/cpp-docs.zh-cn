---
title: Platform::Guid 值类
ms.date: 01/15/2019
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Guid
helpviewer_keywords:
- Platform::Guid Struct
ms.assetid: 25c0bfb2-7f93-44d8-bdf4-ef4fbac3424a
ms.openlocfilehash: 3849074f93424912b1dc5b93883482a6cb55892a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750667"
---
# <a name="platformguid-value-class"></a>Platform::Guid 值类

表示 Windows 运行时类型系统中的 [GUID]（/窗口/win32/api/guiddef/ns-guiddef-guid-guid 类型）。

## <a name="syntax"></a>语法

```cpp
public value struct Guid
```

### <a name="members"></a>成员

`Platform::Guid``GetHashCode()``ToString()`[Platform::Object Class](../cppcx/platform-object-class.md)`GetTypeCode()`[Platform::Type Class](../cppcx/platform-type-class.md)具有 派生自平台：对象类的方法，以及从平台派生的方法：：类型类 。 `Equals()` `Platform::Guid`也有以下成员。

|成员|说明|
|------------|-----------------|
|[Guid](#ctor)|初始化 `Platform::Guid` 的新实例。|
|[运算符*](#operator-equality)|等于运算符。|
|[操作员！](#operator-inequality)|不等于运算符。|
|[算子&lt;](#operator-less)|小于运算符。|
|[运算符（）](#operator-call)|将 `Platform::Guid` 转换为 `GUID`。|

### <a name="remarks"></a>备注

要生成新`Platform::Guid`，请使用[Windows：：基础：：GuidHelper：：创建新 Guid](/uwp/api/windows.foundation.guidhelper.createnewguid#Windows_Foundation_GuidHelper_CreateNewGuid)静态方法。

### <a name="requirements"></a>要求

**受支持的最小客户端：** 视窗 8

**受支持的服务器最少：** 视窗服务器 2012

**命名空间：** Platform

**元数据：** 平台.winmd

## <a name="guidguid-constructors"></a><a name="ctor"></a>吉德：：吉德构造函数

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
的前 4 个字节`GUID`。

*B*<br/>
的下 2 个字节。 `GUID`

*C*<br/>
的下 2 个字节。 `GUID`

*D*<br/>
`GUID` 的下一个字节。

*e*<br/>
`GUID` 的下一个字节。

*F*<br/>
`GUID` 的下一个字节。

*G*<br/>
`GUID` 的下一个字节。

*H*<br/>
`GUID` 的下一个字节。

*Ⅰ*<br/>
`GUID` 的下一个字节。

*J*<br/>
`GUID` 的下一个字节。

*K*<br/>
`GUID` 的下一个字节。

*米*<br/>
A`GUID`形式为[GUID 结构](/windows/win32/api/guiddef/ns-guiddef-guid)。

*n*<br/>
其余 8 个字节的`GUID`。

## <a name="guidoperator-operator"></a><a name="operator-equality"></a>吉德：：：操作员=运算符

比较两个 `Platform::Guid` 实例是否相等。

### <a name="syntax"></a>语法

```cpp
static bool Platform::Guid::operator==(Platform::Guid guid1, Platform::Guid guid2);
```

### <a name="parameters"></a>参数

*吉德1*<br/>
要比较的第一个 `Platform::Guid`。

*吉德2*<br/>
要比较的第二个 `Platform::Guid`。

### <a name="return-value"></a>返回值

如果两`Platform::Guid`个实例相等，则为 True。

### <a name="remarks"></a>备注

更喜欢使用`==`运算符而不是[Windows：基础：：GuidHelper：：等于](/uwp/api/windows.foundation.guidhelper.equals)静态方法。

## <a name="guidoperator-operator"></a><a name="operator-inequality"></a>吉德：：操作员！

比较两个 `Platform::Guid` 实例是否不相等。

### <a name="syntax"></a>语法

```cpp
static bool Platform::Guid::operator!=(Platform::Guid guid1, Platform::Guid guid2);
```

### <a name="parameters"></a>参数

*吉德1*<br/>
要比较的第一个 `Platform::Guid`。

*吉德2*<br/>
要比较的第二个 `Platform::Guid`。

### <a name="return-value"></a>返回值

如果两`Platform::Guid`个实例不相等，则为 True。

## <a name="guidoperatorlt-operator"></a><a name="operator-less"></a>吉德：：操作员&lt;

比较两`Platform::Guid`个排序实例。

### <a name="syntax"></a>语法

```cpp
static bool Platform::Guid::operator<(Platform::Guid guid1, Platform::Guid guid2);
```

### <a name="parameters"></a>参数

*吉德1*<br/>
要比较的第一个 `Platform::Guid`。

*吉德2*<br/>
要比较的第二个 `Platform::Guid`。

### <a name="return-value"></a>返回值

如果*guid1*是在*guid2*之前订购的，则为 True。 排序是字典，在将每个`Platform::Guid`值视为四个 32 位无符号值的数组。 这不是 SQL Server 或 .NET 框架使用的顺序，也不与字符串表示法的字典排序相同。

提供此运算符，以便`Guid`C++标准库可以更轻松地使用对象。

## <a name="guidoperator-operator"></a><a name="operator-call"></a>吉德：：操作员（） 运算符

隐式将`Platform::Guid`转换为[GUID 结构](/windows/win32/api/guiddef/ns-guiddef-guid)。

### <a name="syntax"></a>语法

```cpp
const GUID& Platform::Guid::operator();
```

### <a name="return-value"></a>返回值

[GUID 结构](/windows/win32/api/guiddef/ns-guiddef-guid)。

## <a name="see-also"></a>请参阅

[Platform 命名空间](../cppcx/platform-namespace-c-cx.md)

---
title: Platform::Guid 值类
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Guid
helpviewer_keywords:
- Platform::Guid Struct
ms.assetid: 25c0bfb2-7f93-44d8-bdf4-ef4fbac3424a
ms.openlocfilehash: 0a339de3aec14b6bd1dc461f53c1a7417db738ea
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50482922"
---
# <a name="platformguid-value-class"></a>Platform::Guid 值类

代表 Windows 运行时类型系统中的 [GUID](https://msdn.microsoft.com/library/windows/desktop/aa373931) 类型。

## <a name="syntax"></a>语法

```cpp
public value struct Guid
```

### <a name="members"></a>成员

Guid 具有从 [Platform::Object Class](../cppcx/platform-object-class.md)派生的 Equals()、GetHashCode() 和 ToString() 方法，以及从 [Platform::Type Class](../cppcx/platform-type-class.md)。 Guid 还具有下列成员。

|成员|描述|
|------------|-----------------|
|[Guid](#ctor)|初始化 Guid 结构的新实例。|
|[operator==](#operator-equality)|等于运算符。|
|[operator!=](#operator-not-equal)|不等于运算符。|
|[operator()](#operator-call)|将 Guid 转换为 GUID。|

### <a name="remarks"></a>备注

有关如何使用 Windows 函数 [CoCreateGuid](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateguid)生成新的 Platform::Guid 的示例，请参阅 [WinRT 组件：如何生成 GUID？](http://blogs.msdn.com/b/eternalcoding/archive/2013/03/25/winrt-component-how-to-generate-a-guid.aspx)

### <a name="requirements"></a>要求

**支持的最低客户端：** Windows 8

**支持的最低服务器：** Windows Server 2012

**命名空间：** Platform

**元数据：** platform.winmd

## <a name="ctor"></a> Guid:: guid 构造函数

初始化 Guid 结构的新实例。

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
GUID 的前 4 个字节。

*b*<br/>
GUID 的下两个字节。

*c*<br/>
GUID 的下两个字节。

*d*<br/>
GUID 的下一个字节。

*e*<br/>
GUID 的下一个字节。

*f*<br/>
GUID 的下一个字节。

*g*<br/>
GUID 的下一个字节。

*h*<br/>
GUID 的下一个字节。

*i*<br/>
GUID 的下一个字节。

*J*<br/>
GUID 的下一个字节。

*k*<br/>
GUID 的下一个字节。

*m*<br/>
所定义的 GUID。

*n*<br/>
GUID 的其余 8 个字节。

## <a name="operator-equality"></a> Guid::operator = = 运算符

比较两个 guid。

### <a name="syntax"></a>语法

```cpp
Platform::Guid::operator==
```

### <a name="return-value"></a>返回值

如果两个 guid 相等，则为 true。

## <a name="operator-inequality"></a> Guid::operator ！ = 运算符

比较两个 guid。

### <a name="syntax"></a>语法

```cpp
Platform::Guid::operator!=
```

### <a name="return-value"></a>返回值

如果两个 guid 是否不相等，则为 true。

## <a name="operator-call"></a> Guid::operator() 运算符

将隐式转换[GUID 结构](https://msdn.microsoft.com/library/windows/desktop/aa373931)platform:: guid 的 GUID。

### <a name="syntax"></a>语法

```cpp
Platform::Guid operator();
```

### <a name="return-value"></a>返回值

一个 Guid 结构。

## <a name="see-also"></a>请参阅

[平台命名空间](../cppcx/platform-namespace-c-cx.md)
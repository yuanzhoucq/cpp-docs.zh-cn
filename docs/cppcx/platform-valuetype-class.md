---
title: Platform::ValueType 类
ms.date: 02/03/2017
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::ValueType::ToString
helpviewer_keywords:
- Platform::ValueType Class
ms.assetid: 79aa8754-b140-4974-a5b1-be046938a10a
ms.openlocfilehash: 57fb089f0d9dc53ba8a65cef41e3341168ffea45
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50596399"
---
# <a name="platformvaluetype-class"></a>Platform::ValueType 类

值类型实例的基类。

## <a name="syntax"></a>语法

```cpp
public ref class ValueType : Object
```

## <a name="public-methods"></a>公共方法

|||
|-|-|
|[ValueType::ToString](#tostring)|返回对象的字符串表示形式。 继承自[platform:: object](../cppcx/platform-object-class.md)。|

### <a name="remarks"></a>备注

ValueType 类用于构造值类型。 ValueType 派生自有基本成员的 Object。 但是，编译器会将这些基本成员与从 ValueType 类派生的值类型分离。 值类型进行装箱时，编译器会重新附加这些基本成员。

### <a name="requirements"></a>要求

**支持的最低客户端：** Windows 8

**支持的最低服务器：** Windows Server 2012

**命名空间：** Platform

**元数据：** platform.winmd

## <a name="tostring"></a> Valuetype:: Tostring 方法

返回对象的字符串表示形式。

### <a name="syntax"></a>语法

```cpp
Platform::String ToString();
```

### <a name="return-value"></a>返回值

Platform:: string 表示的值。

## <a name="see-also"></a>请参阅

[平台命名空间](../cppcx/platform-namespace-c-cx.md)
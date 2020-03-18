---
title: Platform::IBoxArray 接口
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::IBoxArray
- VCCORLIB/Platform::IBoxArray::Value
helpviewer_keywords:
- Platform::IBoxArray
ms.assetid: 6cd82c9e-4230-4147-9edb-7a652875dbf1
ms.openlocfilehash: 493770cab092c2bb719d47e5d3a9d6a9f0646489
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444155"
---
# <a name="platformiboxarray-interface"></a>Platform::IBoxArray 接口

`IBoxArray` 是在应用程序二进制接口 (ABI) 之间传递或在 `Platform::Object^` 元素的集合中存储（如 XAML 控件）的值类型数组的包装器。

## <a name="syntax"></a>语法

```cpp
template <typename T>
interface class IBoxArray
```

#### <a name="parameters"></a>参数

*T*<br/>
每个数组元素中的装箱值的类型。

### <a name="remarks"></a>备注

`IBoxArray` 是 `Windows::Foundation::IReferenceArray`C++的/cx 名称。

### <a name="members"></a>Members

`IBoxArray` 接口继承自 `IValueType` 接口。 `IBoxArray` 还包括这些成员：

|方法|说明|
|------------|-----------------|
|[值](#value)|返回此 `IBoxArray` 实例以前存储的未装箱数组。|

## <a name="value"></a>IBoxArray：： Value 属性

返回此对象中最初存储的值。

### <a name="syntax"></a>语法

```cpp
property T Value {T get();}
```

### <a name="parameters"></a>参数

*T*<br/>
装箱值的类型。

### <a name="property-valuereturn-value"></a>属性值/返回值

返回此对象中最初存储的值。

### <a name="remarks"></a>备注

有关示例，请参见[装箱](../cppcx/boxing-c-cx.md)。

## <a name="see-also"></a>另请参阅

[Array 和 WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)

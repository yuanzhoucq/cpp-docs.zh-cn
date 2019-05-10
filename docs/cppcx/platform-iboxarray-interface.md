---
title: Platform::IBoxArray 接口
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Namespace not found::Platform
- VCCORLIB/Namespace not found::Platform::Value
helpviewer_keywords:
- Platform::IBoxArray
ms.assetid: 6cd82c9e-4230-4147-9edb-7a652875dbf1
ms.openlocfilehash: ea2517ad64cfd6742ef072d24e94a9b3899cea2d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392071"
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

`IBoxArray` 是C++/CX 名称`Windows::Foundation::IReferenceArray`。

### <a name="members"></a>成员

`IBoxArray` 接口继承自 `IValueType` 接口。 `IBoxArray` 还包括这些成员：

|方法|描述|
|------------|-----------------|
|[值](#value)|返回此 `IBoxArray` 实例以前存储的未装箱数组。|

## <a name="value"></a> Iboxarray:: Value 属性

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

有关示例，请参阅[装箱](../cppcx/boxing-c-cx.md)。

## <a name="see-also"></a>请参阅

[Array 和 WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)

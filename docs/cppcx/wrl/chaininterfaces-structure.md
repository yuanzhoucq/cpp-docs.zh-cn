---
title: ChainInterfaces 结构
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::ChainInterfaces
- implements/Microsoft::WRL::ChainInterfaces::CanCastTo
- implements/Microsoft::WRL::ChainInterfaces::CastToUnknown
- implements/Microsoft::WRL::ChainInterfaces::FillArrayWithIid
- implements/Microsoft::WRL::ChainInterfaces::IidCount
- implements/Microsoft::WRL::ChainInterfaces::Verify
helpviewer_keywords:
- Microsoft::WRL::ChainInterfaces structure
- Microsoft::WRL::ChainInterfaces::CanCastTo method
- Microsoft::WRL::ChainInterfaces::CastToUnknown method
- Microsoft::WRL::ChainInterfaces::FillArrayWithIid method
- Microsoft::WRL::ChainInterfaces::IidCount constant
- Microsoft::WRL::ChainInterfaces::Verify method
ms.assetid: d7415b59-5468-4bef-a3fd-8d82b12f0e9c
ms.openlocfilehash: dd1af3fb5c1079a40d8248dc71ae4972537aa856
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372653"
---
# <a name="chaininterfaces-structure"></a>ChainInterfaces 结构

指定可应用于一组接口 ID 的验证和初始化函数。

## <a name="syntax"></a>语法

```cpp
template <
    typename I0,
    typename I1,
    typename I2 = Details::Nil,
    typename I3 = Details::Nil,
    typename I4 = Details::Nil,
    typename I5 = Details::Nil,
    typename I6 = Details::Nil,
    typename I7 = Details::Nil,
    typename I8 = Details::Nil,
    typename I9 = Details::Nil
>
struct ChainInterfaces : I0;

template <
    typename DerivedType,
    typename BaseType,
    bool hasImplements,
    typename I1,
    typename I2,
    typename I3,
    typename I4,
    typename I5,
    typename I6,
    typename I7,
    typename I8,
    typename I9
>
struct ChainInterfaces<
    MixIn<
        DerivedType,
        BaseType,
        hasImplements
    >, I1, I2, I3, I4, I5, I6, I7, I8, I9
>;
```

### <a name="parameters"></a>参数

*I0*<br/>
（必需）接口 ID 0。

*I1*<br/>
（必需）接口 ID 1。

*I2*<br/>
（可选）接口 ID 2。

*I3*<br/>
（可选）接口 ID 3。

*I4*<br/>
（可选）接口 ID 4。

*I5*<br/>
（可选）接口 ID 5。

*I6*<br/>
（可选）接口 ID 6。

*I7*<br/>
（可选）接口 ID 7。

*I8*<br/>
（可选）接口 ID 8。

*I9*<br/>
（可选）接口 ID 9。

*派生类型*<br/>
派生类型。

*BaseType*<br/>
派生类型的基类型。

*有实现*<br/>
布尔值，如果为**true，** 则意味着不能将[MixIn](mixin-structure.md)结构与不派生自[实现](implements-structure.md)结构的类一起使用。

## <a name="members"></a>成员

### <a name="protected-methods"></a>受保护的方法

名称                                                   | 说明
------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[链接口：：坎卡斯特托](#cancastto)               | 指示是否可以将指定的接口 ID 强制转换为`ChainInterface`模板参数定义的每个专门化。
[链接口：：Castto 未知](#casttounknown)       | 将*I0*模板参数定义的类型的接口指针强制转换为 指向`IUnknown`的指针。
[链接口：：填充与Iid](#fillarraywithiid) | 将*I0*模板参数定义的接口 ID 存储在指定的接口 ID 数组中的指定位置。
[链接口：验证](#verify)                     | 验证模板参数*I0*到*I9*定义的每个接口`IUnknown`继承和/或`IInspectable`，并且*I0*继承从*I1*到*I9*。

### <a name="protected-constants"></a>受保护的常量

名称                                   | 说明
-------------------------------------- | -----------------------------------------------------------------------------------------------------------------
[链接口：：IidCount](#iidcount) | 模板参数*I0*通过*I9*指定的接口中包含的接口 ID 总数。

## <a name="inheritance-hierarchy"></a>继承层次结构

`I0`

`ChainInterfaces`

## <a name="requirements"></a>要求

**标题：** 实现.h

**命名空间：** Microsoft::WRL

## <a name="chaininterfacescancastto"></a><a name="cancastto"></a>链接口：：坎卡斯特托

指示是否可以将指定的接口 ID 强制转换为非默认模板参数定义的每个专门化。

```cpp
__forceinline bool CanCastTo(
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>参数

*riid*<br/>
接口 ID。

*Ppv*<br/>
指向成功强制转换的最后一个接口 ID 的指针。

### <a name="return-value"></a>返回值

如果所有强制转换操作都成功，**则为 true;** 否则，**假**。

## <a name="chaininterfacescasttounknown"></a><a name="casttounknown"></a>链接口：：Castto 未知

将*I0*模板参数定义的类型的接口指针强制转换为 指向`IUnknown`的指针。

```cpp
__forceinline IUnknown* CastToUnknown();
```

### <a name="return-value"></a>返回值

一个指向 `IUnknown` 的指针。

## <a name="chaininterfacesfillarraywithiid"></a><a name="fillarraywithiid"></a>链接口：：填充与Iid

将*I0*模板参数定义的接口 ID 存储在指定的接口 ID 数组中的指定位置。

```cpp
__forceinline static void FillArrayWithIid(
   _Inout_ unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>参数

*index*<br/>
指向*iids*数组中的索引值。

*伊德*<br/>
接口指示的数组。

## <a name="chaininterfacesiidcount"></a><a name="iidcount"></a>链接口：：IidCount

模板参数*I0*通过*I9*指定的接口中包含的接口 ID 总数。

```cpp
static const unsigned long IidCount = Details::InterfaceTraits<I0>::IidCount + Details::InterfaceTraits<I1>::IidCount + Details::InterfaceTraits<I2>::IidCount + Details::InterfaceTraits<I3>::IidCount + Details::InterfaceTraits<I4>::IidCount + Details::InterfaceTraits<I5>::IidCount + Details::InterfaceTraits<I6>::IidCount + Details::InterfaceTraits<I7>::IidCount + Details::InterfaceTraits<I8>::IidCount + Details::InterfaceTraits<I9>::IidCount;
```

### <a name="return-value"></a>返回值

接口 ID 的总数。

### <a name="remarks"></a>备注

模板参数*I0*和*I1*是必需的，参数*I2*到*I9*是可选的。 每个接口的 IID 计数通常为 1。

## <a name="chaininterfacesverify"></a><a name="verify"></a>链接口：验证

验证模板参数*I0*到*I9*定义的每个接口`IUnknown`继承和/或`IInspectable`，并且*I0*继承从*I1*到*I9*。

```cpp
WRL_NOTHROW __forceinline static void Verify();
```

### <a name="remarks"></a>备注

如果验证操作失败，则 `static_assert` 将发出描述失败的错误消息。

模板参数*I0*和*I1*是必需的，参数*I2*到*I9*是可选的。

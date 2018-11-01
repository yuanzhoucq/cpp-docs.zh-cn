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
ms.openlocfilehash: 87967f733cbb6ae2db999232c57751521d77fdc7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50552693"
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
（必需）接口 ID 为 1。

*I2*<br/>
（可选）接口 ID 为 2。

*I3*<br/>
（可选）ID 为 3 的接口。

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

*DerivedType*<br/>
派生的类型。

*BaseType*<br/>
派生类型的基类型。

*hasImplements*<br/>
一个布尔值，如果 **，则返回 true**，意味着不能使用[MixIn](../windows/mixin-structure.md)不是派生的类结构[实现](../windows/implements-structure.md)结构。

## <a name="members"></a>成员

### <a name="protected-methods"></a>受保护的方法

名称                                                   | 描述
------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[Chaininterfaces:: Cancastto](#cancastto)               | 指示指定的接口 ID 是否可以转换为每个定义的专用化`ChainInterface`模板参数。
[Chaininterfaces:: Casttounknown](#casttounknown)       | 定义的类型的接口指针转换*I0*指向的模板参数`IUnknown`。
[Chaininterfaces:: Fillarraywithiid](#fillarraywithiid) | 通过定义的接口 ID 的存储*I0*到指定数组中的接口 Id 的指定位置的模板参数。
[Chaininterfaces:: Verify](#verify)                     | 验证每个接口定义的模板参数*I0*通过*I9*继承`IUnknown`和/或`IInspectable`，以及*I0*继承*I1*通过*I9*。

### <a name="protected-constants"></a>受保护的常量

name                                   | 描述
-------------------------------------- | -----------------------------------------------------------------------------------------------------------------
[Chaininterfaces:: Iidcount](#iidcount) | 模板参数所指定的接口中包含的接口 Id 总数*I0*通过*I9*。

## <a name="inheritance-hierarchy"></a>继承层次结构

`I0`

`ChainInterfaces`

## <a name="requirements"></a>要求

**标头：** implements.h

**命名空间：** Microsoft::WRL

## <a name="cancastto"></a>Chaininterfaces:: Cancastto

指示指定的接口 ID 是否可以转换为每个定义的非默认模板参数的专用化。

```cpp
__forceinline bool CanCastTo(
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>参数

*riid*<br/>
接口 ID。

*ppv*<br/>
指向已成功转换的最后一个接口 ID 的指针。

### <a name="return-value"></a>返回值

**true**如果所有的强制转换操作成功; 否则为**false**。

## <a name="casttounknown"></a>Chaininterfaces:: Casttounknown

定义的类型的接口指针转换*I0*指向的模板参数`IUnknown`。

```cpp
__forceinline IUnknown* CastToUnknown();
```

### <a name="return-value"></a>返回值

一个指向`IUnknown`。

## <a name="fillarraywithiid"></a>Chaininterfaces:: Fillarraywithiid

通过定义的接口 ID 的存储*I0*到指定数组中的接口 Id 的指定位置的模板参数。

```cpp
__forceinline static void FillArrayWithIid(
   _Inout_ unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>参数

*index*<br/>
为到索引值的指针*iid*数组。

*iid*<br/>
接口 Id 的数组。

## <a name="iidcount"></a>Chaininterfaces:: Iidcount

模板参数所指定的接口中包含的接口 Id 总数*I0*通过*I9*。

```cpp
static const unsigned long IidCount = Details::InterfaceTraits<I0>::IidCount + Details::InterfaceTraits<I1>::IidCount + Details::InterfaceTraits<I2>::IidCount + Details::InterfaceTraits<I3>::IidCount + Details::InterfaceTraits<I4>::IidCount + Details::InterfaceTraits<I5>::IidCount + Details::InterfaceTraits<I6>::IidCount + Details::InterfaceTraits<I7>::IidCount + Details::InterfaceTraits<I8>::IidCount + Details::InterfaceTraits<I9>::IidCount;
```

### <a name="return-value"></a>返回值

接口 ID 的总数。

### <a name="remarks"></a>备注

模板参数*I0*并*I1*是必需的并且参数*I2*通过*I9*都是可选的。 每个接口的 IID 计数通常为 1。

## <a name="verify"></a>Chaininterfaces:: Verify

验证每个接口定义的模板参数*I0*通过*I9*继承`IUnknown`和/或`IInspectable`，以及*I0*继承*I1*通过*I9*。

```cpp
WRL_NOTHROW __forceinline static void Verify();
```

### <a name="remarks"></a>备注

如果验证操作失败，则 `static_assert` 将发出描述失败的错误消息。

模板参数*I0*并*I1*是必需的并且参数*I2*通过*I9*都是可选的。

---
title: InterfaceTraits 结构
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceTraits
- implements/Microsoft::WRL::Details::InterfaceTraits::CanCastTo
- implements/Microsoft::WRL::Details::InterfaceTraits::CastToBase
- implements/Microsoft::WRL::Details::InterfaceTraits::CastToUnknown
- implements/Microsoft::WRL::Details::InterfaceTraits::FillArrayWithIid
- implements/Microsoft::WRL::Details::InterfaceTraits::IidCount
- implements/Microsoft::WRL::Details::InterfaceTraits::Verify
helpviewer_keywords:
- Microsoft::WRL::Details::InterfaceTraits structure
- Microsoft::WRL::Details::InterfaceTraits::CanCastTo method
- Microsoft::WRL::Details::InterfaceTraits::CastToBase method
- Microsoft::WRL::Details::InterfaceTraits::CastToUnknown method
- Microsoft::WRL::Details::InterfaceTraits::FillArrayWithIid method
- Microsoft::WRL::Details::InterfaceTraits::IidCount constant
- Microsoft::WRL::Details::InterfaceTraits::Verify method
ms.assetid: ede0c284-19a7-4892-9738-ff3da4923d0a
ms.openlocfilehash: c08c6e8bbcc16120dd44da69a2933fc3ec42f387
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216565"
---
# <a name="interfacetraits-structure"></a>InterfaceTraits 结构

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
template<typename I0>
struct __declspec(novtable) InterfaceTraits;

template<typename CloakedType>
struct __declspec(novtable) InterfaceTraits<
    CloakedIid<CloakedType>
>;

template<>
struct __declspec(novtable) InterfaceTraits<Nil>;
```

### <a name="parameters"></a>参数

*I0*<br/>
接口的名称。

*CloakedType*<br/>
对于 `RuntimeClass` 、 `Implements` 和 `ChainInterfaces` ，不在支持的接口 id 列表中的接口。

## <a name="remarks"></a>备注

实现接口的常见特性。

第二个模板是掩蔽接口的专用化。 第三个模板是零参数的专用化。

## <a name="members"></a>成员

### <a name="public-typedefs"></a><a name="public-typedefs"></a>公共 Typedef

名称   | 描述
------ | ------------------------------------------
`Base` | *I0*模板参数的同义词。

### <a name="public-methods"></a>公共方法

“属性”                                                   | 描述
------------------------------------------------------ | ----------------------------------------------------------------------------------------
[InterfaceTraits：： CanCastTo](#cancastto)               | 指示是否可以将指定指针转换为指向的指针 `Base` 。
[InterfaceTraits：： CastToBase](#casttobase)             | 将指定指针强制转换为指向的指针 `Base` 。
[InterfaceTraits：： CastToUnknown](#casttounknown)       | 将指定指针强制转换为指向的指针 `IUnknown` 。
[InterfaceTraits：： FillArrayWithIid](#fillarraywithiid) | 将的接口 ID 分配 `Base` 给索引参数指定的数组元素。
[InterfaceTraits：： Verify](#verify)                     | 验证 `Base` 是否已正确派生。

### <a name="public-constants"></a>公共常量

名称                                   | 描述
-------------------------------------- | ---------------------------------------------------------------------------------------
[InterfaceTraits：： IidCount](#iidcount) | 保存与当前对象关联的接口 Id 的数量 `InterfaceTraits` 。

## <a name="inheritance-hierarchy"></a>继承层次结构

`InterfaceTraits`

## <a name="requirements"></a>要求

**标头：** 实现。h

**命名空间：** Microsoft：： WRL：:D etails

## <a name="interfacetraitscancastto"></a><a name="cancastto"></a>InterfaceTraits：： CanCastTo

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
template<typename T>
static __forceinline bool CanCastTo(
   _In_ T* ptr,
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>参数

*ptr*<br/>
指向类型的指针的名称。

*riid*<br/>
的接口 ID `Base` 。

*ppv*<br/>
如果此操作成功， *ppv*将指向由指定的接口 `Base` 。 否则， *ppv*设置为 **`nullptr`** 。

### <a name="return-value"></a>返回值

**`true`** 如果此操作成功并且*ptr*强制转换为指向的指针 `Base` ，则为; 否则为 **`false`** 。

### <a name="remarks"></a>备注

指示是否可以将指定指针转换为指向的指针 `Base` 。

有关的详细信息 `Base` ，请参阅[公共 typedef](#public-typedefs)部分。

## <a name="interfacetraitscasttobase"></a><a name="casttobase"></a>InterfaceTraits：： CastToBase

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
template<typename T>
static __forceinline Base* CastToBase(
   _In_ T* ptr
);
```

### <a name="parameters"></a>参数

*T*<br/>
参数*指针*的类型。

*ptr*<br/>
指向类型*T*的指针。

### <a name="return-value"></a>返回值

一个指向 `Base` 的指针。

### <a name="remarks"></a>备注

将指定指针强制转换为指向的指针 `Base` 。

有关的详细信息 `Base` ，请参阅[公共 typedef](#public-typedefs)部分。

## <a name="interfacetraitscasttounknown"></a><a name="casttounknown"></a>InterfaceTraits：： CastToUnknown

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
template<typename T>
static __forceinline IUnknown* CastToUnknown(
   _In_ T* ptr
);
```

### <a name="parameters"></a>参数

*T*<br/>
参数*指针*的类型。

*ptr*<br/>
指向类型*T*的指针。

### <a name="return-value"></a>返回值

一个指针，指向派生的 IUnknown `Base` 。

### <a name="remarks"></a>备注

将指定指针强制转换为指向的指针 `IUnknown` 。

有关的详细信息 `Base` ，请参阅[公共 typedef](#public-typedefs)部分。

## <a name="interfacetraitsfillarraywithiid"></a><a name="fillarraywithiid"></a>InterfaceTraits：： FillArrayWithIid

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
__forceinline static void FillArrayWithIid(
   _Inout_ unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>参数

*index*<br/>
指向包含从零开始的索引值的字段的指针。

*iid*<br/>
接口 Id 的数组。

### <a name="remarks"></a>备注

将的接口 ID 分配 `Base` 给索引参数指定的数组元素。

与此 API 的名称相反，只修改一个数组元素;不是整个数组。

有关的详细信息 `Base` ，请参阅[公共 typedef](#public-typedefs)部分。

## <a name="interfacetraitsiidcount"></a><a name="iidcount"></a>InterfaceTraits：： IidCount

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
static const unsigned long IidCount = 1;
```

### <a name="remarks"></a>备注

保存与当前对象关联的接口 Id 的数量 `InterfaceTraits` 。

## <a name="interfacetraitsverify"></a><a name="verify"></a>InterfaceTraits：： Verify

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
__forceinline static void Verify();
```

### <a name="remarks"></a>备注

验证 `Base` 是否已正确派生。

有关的详细信息 `Base` ，请参阅[公共 typedef](#public-typedefs)部分。

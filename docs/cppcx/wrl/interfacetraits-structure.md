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
ms.openlocfilehash: 17f743a38af3ddc600a55e38905d19868d076a22
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371374"
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

*隐形型*<br/>
`Implements``ChainInterfaces`和`RuntimeClass`的接口不会位于受支持的接口指示的列表中。

## <a name="remarks"></a>备注

实现接口的通用特性。

第二个模板是掩蔽接口的专门化。 第三个模板是 Nil 参数的专门化。

## <a name="members"></a>成员

### <a name="public-typedefs"></a><a name="public-typedefs"></a>公共类型

名称   | 说明
------ | ------------------------------------------
`Base` | *I0*模板参数的同义词。

### <a name="public-methods"></a>公共方法

名称                                                   | 说明
------------------------------------------------------ | ----------------------------------------------------------------------------------------
[接口特征：：坎卡斯特托](#cancastto)               | 指示指定指针是否可以转换为指向`Base`的指针。
[接口特征：：CasttoBase](#casttobase)             | 将指定的指针强制转换为 指向`Base`的指针。
[接口特征：：强制未知](#casttounknown)       | 将指定的指针强制转换为 指向`IUnknown`的指针。
[接口特征：：填充带](#fillarraywithiid) | 将 的`Base`接口 ID 分配给索引参数指定的数组元素。
[接口特征：验证](#verify)                     | 验证`Base`正确派生的。

### <a name="public-constants"></a>公共常量

名称                                   | 说明
-------------------------------------- | ---------------------------------------------------------------------------------------
[接口特征：：IidCount](#iidcount) | 保存与当前`InterfaceTraits`对象关联的接口指示数。

## <a name="inheritance-hierarchy"></a>继承层次结构

`InterfaceTraits`

## <a name="requirements"></a>要求

**标题：** 实现.h

**命名空间：** 微软：：WRL：:D

## <a name="interfacetraitscancastto"></a><a name="cancastto"></a>接口特征：：坎卡斯特托

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

*Ptr*<br/>
指向类型的指针的名称。

*riid*<br/>
的接口`Base`ID。

*Ppv*<br/>
如果此操作成功 *，ppv*将指向 指定的`Base`接口。 否则 *，ppv*设置为`nullptr`。

### <a name="return-value"></a>返回值

如果此操作成功，并且*ptr*被强制转换为指向`Base`的指针，**则为 true。** 否则，**假**。

### <a name="remarks"></a>备注

指示指定指针是否可以转换为指向`Base`的指针。

有关 的详细信息`Base`，请参阅[公共类型防御区](#public-typedefs)部分。

## <a name="interfacetraitscasttobase"></a><a name="casttobase"></a>接口特征：：CasttoBase

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
template<typename T>
static __forceinline Base* CastToBase(
   _In_ T* ptr
);
```

### <a name="parameters"></a>参数

*T*<br/>
参数*ptr*的类型。

*Ptr*<br/>
指向类型*T*的指针。

### <a name="return-value"></a>返回值

一个指向 `Base` 的指针。

### <a name="remarks"></a>备注

将指定的指针强制转换为 指向`Base`的指针。

有关 的详细信息`Base`，请参阅[公共类型防御区](#public-typedefs)部分。

## <a name="interfacetraitscasttounknown"></a><a name="casttounknown"></a>接口特征：：强制未知

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
template<typename T>
static __forceinline IUnknown* CastToUnknown(
   _In_ T* ptr
);
```

### <a name="parameters"></a>参数

*T*<br/>
参数*ptr*的类型。

*Ptr*<br/>
指向类型*T 的*指针。

### <a name="return-value"></a>返回值

指向派生的 I 未知`Base`项的指针。

### <a name="remarks"></a>备注

将指定的指针强制转换为 指向`IUnknown`的指针。

有关 的详细信息`Base`，请参阅[公共类型防御区](#public-typedefs)部分。

## <a name="interfacetraitsfillarraywithiid"></a><a name="fillarraywithiid"></a>接口特征：：填充带

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
__forceinline static void FillArrayWithIid(
   _Inout_ unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>参数

*index*<br/>
指向包含零基索引值的字段的指针。

*伊德*<br/>
接口指示的数组。

### <a name="remarks"></a>备注

将 的`Base`接口 ID 分配给索引参数指定的数组元素。

与此 API 的名称相反，只修改一个数组元素;而不是整个数组。

有关 的详细信息`Base`，请参阅[公共类型防御区](#public-typedefs)部分。

## <a name="interfacetraitsiidcount"></a><a name="iidcount"></a>接口特征：：IidCount

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
static const unsigned long IidCount = 1;
```

### <a name="remarks"></a>备注

保存与当前`InterfaceTraits`对象关联的接口指示数。

## <a name="interfacetraitsverify"></a><a name="verify"></a>接口特征：验证

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
__forceinline static void Verify();
```

### <a name="remarks"></a>备注

验证`Base`正确派生的。

有关 的详细信息`Base`，请参阅[公共类型防御区](#public-typedefs)部分。

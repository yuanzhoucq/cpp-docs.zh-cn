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
ms.openlocfilehash: e8222ccaca9572331412b90e696829568eedcf8e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50543944"
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
有关`RuntimeClass`，`Implements`和`ChainInterfaces`，不会在列表中的接口支持接口 Id。

## <a name="remarks"></a>备注

实现的接口的共同特征。

第二个模板是掩蔽的接口的专用化。 第三个模板是为 Nil 参数专用化。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

name   | 描述
------ | ------------------------------------------
`Base` | 同义词*I0*模板参数。

### <a name="public-methods"></a>公共方法

名称                                                   | 描述
------------------------------------------------------ | ----------------------------------------------------------------------------------------
[Interfacetraits:: Cancastto](#cancastto)               | 指示是否指定的指针可以转换为一个指向`Base`。
[Interfacetraits:: Casttobase](#casttobase)             | 将转换为指针指定的指针`Base`。
[Interfacetraits:: Casttounknown](#casttounknown)       | 将转换为指针指定的指针`IUnknown`。
[Interfacetraits:: Fillarraywithiid](#fillarraywithiid) | 为指定的接口 ID`Base`索引参数指定的数组元素。
[Interfacetraits:: Verify](#verify)                     | 验证`Base`正确派生。

### <a name="public-constants"></a>公共常量

name                                   | 描述
-------------------------------------- | ---------------------------------------------------------------------------------------
[Interfacetraits:: Iidcount](#iidcount) | 保存数量的接口 Id 与当前关联`InterfaceTraits`对象。

## <a name="inheritance-hierarchy"></a>继承层次结构

`InterfaceTraits`

## <a name="requirements"></a>要求

**标头：** implements.h

**Namespace:** Microsoft::WRL::Details

## <a name="cancastto"></a>Interfacetraits:: Cancastto

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
指向类型的名称。

*riid*<br/>
接口 ID `Base`。

*ppv*<br/>
如果此操作成功， *ppv*指向由指定的界面`Base`。 否则为*ppv*设置为`nullptr`。

### <a name="return-value"></a>返回值

**true**此操作是否成功并*ptr*被强制转换为一个指向`Base`; 否则为**false**。

### <a name="remarks"></a>备注

指示是否指定的指针可以转换为一个指向`Base`。

有关详细信息`Base`，请参阅[公共 Typedef](#public-typedefs)部分。

## <a name="casttobase"></a>Interfacetraits:: Casttobase

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
template<typename T>
static __forceinline Base* CastToBase(
   _In_ T* ptr
);
```

### <a name="parameters"></a>参数

*T*<br/>
参数的类型*ptr*。

*ptr*<br/>
指向类型指针*T*。

### <a name="return-value"></a>返回值

一个指向`Base`。

### <a name="remarks"></a>备注

将转换为指针指定的指针`Base`。

有关详细信息`Base`，请参阅[公共 Typedef](#public-typedefs)部分。

## <a name="casttounknown"></a>Interfacetraits:: Casttounknown

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
template<typename T>
static __forceinline IUnknown* CastToUnknown(
   _In_ T* ptr
);
```

### <a name="parameters"></a>参数

*T*<br/>
参数的类型*ptr*。

*ptr*<br/>
指向类型的指针*T*。

### <a name="return-value"></a>返回值

从其指向 IUnknown 的指针`Base`派生。

### <a name="remarks"></a>备注

将转换为指针指定的指针`IUnknown`。

有关详细信息`Base`，请参阅[公共 Typedef](#public-typedefs)部分。

## <a name="fillarraywithiid"></a>Interfacetraits:: Fillarraywithiid

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
__forceinline static void FillArrayWithIid(
   _Inout_ unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>参数

*index*<br/>
指向包含一个从零开始的索引值的字段。

*iid*<br/>
接口 Id 的数组。

### <a name="remarks"></a>备注

为指定的接口 ID`Base`索引参数指定的数组元素。

与此 API 的名称，修改只有一个数组元素;不是整个数组。

有关详细信息`Base`，请参阅[公共 Typedef](#public-typedefs)部分。

## <a name="iidcount"></a>Interfacetraits:: Iidcount

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
static const unsigned long IidCount = 1;
```

### <a name="remarks"></a>备注

保存数量的接口 Id 与当前关联`InterfaceTraits`对象。

## <a name="verify"></a>Interfacetraits:: Verify

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
__forceinline static void Verify();
```

### <a name="remarks"></a>备注

验证`Base`正确派生。

有关详细信息`Base`，请参阅[公共 Typedef](#public-typedefs)部分。

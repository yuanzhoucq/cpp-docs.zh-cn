---
title: RuntimeClassBaseT 结构
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::RuntimeClassBaseT
- implements/Microsoft::WRL::Details::RuntimeClassBaseT::AsIID
- implements/Microsoft::WRL::Details::RuntimeClassBaseT::GetImplementedIIDS
helpviewer_keywords:
- Microsoft::WRL::Details::RuntimeClassBaseT structure
- Microsoft::WRL::Details::RuntimeClassBaseT::AsIID method
- Microsoft::WRL::Details::RuntimeClassBaseT::GetImplementedIIDS method
ms.assetid: a62775fb-3359-4f45-9ff1-c07fa8da464b
ms.openlocfilehash: 5d93b3e86e7ba105a42ccbedbbf44c51ada97bbd
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/16/2019
ms.locfileid: "54335562"
---
# <a name="runtimeclassbaset-structure"></a>RuntimeClassBaseT 结构

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
template <unsigned int RuntimeClassTypeT>
friend struct Details::RuntimeClassBaseT;
```

### <a name="parameters"></a>参数

*RuntimeClassTypeT*<br/>
指定一个或多个标记的字段[RuntimeClassType](runtimeclasstype-enumeration.md)枚举器。

## <a name="remarks"></a>备注

提供的帮助器方法`QueryInterface`操作和入门的接口 Id。

## <a name="members"></a>成员

### <a name="protected-methods"></a>受保护的方法

名称                                                         | 描述
------------------------------------------------------------ | -----------------------------------------------------------------------------
[RuntimeClassBaseT::AsIID](#asiid)                           | 检索指向指定的接口 id。
[RuntimeClassBaseT::GetImplementedIIDS](#getimplementediids) | 检索接口实现由指定类型的 Id 的数组。

## <a name="inheritance-hierarchy"></a>继承层次结构

`RuntimeClassBaseT`

## <a name="requirements"></a>要求

**标头：** implements.h

**命名空间：** Microsoft::WRL::Details

## <a name="asiid"></a>RuntimeClassBaseT::AsIID

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
template<typename T>
__forceinline static HRESULT AsIID(
   _In_ T* implements,
   REFIID riid,
   _Deref_out_ void **ppvObject
);
```

### <a name="parameters"></a>参数

*T*<br/>
实现接口 ID 由参数指定的类型*riid*。

*implements*<br/>
指定模板参数的类型的变量*T*。

*riid*<br/>
要检索的接口 ID。

*ppvObject*<br/>
如果此操作成功，由参数指定指针-到-a-指向接口的指针*riid*。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK否则为描述错误的 HRESULT。

### <a name="remarks"></a>备注

检索指向指定的接口 id。

## <a name="getimplementediids"></a>RuntimeClassBaseT::GetImplementedIIDS

支持 WRL 基础结构，不应在代码中直接使用。

```cpp
template<typename T>
__forceinline static HRESULT GetImplementedIIDS(
   _In_ T* implements,
   _Out_ ULONG *iidCount,
   _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids
);
```

### <a name="parameters"></a>参数

*T*<br/>
类型*实现*参数。

*implements*<br/>
为参数指定的类型的指针*T*。

*iidCount*<br/>
接口 Id 来检索最大数目。

*iids*<br/>
如果此操作成功，完成的接口实现的类型的 Id 数组*T*。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK否则为描述错误的 HRESULT。

### <a name="remarks"></a>备注

检索接口实现由指定类型的 Id 的数组。

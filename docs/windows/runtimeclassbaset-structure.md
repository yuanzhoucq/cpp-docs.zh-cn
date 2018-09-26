---
title: RuntimeClassBaseT 结构 |Microsoft Docs
ms.custom: ''
ms.date: 09/24/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::RuntimeClassBaseT
- implements/Microsoft::WRL::Details::RuntimeClassBaseT::AsIID
- implements/Microsoft::WRL::Details::RuntimeClassBaseT::GetImplementedIIDS
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Details::RuntimeClassBaseT structure
- Microsoft::WRL::Details::RuntimeClassBaseT::AsIID method
- Microsoft::WRL::Details::RuntimeClassBaseT::GetImplementedIIDS method
ms.assetid: a62775fb-3359-4f45-9ff1-c07fa8da464b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c9e7f5b38d3434e8753646db4733218978e7e766
ms.sourcegitcommit: edb46b0239a0e616af4ec58906e12338c3e8d2c6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/25/2018
ms.locfileid: "47169705"
---
# <a name="runtimeclassbaset-structure"></a>RuntimeClassBaseT 结构

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
template <
   unsigned int RuntimeClassTypeT
>
friend struct Details::RuntimeClassBaseT;
```

### <a name="parameters"></a>参数

*RuntimeClassTypeT*<br/>
指定一个或多个标记的字段[RuntimeClassType](../windows/runtimeclasstype-enumeration.md)枚举器。

## <a name="remarks"></a>备注

提供的帮助器方法`QueryInterface`操作和入门的接口 Id。

## <a name="members"></a>成员

### <a name="protected-methods"></a>受保护的方法

名称                                                         | 描述
------------------------------------------------------------ | -----------------------------------------------------------------------------
[Runtimeclassbaset:: Asiid](#asiid)                           | 检索指向指定的接口 id。
[Runtimeclassbaset:: Getimplementediids](#getimplementediids) | 检索接口实现由指定类型的 Id 的数组。

## <a name="inheritance-hierarchy"></a>继承层次结构

`RuntimeClassBaseT`

## <a name="requirements"></a>要求

**标头：** implements.h

**Namespace:** Microsoft::WRL::Details

## <a name="asiid"></a>Runtimeclassbaset:: Asiid

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

*实现*<br/>
指定模板参数的类型的变量*T*。

*riid*<br/>
要检索的接口 ID。

*ppvObject*<br/>
如果此操作成功，由参数指定指针-到-a-指向接口的指针*riid*。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK否则为描述错误的 HRESULT。

### <a name="remarks"></a>备注

检索指向指定的接口 id。

## <a name="getimplementediids"></a>Runtimeclassbaset:: Getimplementediids

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

*实现*<br/>
为参数指定的类型的指针*T*。

*iidCount*<br/>
接口 Id 来检索最大数目。

*iid*<br/>
如果此操作成功，完成的接口实现的类型的 Id 数组*T*。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK否则为描述错误的 HRESULT。

### <a name="remarks"></a>备注

检索接口实现由指定类型的 Id 的数组。

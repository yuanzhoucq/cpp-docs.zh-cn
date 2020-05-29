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
ms.openlocfilehash: 06a9f73e00d541b0e5bcbe20c57befe4a67c5132
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375724"
---
# <a name="runtimeclassbaset-structure"></a>RuntimeClassBaseT 结构

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
template <unsigned int RuntimeClassTypeT>
friend struct Details::RuntimeClassBaseT;
```

### <a name="parameters"></a>参数

*运行时类类型T*<br/>
指定一个或多个[运行时类类型](runtimeclasstype-enumeration.md)枚举器的标志字段。

## <a name="remarks"></a>备注

为`QueryInterface`操作和获取接口识别器提供帮助程序方法。

## <a name="members"></a>成员

### <a name="protected-methods"></a>受保护的方法

名称                                                         | 说明
------------------------------------------------------------ | -----------------------------------------------------------------------------
[运行时类基础：：AsIID](#asiid)                           | 检索指向指定接口 ID 的指针。
[运行时类基础：：获取已实现 IIDS](#getimplementediids) | 检索由指定类型实现的接口指示的数组。

## <a name="inheritance-hierarchy"></a>继承层次结构

`RuntimeClassBaseT`

## <a name="requirements"></a>要求

**标题：** 实现.h

**命名空间：** 微软：：WRL：:D

## <a name="runtimeclassbasetasiid"></a><a name="asiid"></a>运行时类基础：：AsIID

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
实现参数*riid*指定的接口 ID 的类型。

*实现*<br/>
模板参数*T*指定的类型的变量。

*riid*<br/>
要检索的接口 ID。

*ppvObject*<br/>
如果此操作成功，则指向参数*riid*指定的接口的指针指向指针。

### <a name="return-value"></a>返回值

S_OK如果成功;否则，描述错误的 HRESULT。

### <a name="remarks"></a>备注

检索指向指定接口 ID 的指针。

## <a name="runtimeclassbasetgetimplementediids"></a><a name="getimplementediids"></a>运行时类基础：：获取已实现 IIDS

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
*实现*参数的类型。

*实现*<br/>
指向参数*T*指定的类型的指针。

*iidCount*<br/>
要检索的接口指示的最大数量。

*伊德*<br/>
如果此操作成功完成，则按*类型 T*实现的接口 I 的数组。

### <a name="return-value"></a>返回值

S_OK如果成功;否则，描述错误的 HRESULT。

### <a name="remarks"></a>备注

检索由指定类型实现的接口指示的数组。

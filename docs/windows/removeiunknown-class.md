---
title: RemoveIUnknown 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::RemoveIUnknown
dev_langs:
- C++
ms.assetid: 998e711a-7d1a-44c6-a016-e6167aa40863
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 81892b624425032c8f0e69fe667ad24026c40ca4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46410257"
---
# <a name="removeiunknown-class"></a>RemoveIUnknown 类

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
template <
   typename T
>
struct RemoveIUnknown;

template <
   typename T
>
class RemoveIUnknown : public T;
```

### <a name="parameters"></a>参数

*T*<br/>
一个类。

## <a name="remarks"></a>备注

创建类型的它等效于`IUnknown`-基于的类型，但具有非虚拟`QueryInterface`， `AddRef`，和`Release`成员函数。

默认情况下，COM 方法提供了虚拟`QueryInterface`， `AddRef`，和`Release`方法。 但是，`ComPtr`不需要的虚方法的开销。 `RemoveIUnknown` 通过提供专用的非虚拟消除这些开销`QueryInterface`， `AddRef`，和`Release`方法。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|描述|
|----------|-----------------|
|`ReturnType`|等同于模板参数的类型的同义词*T*却非虚拟`IUnknown`成员。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`T`

`RemoveIUnknown`

## <a name="requirements"></a>要求

**标头：** client.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>请参阅

[Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)
---
title: RemoveReference 结构 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::RemoveReference
dev_langs:
- C++
helpviewer_keywords:
- RemoveReference structure
ms.assetid: 43ff91bb-815a-440e-b9fb-7dcbb7c863af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f6ab085e1bed3909090990cfa8e265bea792a483
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46447019"
---
# <a name="removereference-structure"></a>RemoveReference 结构

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
template<class T>
struct RemoveReference;
template<class T>
struct RemoveReference<T&>;
template<class T>
struct RemoveReference<T&&>;
```

### <a name="parameters"></a>参数

*T*<br/>
一个类。

## <a name="remarks"></a>备注

去除从指定的类模板参数引用或右值引用的特征。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|描述|
|----------|-----------------|
|`Type`|类模板参数的同义词。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`RemoveReference`

## <a name="requirements"></a>要求

**标头：** internal.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>请参阅

[Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)
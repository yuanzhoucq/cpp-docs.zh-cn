---
title: RuntimeClassBaseT 结构 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::RuntimeClassBaseT
dev_langs:
- C++
ms.assetid: a62775fb-3359-4f45-9ff1-c07fa8da464b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bcfce810dff7862c60fca853b216eeb05d09dd0f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46414896"
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

## <a name="inheritance-hierarchy"></a>继承层次结构

`RuntimeClassBaseT`

## <a name="requirements"></a>要求

**标头：** implements.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>请参阅

[Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)
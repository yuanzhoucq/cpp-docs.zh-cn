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
ms.openlocfilehash: 0d137281d7f573275b216eecaea9e4f09564b9f6
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43206546"
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

*RuntimeClassTypeT*  
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

[参考 （Windows 运行时库）](https://msdn.microsoft.com/00000000-0000-0000-0000-000000000000)  
[Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)
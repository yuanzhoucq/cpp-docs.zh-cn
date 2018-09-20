---
title: ImplementsHelper 结构 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::ImplementsHelper
dev_langs:
- C++
helpviewer_keywords:
- ImplementsHelper structure
ms.assetid: b857ba80-81bd-4e53-92b6-210991954243
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4ff40e03bf464d4c6f434b491c8b48d2b797d72b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46440521"
---
# <a name="implementshelper-structure"></a>ImplementsHelper 结构

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
template <
   typename RuntimeClassFlagsT,
   typename ILst,
   bool IsDelegateToClass
>
friend struct Details::ImplementsHelper;
```

### <a name="parameters"></a>参数

*RuntimeClassFlagsT*<br/>
指定一个或多个标记的字段[RuntimeClassType](../windows/runtimeclasstype-enumeration.md)枚举器。

*ILst*<br/>
接口 Id 的列表。

*IsDelegateToClass*<br/>
指定 **，则返回 true**如果的当前实例`Implements`是一个基类中的第一个接口 ID *ILst*; 否则为**false**。

## <a name="remarks"></a>备注

可帮助实现[实现](../windows/implements-structure.md)结构。

此模板会遍历接口的列表，并将其添加作为基类，这些类，以及启用所需的信息`QueryInterface`。

## <a name="members"></a>成员

## <a name="inheritance-hierarchy"></a>继承层次结构

`ImplementsHelper`

## <a name="requirements"></a>要求

**标头：** implements.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>请参阅

[Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)
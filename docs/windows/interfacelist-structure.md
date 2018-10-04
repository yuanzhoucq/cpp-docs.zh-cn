---
title: InterfaceList 结构 |Microsoft Docs
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceList
dev_langs:
- C++
helpviewer_keywords:
- InterfaceList structure
ms.assetid: 6ec3228d-eb3e-4b7e-aef1-7dcf17bdf61a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3d9cbc1dfb31d744086e7a138521ae24f58e693f
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2018
ms.locfileid: "48788651"
---
# <a name="interfacelist-structure"></a>InterfaceList 结构

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
template <typename T, typename U>
struct InterfaceList;
```

### <a name="parameters"></a>参数

*T*<br/>
接口名称;递归列表中的第一个接口。

*U*<br/>
接口名称;其余的接口中的递归列表。

## <a name="remarks"></a>备注

用于创建接口的递归列表。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|描述|
|----------|-----------------|
|`FirstT`|模板参数的同义词*T*。|
|`RestT`|模板参数的同义词*U*。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`InterfaceList`

## <a name="requirements"></a>要求

**标头：** implements.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>请参阅

[Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)
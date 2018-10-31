---
title: EnableIf 结构 |Microsoft Docs
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::EnableIf
dev_langs:
- C++
helpviewer_keywords:
- EnableIf structure
ms.assetid: 7825b283-e6b2-4f39-a4b9-c03bcd431b8e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2512c9b8b552027f4a0b4d72788e19d77a35d92e
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2018
ms.locfileid: "48789184"
---
# <a name="enableif-structure"></a>EnableIf 结构

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
template <bool b, typename T = void>
struct EnableIf;

template <typename T>
struct EnableIf<true, T>;
```

### <a name="parameters"></a>参数

*T*<br/>
一种类型。

*b*<br/>
布尔表达式。

## <a name="remarks"></a>备注

定义指定如果第一个模板参数的计算结果为第二个模板参数的类型的数据成员 **，则返回 true**。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|描述|
|----------|-----------------|
|`type`|如果模板参数*b*的计算结果为**true**，部分专用化定义数据成员`type`类型`T`。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`EnableIf`

## <a name="requirements"></a>要求

**标头：** internal.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>请参阅

[Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)
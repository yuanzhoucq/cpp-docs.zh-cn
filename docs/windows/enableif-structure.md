---
title: EnableIf 结构 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 2cc4e8f272838e5fa1de3eac8bd04a4ec3407dee
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46400661"
---
# <a name="enableif-structure"></a>EnableIf 结构

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
template <
   bool b,
   typename T = void
>

struct EnableIf;
template <
   typename T
>
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
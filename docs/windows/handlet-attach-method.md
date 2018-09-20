---
title: 'Handlet:: Attach 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Attach
dev_langs:
- C++
helpviewer_keywords:
- Attach method
ms.assetid: a8783a18-bbf6-456c-98a3-e2048a10d79f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5cfb8249d228b5a8e609952e1118bc23a75b9c98
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46426440"
---
# <a name="handletattach-method"></a>HandleT::Attach 方法

将指定的句柄与当前相关联**HandleT**对象。

## <a name="syntax"></a>语法

```cpp
void Attach(
   typename HandleTraits::Type h
);
```

#### <a name="parameters"></a>参数

*h*<br/>
句柄。

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers

## <a name="see-also"></a>请参阅

[HandleT 类](../windows/handlet-class.md)
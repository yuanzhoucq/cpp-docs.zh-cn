---
title: '&lt;atomic&gt; 枚举| Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- atomic/std::memory_order
ms.assetid: cd3a81c5-a19e-448f-952a-c34c717f21a9
caps.latest.revision: 11
helpviewer_keywords:
- std::memory_order
manager: ghogen
ms.openlocfilehash: 59cd642bf1a74c2a3c07cb72b4ee072e3e4514eb
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="ltatomicgt-enums"></a>&lt;atomic&gt; 枚举

## <a name="memory_order_enum"></a>  memory_order Enum

为内存位置上的同步操作提供符号名称。 这些操作将影响一个线程内的分配如何在另一个线程内变得可见。

```cpp
typedef enum memory_order {
    memory_order_relaxed,
    memory_order_consume,
    memory_order_acquire,
    memory_order_release,
    memory_order_acq_rel,
    memory_order_seq_cst,
} memory_order;
```

### <a name="enumeration-members"></a>枚举成员

|||
|-|-|
|`memory_order_relaxed`|无需排序。|
|`memory_order_consume`|加载操作将充当内存位置上的消耗操作。|
|`memory_order_acquire`|加载操作将充当内存位置上的获取操作。|
|`memory_order_release`|存储操作将充当内存位置上的释放操作。|
|`memory_order_acq_rel`|将 `memory_order_acquire` 和 `memory_order_release` 结合。|
|`memory_order_seq_cst`|将 `memory_order_acquire` 和 `memory_order_release` 结合。 标记为 `memory_order_seq_cst` 的内存访问必须顺序一致。|

## <a name="see-also"></a>请参阅

[\<atomic>](../standard-library/atomic.md)<br/>

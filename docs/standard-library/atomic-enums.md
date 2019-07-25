---
title: '&lt;atomic&gt; 枚举'
ms.date: 11/04/2016
f1_keywords:
- atomic/std::memory_order
ms.assetid: cd3a81c5-a19e-448f-952a-c34c717f21a9
helpviewer_keywords:
- std::memory_order
ms.openlocfilehash: 14b816177593a9f6dade60e36676a37f724fc209
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457599"
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

[\<atomic>](../standard-library/atomic.md)

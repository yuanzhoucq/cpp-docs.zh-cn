---
title: "&lt;atomic&gt; 枚举| Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: []
ms.assetid: cd3a81c5-a19e-448f-952a-c34c717f21a9
caps.latest.revision: 11
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 94167b5068e3fb1370528d42c80d338a486cd68e
ms.lasthandoff: 02/24/2017

---
# <a name="ltatomicgt-enums"></a>&lt;atomic&gt; 枚举
  
##  <a name="memory_order_enum"></a>  memory_order Enum  
 为内存位置上的同步操作提供符号名称。 这些操作将影响一个线程内的分配如何在另一个线程内变得可见。  
  
```
typedef enum memory_order {
    memory_order_relaxed,
    memory_order_consume,
    memory_order_acquire,
    memory_order_release,
    memory_order_acq_rel,
    memory_order_seq_cst,
} memory_order;
```  
  
### <a name="remarks"></a>备注  
  
|||  
|-|-|  
|`memory_order_relaxed`|无需排序。|  
|`memory_order_consume`|加载操作将充当内存位置上的消耗操作。|  
|`memory_order_acquire`|加载操作将充当内存位置上的获取操作。|  
|`memory_order_release`|存储操作将充当内存位置上的释放操作。|  
|`memory_order_acq_rel`|将 `memory_order_acquire` 和 `memory_order_release` 结合。|  
|`memory_order_seq_cst`|将 `memory_order_acquire` 和 `memory_order_release` 结合。 标记为 `memory_order_seq_cst` 的内存访问必须顺序一致。|  
  
## <a name="see-also"></a>另请参阅  
 [\<atomic>](../standard-library/atomic.md)





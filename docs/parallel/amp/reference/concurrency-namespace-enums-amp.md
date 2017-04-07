---
title: "并发命名空间枚举 (AMP) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- amp/Concurrency::access_type
- amp/Concurrency::queuing_mode
dev_langs:
- C++
ms.assetid: 4c87457e-184f-4992-81ab-ca75e7d524ab
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: fc190feb08d9b221cd1cc21a9c91ad567c86c848
ms.openlocfilehash: b9555023e01cb765ca943fcaaf785cdc2b4e2d0d
ms.lasthandoff: 02/24/2017

---
# <a name="concurrency-namespace-enums-amp"></a>并发命名空间枚举 (AMP)
|||  
|-|-|  
|[access_type 枚举](#access_type)|[queuing_mode 枚举](#queuing_mode)|  
  
##  <a name="access_type"></a>access_type 枚举  
 用来表示对数据的访问的各种类型的枚举类型。  
  
```  
enum access_type;  
```  
### <a name="values"></a>值  
  
|名称|描述|  
|----------|-----------------|  
|`access_type_auto`|自动选择最佳`access_type`加速器。|  
|`access_type_none`|专用。 仅可访问，在快捷键上而不是在 CPU 分配。|  
|`access_type_read`|共享。 分配在快捷键上可以访问，以及在 CPU 上可读。|  
|`access_type_read_write`|共享。 分配在快捷键上可访问，且是在 CPU 上可写。|  
|`access_type_write`|共享。 分配在快捷键上可访问且是读取和写入在 CPU 上。|  

  
##  <a name="queuing_mode"></a>queuing_mode 枚举  
 指定在快捷键支持的排队模式。  
  
```  
enum queuing_mode;  
``` 
### <a name="values"></a>值  
  
|名称|描述|  
|----------|-----------------|  
|`queuing_mode_immediate`|指定的任何排队模式命令，例如， [parallel_for_each 函数 (c + + AMP)](concurrency-namespace-functions-amp.md#parallel_for_each)，只要它们返回给调用方被发送到相应的加速器设备。|  
|`queuing_mode_automatic`|指定命令进行排队等候上对应于命令队列的排队模式[accelerator_view](accelerator-view-class.md)对象。 命令发送到设备时[accelerator_view:: flush](accelerator-view-class.md#flush)调用。|   
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace (c + + AMP)](concurrency-namespace-cpp-amp.md)


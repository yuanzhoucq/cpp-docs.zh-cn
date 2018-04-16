---
title: "并发命名空间枚举 (AMP) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- amp/Concurrency::access_type
- amp/Concurrency::queuing_mode
dev_langs:
- C++
ms.assetid: 4c87457e-184f-4992-81ab-ca75e7d524ab
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d17378a34698cc80d356983898e0023b76877140
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="concurrency-namespace-enums-amp"></a>并发命名空间枚举 (AMP)
|||  
|-|-|  
|[access_type Enumeration](#access_type)|[queuing_mode 枚举](#queuing_mode)|  
  
##  <a name="access_type"></a>  access_type Enumeration  
 用于表示数据的访问权限的各种类型的枚举类型。  
  
```  
enum access_type;  
```  
### <a name="values"></a>值  
  
|名称|描述|  
|----------|-----------------|  
|`access_type_auto`|自动选择最佳`access_type`快捷键。|  
|`access_type_none`|专用。 分配仅可在快捷键上和不在 CPU 上访问。|  
|`access_type_read`|共享。 分配快捷键上是可访问且在 CPU 上可读。|  
|`access_type_read_write`|共享。 分配快捷键上是可访问以及在 CPU 上可写。|  
|`access_type_write`|共享。 分配快捷键上是可访问和可读且在 CPU 上可写。|  

  
##  <a name="queuing_mode"></a>  queuing_mode Enumeration  
 指定在快捷键受支持的排队模式。  
  
```  
enum queuing_mode;  
``` 
### <a name="values"></a>值  
  
|名称|描述|  
|----------|-----------------|  
|`queuing_mode_immediate`|对任何指定排队模式命令，例如， [parallel_for_each 函数 (c + + AMP)](concurrency-namespace-functions-amp.md#parallel_for_each)，只要它们返回到调用方发送到相应的快捷键设备。|  
|`queuing_mode_automatic`|指定命令，将在对应的命令队列上排队的排队模式[accelerator_view](accelerator-view-class.md)对象。 命令发送到设备时[accelerator_view:: flush](accelerator-view-class.md#flush)调用。|   
  
## <a name="see-also"></a>请参阅  
 [并发命名空间 (C++ AMP)](concurrency-namespace-cpp-amp.md)

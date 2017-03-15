---
title: "堆常量 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_HEAPBADPTR"
  - "_HEAPEMPTY"
  - "_HEAPBADBEGIN"
  - "_HEAPOK"
  - "_HEAPBADNODE"
  - "_HEAPEND"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_HEAPBADBEGIN 常量"
  - "_HEAPBADNODE 常量"
  - "_HEAPBADPTR 常量"
  - "_HEAPEMPTY 常量"
  - "_HEAPEND 常量"
  - "_HEAPOK 常量"
  - "堆常量"
  - "HEAPBADBEGIN 常量"
  - "HEAPBADNODE 常量"
  - "HEAPBADPTR 常量"
  - "HEAPEMPTY 常量"
  - "HEAPEND 常量"
  - "HEAPOK 常量"
ms.assetid: 3f751bb9-2dc4-486f-b5f5-9061c96d3754
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 堆常量
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 语法  
  
```  
  
#include <malloc.h>  
  
```  
  
## 备注  
 这些常量提供指示堆状态的返回值。  
  
|常量|含义|  
|--------|--------|  
|`_HEAPBADBEGIN`|初始的头信息未找到或者无效。|  
|`_HEAPBADNODE`|找到错误节点，或者堆已损坏。|  
|`_HEAPBADPTR`|**\_HEAPINFO** 结构的**\_pentry** 字段不包含到堆的有效指针 \(仅`_heapwalk` 例程\)。|  
|`_HEAPEMPTY`|堆尚未初始化。|  
|`_HEAPEND`|已成功到达堆结束处\(仅`_heapwalk` 例程\)。|  
|`_HEAPOK`|堆一致 \(仅`_heapset` 和 `_heapchk` 实例\)。  到目前为止没有错误；**\_HEAPINFO** 结构包含以下输入的信息 \(仅`_heapwalk` 例程\)。|  
  
## 请参阅  
 [\_heapchk](../c-runtime-library/reference/heapchk.md)   
 [\_heapset](../c-runtime-library/heapset.md)   
 [\_heapwalk](../c-runtime-library/reference/heapwalk.md)   
 [全局常量](../c-runtime-library/global-constants.md)
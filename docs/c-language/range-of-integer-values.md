---
title: "整数值的范围 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 0e9c6161-8f3f-4bfb-9fcc-a6c8dc97d702
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 整数值的范围
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**ANSI 3.1.2.5** 各种类型的整数的值的表示形式和集  
  
 整数包含 32 位（4 个字节）。  带符号整数以 2 的补数的形式表示。  最高有效位保存符号：1 表示负数，0 表示整数或零。  下面列出了这些值：  
  
|类型|最小值和最大值|  
|--------|-------------|  
|**unsigned short**|0 到 65535|  
|`signed short`|–32768 到 32767|  
|`unsigned long`|0 到 4294967295|  
|**signed long**|–2147483648 到 2147483647|  
  
## 请参阅  
 [整数](../c-language/integers.md)
---
title: "结构成员的填充和对齐 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "结构成员, 填充和对齐"
ms.assetid: c999820b-dd47-41fc-b923-e4c7ebbcd30f
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 结构成员的填充和对齐
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**ANSI 3.5.2.1** 结构的成员的填充和对齐方式，以及位域是否可以跨存储单元边界  
  
 结构成员按其声明顺序进行存储：第一个成员的内存地址最低，最后一个成员的内存地址最高。  
  
 每个数据对象具有 alignment\-requirement。  所有数据（结构、联合和数组除外）的对齐要求是对象的大小或当前打包大小（使用 \/Zp 或 `pack` 杂注指定，以较小者为准）。  对于结构、联合和数组，对齐要求是其成员的最大对齐要求。  为每个对象分配一个 offset，以便  
  
 *offset*  `%` *alignment\-requirement* `==` 0  
  
 如果整型的大小相同，并且下一个位域适合当前分配单元而未跨位域的常见对齐要求所强加的边界，则将相邻位域打包到相同的 1 字节、2 字节或 4 字节分配单元中。  
  
## 请参阅  
 [结构、联合、枚举和位域](../c-language/structures-unions-enumerations-and-bit-fields.md)
---
title: "链接器工具警告 LNK4219 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4219"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4219"
ms.assetid: 363fedf4-b10c-4985-811a-55a9fba688d6
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 链接器工具警告 LNK4219
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

fixup name 链接地址信息溢出。目标“target symbol name”超出范围，正在插入 thunk  
  
 链接器在地址或偏移量无法适应给定指令时插入了 thunk，因为目标符号距离指令位置太远。  
  
 可能需要对图像重排序（例如使用 [\/ORDER](../../build/reference/order-put-functions-in-order.md) 选项），以避免额外的间接寻址级别。
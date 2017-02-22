---
title: "数学错误 M6203 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "M6203"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "M6203"
ms.assetid: bd7fdd1c-83e4-4d6a-901e-10a0308bf5be
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 数学错误 M6203
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: \_OVERFLOW 错误  
  
 给定函数的结果太大而无法表示。  
  
 该错误用函数名、它的参数以及错误类型调用 `_matherr` 函数。  可以重写 `_matherr` 函数，以自定义某些运行时浮点数学错误的处理方法。
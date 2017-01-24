---
title: "数学错误 M6201 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "M6201"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "M6201"
ms.assetid: 4041c331-d9aa-4dd4-b565-7dbe0218538c
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 数学错误 M6201
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: \_DOMAIN 错误  
  
 给定函数的参数超出该函数的合法输入值域。  
  
## 示例  
  
```  
result = sqrt(-1.0)   // C statement  
result = SQRT(-1.0)   !  FORTRAN statement  
```  
  
 该错误用函数名、它的参数以及错误类型调用 `_matherr` 函数。  可以重写 `_matherr` 函数，以自定义某些运行时浮点数学错误的处理方法。
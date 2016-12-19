---
title: ".IF | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - ".IF"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".IF directive"
ms.assetid: dccc7615-8fc7-4829-9f39-0ee405f6c1e3
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# .IF
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

生成、测试 `condition1` 的代码 \(轴， AMP\_GT 7\) 和执行 *语句* ，如果该条件为 true。  
  
## 语法  
  
```  
  
   .IF condition1   
statements  
[[.ELSEIF condition2   
   statements]]  
[[.ELSE  
   statements]]  
.ENDIF  
```  
  
## 备注  
 如果 [.ELSE](../../assembler/masm/dot-else.md) 之后，它将执行语句，如果原始条件为 false。  请注意条件在运行时计算。  
  
## 请参阅  
 [Directives Reference](../../assembler/masm/directives-reference.md)
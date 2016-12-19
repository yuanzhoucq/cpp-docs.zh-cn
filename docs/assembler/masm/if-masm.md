---
title: "IF (MASM) | Microsoft Docs"
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
  - "if"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IF directive"
ms.assetid: 82e43712-4f0c-4bf6-90ce-0663e81af707
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# IF (MASM)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

授予 *ifstatements* 集，如果 *expression1* 为 true \(非零\) 或 *elseifstatements* ，如果 *expression1* 中的错误 \(0\)，并 *expression2* 为 true。  
  
## 语法  
  
```  
  
   IF expression1  
ifstatements  
[[ELSEIF expression2  
   elseifstatements]]  
[[ELSE  
   elsestatements]]  
ENDIF  
```  
  
## 备注  
 下面的指令可以通过 [ELSEIF](../../assembler/masm/elseif-masm.md)替换: **ELSEIFB**、 **ELSEIFDEF**、 **ELSEIFDIF**、 **ELSEIFDIFI**、 **ELSEIFE**、 **ELSEIFIDN**、 **ELSEIFIDNI**、 **ELSEIFNB**和 **ELSEIFNDEF**。  或者，存在，或者前表达式是错误的，这 *elsestatements* 。  请注意计算表达式在汇编时。  
  
## 请参阅  
 [Directives Reference](../../assembler/masm/directives-reference.md)
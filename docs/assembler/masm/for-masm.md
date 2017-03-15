---
title: "FOR (MASM) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "for"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "FOR directive"
ms.assetid: 99872e61-f503-4d34-b305-59f8556ba6b7
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# FOR (MASM)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

标记为每 `argument`一次将重复的块，在当前 `argument` 替换每重复 `parameter` 。  
  
## 语法  
  
```  
  
   FOR   
   parameter [[:REQ | :=default]] , <argument [[, argument]]...>  
statements  
ENDM  
```  
  
## 备注  
 和 [IRP](../../assembler/masm/irp.md)相同。  
  
## 请参阅  
 [Directives Reference](../../assembler/masm/directives-reference.md)
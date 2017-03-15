---
title: "PUSHCONTEXT | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PUSHCONTEXT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PUSHCONTEXT directive"
ms.assetid: 18e528ee-df6c-4ce6-8823-b35b40f757fd
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# PUSHCONTEXT
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

保存部分或全部当前 `context`:段寄存器，假设基数值、列表和 cref 标志或处理器\/协处理器值。  `context` 可以是 **假定**、 `RADIX`、 **列表**、 **CPU**或 **任何**。  
  
## 语法  
  
```  
  
PUSHCONTEXT context  
```  
  
## 请参阅  
 [Directives Reference](../../assembler/masm/directives-reference.md)
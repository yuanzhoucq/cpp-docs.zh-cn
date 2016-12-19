---
title: "ML Nonfatal Error A2096 | Microsoft Docs"
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
  - "A2096"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "A2096"
ms.assetid: bab0b5ee-b39f-4e44-a41a-3f949fab4297
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ML Nonfatal Error A2096
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**段落、组或预期的段寄存器**  
  
 段或组预计的，但未找到。  
  
 发生的操作之一:  
  
-   左侧操作数指定与段重写运算符 \(**:**\) 不是段寄存器 \(CS、 DS、 SS、 ES、 FS 或 GS\)，组名、段名或段落表达式。  
  
-   [假定](../../assembler/masm/assume.md) 指令将一段寄存器，没有有效的段地址，段寄存器、组或特定 **简单** 组。  
  
## 请参阅  
 [ML Error Messages](../../assembler/masm/ml-error-messages.md)
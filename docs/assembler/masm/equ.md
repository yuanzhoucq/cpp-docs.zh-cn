---
title: "EQU | Microsoft Docs"
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
  - "EQU"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "EQU directive"
ms.assetid: 96db466a-1eab-45bd-a3c2-5a59bd754eab
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# EQU
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

第一个指令将 *表达式的* 数值与 *名称*。  
  
## 语法  
  
```  
  
      name EQU expression  
name EQU <text>  
```  
  
## 备注  
 该 *名称* 不能后重新定义。  
  
 第二个指令分配指定的 *文本* 。 *名称*。  该名称可以后分配一个不同的 *文本* 。  [TEXTEQU](../../assembler/masm/textequ.md)参见。  
  
## 请参阅  
 [Directives Reference](../../assembler/masm/directives-reference.md)
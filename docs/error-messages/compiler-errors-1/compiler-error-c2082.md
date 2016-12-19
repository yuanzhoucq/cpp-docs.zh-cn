---
title: "编译器错误 C2082 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2082"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2082"
ms.assetid: 87a6d442-157c-46e8-9bff-8388f8338ae0
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2082
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

形参“identifier”的重定义  
  
 已在函数体中重新声明了函数的形参。 若要解决此错误，请删除重新定义。  
  
 以下示例生成 C2082：  
  
```  
// C2082.cpp void func(int i) { int i;   // C2082 int ii;   // OK }  
```
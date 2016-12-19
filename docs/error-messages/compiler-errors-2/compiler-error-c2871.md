---
title: "编译器错误 C2871 | Microsoft Docs"
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
  - "C2871"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2871"
ms.assetid: 44aeb84d-61f0-45e0-8dad-22a3cd46b7f8
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2871
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“name”: 具有该名称的命名空间不存在  
  
 当将不是命名空间的标识符传递给 [using](../Topic/using%20Directive%20\(C%23%20Reference\).md) 指令时，发生此错误。  
  
 下面的示例生成 C2871：  
  
```  
// C2871.cpp  
// compile with: /c  
using namespace d;   // C2871 d is not a namespace  
using namespace System;   // OK  
```
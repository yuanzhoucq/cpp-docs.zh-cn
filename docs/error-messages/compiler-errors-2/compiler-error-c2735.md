---
title: "编译器错误 C2735 | Microsoft Docs"
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
  - "C2735"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2735"
ms.assetid: 6ce45600-7148-4bc0-8699-af0ef137571e
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2735
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

不允许在形参类型说明符中使用“keyword”关键字  
  
 该关键字在此上下文中无效。  
  
 下面的示例生成 C2735：  
  
```  
// C2735.cpp  
void f(inline int){}   // C2735  
```
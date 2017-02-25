---
title: "编译器错误 C3239 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3239"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3239"
ms.assetid: 22a518b7-020f-4f3c-9963-a094667fd1ac
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# 编译器错误 C3239
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“type”：公共语言运行时不允许使用指向内部\/pin 指针的指针  
  
 编译器遇到了无效的类型。  
  
 下面的示例生成 C3229：  
  
```  
// C3239.cpp // compile with: /clr int main() { interior_ptr<int>* pip0;   // C3239 // OK int * pip1; interior_ptr<int> pip2; int ** pip; }  
```
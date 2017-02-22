---
title: "编译器错误 C2671 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2671"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2671"
ms.assetid: fc0ee40f-c8f3-408f-b89d-745d149c4169
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器错误 C2671
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: 静态成员函数没有“this”指针  
  
 `static` 成员函数尝试访问 `this`。  
  
 下面的示例生成 C2671：  
  
```  
// C2671.cpp  
struct S {  
   static S* const func() { return this; }  // C2671  
};  
```
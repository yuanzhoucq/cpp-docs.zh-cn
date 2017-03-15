---
title: "编译器错误 C2534 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2534"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2534"
ms.assetid: 481f9f54-5b51-4aa0-8eea-218f10807705
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器错误 C2534
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”: 构造函数无法返回值  
  
 构造函数不能返回值或具有返回类型（即使 `void` 返回类型也不可以）。  
  
 通过从构造函数定义中移除 `return` 语句可以修复此错误。  
  
 下面的示例生成 C2534：  
  
```  
// C2534.cpp  
class A {  
public:  
   int i;  
   A() { return i; }   // C2534  
};  
```
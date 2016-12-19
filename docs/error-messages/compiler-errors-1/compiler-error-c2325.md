---
title: "编译器错误 C2325 | Microsoft Docs"
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
  - "C2325"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2325"
ms.assetid: e6b0a186-3f2a-4adf-beae-fadd75492bf7
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2325
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“type”:“name”右边的意外类型  
  
 对错误类型的析构函数进行了调用。  
  
 下面的示例生成 C2325：  
  
```  
// C2325.cpp  
// compile with: /c  
class A {};  
typedef A* pA_t;  
void f() {  
    A** ppa = new A *;  
    ppa->~A*;   // C2325  
  
   pA_t *ppa2 = new pA_t;  
   ppa2->~pA_t();   // OK  
}  
```
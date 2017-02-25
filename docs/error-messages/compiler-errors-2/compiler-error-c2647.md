---
title: "编译器错误 C2647 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2647"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2647"
ms.assetid: 1034589e-bc3e-41a6-831f-2a1a4b8a2500
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C2647
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“operator”: 无法取消引用“type2”上的“type1”  
  
 指向成员的指针运算符（`->*` 或 `.*`）的左操作数无法隐式转换为与右运算符相关的类型。  
  
 下面的示例生成 C2647：  
  
```  
// C2647.cpp  
class C {};  
class D {};  
  
int main() {  
   D d, *pd;  
   C c, *pc = 0;  
   int C::*pmc = 0;  
   pd->*pmc = 0;   // C2647  
   d.*pmc = 0;   // C2647  
  
   // OK  
   pc->*pmc = 0;  
   c.*pmc = 0;  
}  
```
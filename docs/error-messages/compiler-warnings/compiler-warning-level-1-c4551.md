---
title: "编译器警告（等级 1）C4551 | Microsoft Docs"
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
  - "C4551"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4551"
ms.assetid: 458b59bd-e2d7-425f-9ba6-268ff200424f
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4551
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

缺少参数列表的函数调用  
  
 函数调用必须在函数名之后包含左括号和右括号，即使该函数未采用任何参数。  
  
 下面的示例生成 C4551：  
  
```  
// C4551.cpp  
// compile with: /W1  
void function1() {  
}  
  
int main() {  
   function1;   // C4551  
   function1();   // OK  
}  
```
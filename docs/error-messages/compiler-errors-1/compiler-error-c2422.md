---
title: "编译器错误 C2422 | Microsoft Docs"
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
  - "C2422"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2422"
ms.assetid: ef0ec302-4028-4778-b134-0b8cea4bcad9
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2422
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“operand”中的非法段重写  
  
 内联程序集代码错误地对操作数使用了段重写运算符（冒号）。可能的原因包括：  
  
-   该运算符前面的寄存器不是段寄存器。  
  
-   该运算符前面的寄存器不是该操作数中的唯一段寄存器。  
  
-   段重写运算符出现在间接寻址运算符（尖括号）内。  
  
-   段重写运算符后面的表达式不是即时操作数或内存操作数。  
  
 下面的示例生成 C2422：  
  
```  
// C2422.cpp  
// processor: x86  
int main() {  
   _asm {  
      mov AX, [BX:ES]   // C2422  
      mov AX, ES   // OK  
   }  
}  
```
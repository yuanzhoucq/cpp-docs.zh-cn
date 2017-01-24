---
title: "编译器错误 C2561 | Microsoft Docs"
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
  - "C2561"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2561"
ms.assetid: 0abe955b-53a6-4a3c-8362-b1a8eb40e8d1
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2561
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”: 函数必须返回值  
  
 该函数被声明为返回一个值，但该函数定义不包含 `return` 语句。  
  
 不正确的函数原型可能会导致该错误：  
  
1.  如果该函数不返回值，请使用返回类型 [void](../../cpp/void-cpp.md) 声明该函数。  
  
2.  确保该函数的所有可能分支都返回在原型中声明的类型的值。  
  
3.  内联程序集例程将返回值存储在 `AX` 寄存器中，包含该例程的 C\+\+ 函数可能需要返回语句。  请将 `AX` 中的值复制到临时变量并从函数返回该变量。  
  
 下面的示例生成 C2561：  
  
```  
// C2561.cpp  
int Test(int x) {  
   if (x) {  
      return;   // C2561  
      // try the following line instead  
      // return 1;  
   }  
   return 0;  
}  
  
int main() {  
   Test(1);  
}  
```
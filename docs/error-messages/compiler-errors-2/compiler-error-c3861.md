---
title: "编译器错误 C3861 | Microsoft Docs"
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
  - "C3861"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3861"
ms.assetid: 0a1eee30-b3db-41b1-b1e5-35949c3924d7
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3861
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”：找不到标识符  
  
 即使使用参数相关的查找，编译器也无法解析对标识符的引用。  
  
 要修复此错误，请检查标识符声明的大小写和拼写。  确保[范围解析运算符](../../cpp/scope-resolution-operator.md)和命名空间 [using directives](../../misc/using-directive-cpp.md) 的用法正确。  如果该标识符是在头文件中声明的，请确保在引用之前已包含该头文件。  此外，确保该标识符未被[条件编译指令](../../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)排除在外。  
  
## 示例  
 下面的示例生成 C3861。  
  
```  
// C3861.cpp  
void f2(){}  
int main() {  
   f();   // C3861  
   f2();   // OK  
}  
```  
  
## 示例  
 C\+\+ 标准库中的异常类现在位于 `std` 命名空间中。  
  
```  
// C3861_b.cpp  
// compile with: /EHsc  
#include <iostream>  
int main() {  
   try {  
      throw exception("Exception");   // C3861  
      // try the following line instead  
      // throw std::exception("Exception");  
   }  
   catch (...) {  
      std::cout << "caught an exception" << std::endl;  
   }  
}  
```
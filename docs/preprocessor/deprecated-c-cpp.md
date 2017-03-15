---
title: "已弃用 (C/C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc-pragma.deprecated"
  - "deprecated_CPP"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "已弃用杂注"
  - "杂注, 已弃用"
ms.assetid: 9c046f12-7875-499a-8d5d-12f8642fed2d
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 已弃用 (C/C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

利用 **deprecated** 杂注，可以指示函数、类型或任何其他标识符不再受将来版本支持，或者不应再使用它们。  
  
## 语法  
  
```  
  
#pragma deprecated( identifier1 [,identifier2, ...] )  
```  
  
## 备注  
 当编译器遇到否决的符号时，它会发出 [C4995](../error-messages/compiler-warnings/compiler-warning-level-3-c4995.md)。  
  
 可以否决宏名称。  将宏名称包含在引号内，否则宏将展开。  
  
 可利用 [deprecated](../cpp/deprecated-cpp.md) `__declspec` 修饰符为重载函数的特殊形式指定否决状态。  
  
## 示例  
  
```  
// pragma_directive_deprecated.cpp  
// compile with: /W3  
#include <stdio.h>  
void func1(void) {  
}  
  
void func2(void) {  
}  
  
int main() {  
   func1();  
   func2();  
   #pragma deprecated(func1, func2)  
   func1();   // C4995  
   func2();   // C4995  
}  
```  
  
 以下示例说明如何否决类：  
  
```  
// pragma_directive_deprecated2.cpp  
// compile with: /W3  
#pragma deprecated(X)  
class X {  // C4995  
public:  
   void f(){}  
};  
  
int main() {  
   X x;   // C4995  
}  
```  
  
## 请参阅  
 [Pragma 指令和 \_\_Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
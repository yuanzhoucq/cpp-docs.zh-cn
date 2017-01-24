---
title: "编译器错误 C2975 | Microsoft Docs"
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
  - "C2975"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2975"
ms.assetid: 526f6b9d-6c76-4c12-9252-1b1d7c1e06c7
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2975
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“arg”:“type”的模板参数无效，应为编译时常数表达式  
  
 模板参数与模板声明不匹配；尖括号内应为常数表达式。  不允许将变量用作模板实参。  检查模板定义，以找到正确的类型。  
  
 下面的示例生成 C2975：  
  
```  
// C2975.cpp  
template<int I>  
class X {};  
  
int main() {  
   int i = 4, j = 2;  
   X<i + j> x1;   // C2975  
   X<6> x2;   // OK  
}  
```  
  
 将 \_\_LINE\_\_ 作为与 [\/ZI](../../build/reference/z7-zi-zi-debug-information-format.md) 一起使用的编译时常数时，也会发生 C2975。  一种解决方法是用 [\/Zi](../../build/reference/z7-zi-zi-debug-information-format.md)（而不是 **\/ZI**）进行编译。  
  
```  
// C2975b.cpp  
// compile with: /ZI  
// processor: x86  
template<long line>   
void test(void) {}  
  
int main() {  
   test<__LINE__>();   // C2975  
}  
```
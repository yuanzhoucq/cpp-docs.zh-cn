---
title: "编译器错误 C3535 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3535"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3535"
ms.assetid: 24449c98-f681-484d-a00b-32533dca3a88
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器错误 C3535
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

无法从“type2”推导“type1”的类型  
  
 无法从初始化表达式的类型推导 `auto` 关键字所声明的变量的类型。  例如，如果初始化表达式的结果为 `void`（不是类型），则会产生此错误。  
  
### 更正此错误  
  
1.  确保初始化表达式的类型不是 `void`。  
  
2.  确保声明不是指向基本类型的指针。  有关详细信息，请参阅[基本类型](../../cpp/fundamental-types-cpp.md)。  
  
3.  如果声明是指向某个类型的指针，确保初始化表达式是指针类型。  
  
## 示例  
 下面的示例会产生 C3535，因为初始化表达式的结果为 `void`。  
  
```  
// C3535a.cpp  
// Compile with /Zc:auto  
void f(){}  
int main()  
{  
   auto x = f();   //C3535  
   return 0;  
}  
```  
  
## 示例  
 下面的示例会产生 C3535，因为该语句将变量 `x` 声明为指向推导类型的指针，但初始值设定项表达式的类型为 double。  因此，编译器无法推导该变量的类型。  
  
```  
// C3535b.cpp  
// Compile with /Zc:auto  
int main()  
{  
   auto* x = 123.0;   // C3535  
   return 0;  
}  
```  
  
## 示例  
 下面的示例会产生 C3535，因为变量 `p` 声明一个指向推导类型的指针，但初始化表达式不是指针类型。  
  
```  
// C3535c.cpp  
// Compile with /Zc:auto  
class A { };  
A x;  
auto *p = x;  // C3535  
```  
  
## 请参阅  
 [auto 关键字](../../cpp/auto-keyword.md)   
 [基本类型](../../cpp/fundamental-types-cpp.md)
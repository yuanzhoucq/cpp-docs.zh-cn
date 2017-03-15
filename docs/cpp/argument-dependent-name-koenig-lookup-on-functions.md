---
title: "针对函数的依赖于参数的名称 (Koenig) 查找 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "依赖于参数的查找 [C++]"
  - "Koenig 查找"
ms.assetid: c0928401-da2c-4658-942d-9ba4df149c35
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# 针对函数的依赖于参数的名称 (Koenig) 查找
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

编译器可以使用依赖于参数的名称查找来查找非限定函数调用的定义。  依赖于参数的名称查找也称为 Koenig 查找。  在命名空间、类、结构、联合或模板的层次结构中定义函数调用中每个参数的类型。  当指定未限定的[后缀](../cpp/postfix-expressions.md)函数调用时，编译器将在与每个参数类型关联的层次结构中搜索函数定义。  
  
## 示例  
 在此示例中，编译器注意到函数 `f()` 采用了参数 `x`。  参数 `x` 是命名空间 `A` 中定义的类型 `A::X`。  编译器搜索命名空间 `A` 并查找采用类型 `A::X` 的参数的函数 `f()` 的定义。  
  
```  
// argument_dependent_name_koenig_lookup_on_functions.cpp  
namespace A  
{  
   struct X  
   {  
   };  
   void f(const X&)  
   {  
   }  
}  
int main()  
{  
// The compiler finds A::f() in namespace A, which is where   
// the type of argument x is defined. The type of x is A::X.  
   A::X x;  
   f(x);     
}  
```  
  
## 请参阅  
 [Visual C\+\+ .NET 2003 增强的编译器一致性](../misc/visual-cpp-dotnet-2003-enhanced-compiler-conformance.md)
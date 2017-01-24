---
title: "函数模板的部分排序 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "函数模板的部分排序"
ms.assetid: 0c17347d-0e80-47ad-b5ac-046462d9dc73
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 函数模板的部分排序 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

有多个与函数调用的参数列表匹配的函数模板可用。  C\+\+ 定义了函数模板的部分排序以指定应调用的函数。  由于有一些模板可能会视为专用化程度相同，因此排序只是部分的。  
  
 编译器从可能的匹配项中选择可用的专用化程度最高的模板函数。  例如，如果一个函数模板采用类型 **T**，另一个函数模板采用 **T\***，则当参数是指针类型时，**T\*** 版本被认为更加专用化，并且优先于一般的 **T** 版本（即使这两个模板都是允许的匹配项）。  
  
 通过以下过程可确定一个函数模板候选项是否更加专用化：  
  
1.  考虑两个函数模板：T1 和 T2。  
  
2.  将 T1 中的参数替换为假想的唯一类型 X。  
  
3.  当 T1 中存在参数列表时，查看 T2 是否为该参数列表的有效模板。  忽略任何隐式转换。  
  
4.  对 T1 和 T2 执行相反的过程。  
  
5.  如果一个模板是另一个模板的有效模板参数列表，但反之不成立，则认为第一个模板的专用化程度低于第二个模板。  如果使用上一步骤的两个模板互相构成有效的参数，则它们被视为同等专用化，当尝试使用它们时，将产生不明确的调用。  
  
6.  使用以下规则：  
  
    1.  针对特定类型的模板的专用化程度高于采用泛型类型参数的模板。  
  
    2.  仅采用 **T\*** 的模板的专用化程度高于仅采用 **T** 的模板，因为假想的类型 **X\*** 是 **T** 模板参数的有效参数，但 **X** 不是 **T\*** 模板参数的有效参数。  
  
    3.  **const T** 的专用化程度高于 **T**，因为 **const X** 是 **T** 模板参数的有效参数，但 **X** 不是**const T** 模板参数的有效参数。  
  
    4.  **const T\*** 的专用化程度高于 **T\***，因为 **const X\*** 是 **T\*** 模板参数的有效参数，但 **X\*** 不是 **const T\*** 模板参数的有效参数。  
  
7.  以下示例按照以下标准中的规定在 Visual C\+\+ .NET 2003 中工作：  
  
```  
// partial_ordering_of_function_templates.cpp  
// compile with: /EHsc  
#include <iostream>  
  
extern "C" int printf(const char*,...);  
template <class T> void f(T) {  
   printf_s("Less specialized function called\n");  
}  
  
template <class T> void f(T*) {  
   printf_s("More specialized function called\n");  
}  
  
template <class T> void f(const T*) {  
   printf_s("Even more specialized function for const T*\n");  
}  
  
int main() {  
   int i =0;  
   const int j = 0;  
   int *pi = &i;  
   const int *cpi = &j;  
  
   f(i);   // Calls less specialized function.  
   f(pi);  // Calls more specialized function.  
   f(cpi); // Calls even more specialized function.  
   // Without partial ordering, these calls would be ambiguous.  
}  
```  
  
### Output  
  
```  
Less specialized function called  
More specialized function called  
Even more specialized function for const T*  
```  
  
## 请参阅  
 [函数模板](../cpp/function-templates.md)
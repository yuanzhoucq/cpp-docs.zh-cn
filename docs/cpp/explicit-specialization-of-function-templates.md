---
title: "函数模板的显式专用化 | Microsoft Docs"
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
  - "声明函数, 函数模板的专用化"
  - "函数模板的显式专用化"
  - "函数模板, 专用化"
  - "重写, 函数"
  - "函数模板的专用化"
ms.assetid: eb0fcb73-eaed-42a1-9b83-14b055a34bf8
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 函数模板的显式专用化
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

利用函数模板，您可以通过为特定类型提供函数模板的显式专用化（重写）来定义该类型的特殊行为。  例如：  
  
```  
template<> void MySwap(double a, double b);  
```  
  
 此声明使您能够为 **double** 变量定义不同函数。  与非模板函数相似，也会应用标准类型转换（如将 **float** 类型的变量提升到 **double**）。  
  
## 示例  
  
```  
// explicit_specialization.cpp  
template<class T> void f(T t)  
{  
};  
  
// Explicit specialization of f with 'char' with the  
// template argument explicitly specified:  
//  
template<> void f<char>(char c)  
{  
}  
  
// Explicit specialization of f with 'double' with the  
// template argument deduced:  
//  
template<> void f(double d)  
{  
}  
int main()  
{  
}  
```  
  
## 请参阅  
 [函数模板](../cpp/function-templates.md)
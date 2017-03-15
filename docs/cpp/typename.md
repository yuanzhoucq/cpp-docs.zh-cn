---
title: "typename | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "typename"
  - "typename_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "typename 模板说明符"
ms.assetid: 52e1d901-220d-4f0d-ab43-dae7e05fb491
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# typename
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

向编译器通知未知标识符是类型。  
  
## 语法  
  
```  
  
typename identifier;  
```  
  
## 备注  
 仅在模板定义中使用此关键字。  
  
 如果该名称是依赖于模板参数的限定名，则必须使用此关键字；如果限定名不是依赖项，则该名称是可选的。  有关详细信息，请参阅[模板和名称解析](../cpp/templates-and-name-resolution.md)。  
  
 **typename** 可由任何类型在模板声明或定义中的任何位置使用。  不允许在基类列表中使用该关键字，除非将它用作模板基类的模板参数。  
  
```  
template <class T>  
class C1 : typename T::InnerType // Error - typename not allowed.  
{};  
template <class T>  
class C2 : A<typename T::InnerType>  // typename OK.  
{};  
```  
  
 **typename** 关键字也替代模板参数列表中的 **class**。  例如，以下语句是相同的：  
  
```  
template<class T1, class T2>...  
template<typename T1, typename T2>...  
```  
  
## 示例  
  
```  
// typename.cpp  
template<class T> class X  
{  
   typename T::Y m_y;   // treat Y as a type  
};  
  
int main()  
{  
}  
```  
  
## 请参阅  
 [模板](../cpp/templates-cpp.md)   
 [C\+\+ 关键字](../cpp/keywords-cpp.md)
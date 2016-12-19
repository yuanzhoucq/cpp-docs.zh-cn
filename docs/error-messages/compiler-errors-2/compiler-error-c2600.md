---
title: "编译器错误 C2600 | Microsoft Docs"
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
  - "C2600"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2600"
ms.assetid: cce11943-ea01-4bee-a7b0-b67d24ec6493
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2600
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“函数”：不能定义编译器生成的特殊成员函数（必须首先在类中声明）  
  
 在为类定义成员函数（如构造函数或析构函数）之前，必须在类中声明它们。  如果没有在类中声明，则编译器会生成默认的构造函数和析构函数（称为特殊成员函数）。  但是，如果在类中定义这些函数中没有匹配声明的函数，则编译器将检测到冲突。  
  
 若要修复此错误，请在类声明中，声明你在类声明以外定义的每个成员函数。  
  
 以下示例生成 C2600：  
  
```  
// C2600.cpp  
// compile with: /c  
class C {};  
C::~C() {}   // C2600  
  
class D {  
   D::~D();  
};  
  
D::~D() {}  
```
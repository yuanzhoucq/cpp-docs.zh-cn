---
title: "编译器错误 C2698 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2698"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2698"
ms.assetid: 3ebfe395-c20b-4c56-9980-ca9ed8653382
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器错误 C2698
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“declaration 1”的 using 声明不能与“declaration 2”的现有 using 声明共存  
  
 一旦有了某数据成员的 [using 声明](../../cpp/using-declaration.md)，则在同一范围中，不允许有任何同名的 using declaration，因为仅可重载函数。  
  
 下面的示例生成 C2698：  
  
```  
// C2698.cpp  
struct A {  
   int x;  
};  
  
struct B {  
   int x;  
};  
  
struct C : A, B {  
   using A::x;  
   using B::x;   // C2698  
}  
```
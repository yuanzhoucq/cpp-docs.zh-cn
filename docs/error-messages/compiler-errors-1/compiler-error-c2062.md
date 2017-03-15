---
title: "编译器错误 C2062 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2062"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2062"
ms.assetid: 6cc98353-2ddf-43ab-88a2-9cc91cdd6033
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C2062
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

意外的类型“type”  
  
 编译器不需要类型名称。  
  
 下面的示例生成 C2062：  
  
```  
// C2062.cpp  
// compile with: /c  
struct A {  : int l; };   // C2062  
struct B { private: int l; };   // OK  
```  
  
 编译器处理构造函数的参数列表中未定义类型的方式也可能导致 C2062。  如果编译器遇到未定义的（拼错了吗？）类型，则它假定构造函数是一个表达式，并发出 C2062。  若要解决此错误，请只使用构造函数参数列表中的定义类型。
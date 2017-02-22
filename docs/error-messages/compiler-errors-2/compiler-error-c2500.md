---
title: "编译器错误 C2500 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2500"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2500"
ms.assetid: 6bff8161-dc9a-48ca-91f1-fd2eefdbbc93
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器错误 C2500
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier1”:“identifier2”已是直接基类  
  
 某类或结构在基类列表中多次出现。  
  
 直接基是在基列表中提到的基。  间接基是基列表中一个类的基类。  
  
 不能多次将一个类指定为直接基类。  一个类可以多次用作间接基类。  
  
 下面的示例生成 C2500：  
  
```  
// C2500.cpp  
// compile with: /c  
class A {};  
class B : public A, public A {};    // C2500  
  
// OK  
class C : public A {};  
class D : public A {};  
class E : public C, public D {};  
```
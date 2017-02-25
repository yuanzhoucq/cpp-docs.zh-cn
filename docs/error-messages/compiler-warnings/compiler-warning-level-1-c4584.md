---
title: "编译器警告（等级 1）C4584 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4584"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4584"
ms.assetid: ad86582f-cb8c-4d21-8c4c-a6c800059e25
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器警告（等级 1）C4584
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“class1”: 基类“class2”已经是“class3”的基类  
  
 定义的类从两个类继承，而这两个类彼此相互继承。  例如：  
  
```  
// C4584.cpp  
// compile with: /W1 /LD  
class A {  
};  
  
class B : public A {  
};  
  
class C : public A, public B { // C4584  
};  
```  
  
 在这种情况下，由于类 C 同时从类 A 和类 B 继承，而类 B 也从类 A 继承，因此将对类 C 发出警告。  该警告充当提醒：您必须完全限定对来自这些基类的成员的使用，否则将因所引用的类成员有多义性而生成编译器错误。
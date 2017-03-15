---
title: "编译器错误 C2701 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2701"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2701"
ms.assetid: 31cf2ab7-ced9-4f75-aa51-e169e20407fb
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器错误 C2701
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: 函数模板不能是局部类的友元  
  
 局部类不能具有作为友元函数的模板函数。  
  
 下面的示例生成 C2701：  
  
```  
// C2701.cpp  
// compile with: /c  
template<typename T>   // OK  
void f1(const T &);  
  
void MyFunction() {  
   class MyClass {  
      template<typename T> friend void f2(const T &);   // C2701  
   };  
}  
```
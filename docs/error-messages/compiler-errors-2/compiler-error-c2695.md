---
title: "编译器错误 C2695 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2695"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2695"
ms.assetid: 3f6f2091-c38b-40ea-ab6c-f1846f5702d7
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器错误 C2695
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function1”: 重写虚函数与“function2”只是在调用约定上不同  
  
 派生类中函数的签名无法重写基类中的函数，也无法更改调用约定。  
  
 下面的示例生成 C2695：  
  
```  
// C2695.cpp  
class C {  
   virtual void __fastcall func();  
};  
  
class D : public C {  
   virtual void __clrcall func();   // C2695  
};  
```
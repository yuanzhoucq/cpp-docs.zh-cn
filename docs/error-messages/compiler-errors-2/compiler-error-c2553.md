---
title: "编译器错误 C2553 | Microsoft Docs"
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
  - "C2553"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2553"
ms.assetid: 64bc1e9a-627f-4ce9-b7bc-dc911bdb9180
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2553
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“base\_function”: 重写虚函数返回类型不同于“override\_function”  
  
 派生类中的函数尝试重写基类中的虚函数，但是派生类函数的返回类型与基类函数的返回类型不同。重写函数的签名必须与正被重写的函数的签名匹配。  
  
 下面的示例生成 C2553：  
  
```  
// C2553.cpp  
// compile with: /clr /c  
ref struct C {  
   virtual void f();  
};  
  
ref struct D : C {  
   virtual int f() override ;   // C2553   
  
   // try the following line instead  
   // virtual void f() override;  
};  
```
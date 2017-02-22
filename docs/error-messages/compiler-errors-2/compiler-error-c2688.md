---
title: "编译器错误 C2688 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2688"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2688"
ms.assetid: 168c9e9d-8f65-4664-af86-db71d3e6ee46
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器错误 C2688
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“C2::fgrv”: 对 varargs 函数不支持多或虚拟继承协变返回  
  
 当函数包含变量参数时，Visual C\+\+ 不支持协变返回类型。  
  
 若要解决此错误，请定义这些函数以便它们不使用变量参数，或者使返回值对所有虚函数都一样。  
  
 下面的示例生成 C2688：  
  
```  
// C2688.cpp  
struct G1 {};  
struct G2 {};  
struct G3 : G1, G2 {};  
struct G4 {};  
struct G5 {};  
struct G6 : G4, G5 {};  
struct G7 : G3, G6 {};  
  
struct C1 {  
   virtual G4& fgrv(int,...);  
};  
  
struct C2 : C1 {  
   virtual G7& fgrv(int,...);   // C2688, does not return G4&  
};  
```
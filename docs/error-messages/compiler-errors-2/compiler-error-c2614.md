---
title: "编译器错误 C2614 | Microsoft Docs"
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
  - "C2614"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2614"
ms.assetid: a550c1d5-8718-4e17-a888-b2619e00fe11
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2614
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“class1”: 非法的成员初始化:“class2”不是基或成员  
  
 在类或结构的初始化列表中仅可出现成员或基类。  
  
## 示例  
 下面的示例生成 C2614。  
  
```  
// C2614.cpp  
// compile with: /c  
struct A {  
   int i;  
   A( int ia ) : B( i ) {};   // C2614 B is not a member of A  
};  
  
struct A2 {  
   int B;  
   int i;  
   A2( int ia ) : B( i ) {};   // OK  
};  
```
---
title: "编译器错误 C2436 | Microsoft Docs"
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
  - "C2436"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2436"
ms.assetid: ca4cc813-bc1d-4c0a-9a2c-3a5fe673d084
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2436
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”: 构造函数初始值设定项列表中的成员函数或嵌套类  
  
 无法初始化构造函数初始值设定项列表中的成员函数或局部类。  
  
 下面的示例生成 C2436：  
  
```  
// C2436.cpp  
struct S{  
   int f();  
   struct Inner{  
      int i;  
   };  
   S():f(10), Inner(0){}   // C2436  
};  
```
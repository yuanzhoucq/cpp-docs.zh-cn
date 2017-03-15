---
title: "编译器错误 C2549 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2549"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2549"
ms.assetid: 29310094-54a3-4605-bc6d-a312a68daf5d
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器错误 C2549
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

用户定义的转换不能指定返回类型  
  
 下面的示例生成 C2549：  
  
```  
// C2549.cpp  
// compile with: /c  
class X {  
public:  
   int operator int() { return value; }   // C2549  
  
   // try the following line instead  
   // operator int() { return value; }  
private:  
   int value;  
};  
```
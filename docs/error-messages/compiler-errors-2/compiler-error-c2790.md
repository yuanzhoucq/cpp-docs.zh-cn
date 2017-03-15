---
title: "编译器错误 C2790 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2790"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2790"
ms.assetid: 38d4fce1-ba00-413d-8bc1-e8aa43d7bc1f
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器错误 C2790
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“super”: 此关键字只能在类成员函数体的内部使用  
  
 如果用户曾经尝试在成员函数的上下文之外使用关键字 [super](../../cpp/super.md)，则出现此错误信息。  
  
 下面的示例生成 C2790：  
  
```  
// C2790.cpp  
void f() {  
   __super::g();   // C2790  
}  
```
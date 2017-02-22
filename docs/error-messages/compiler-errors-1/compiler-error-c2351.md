---
title: "编译器错误 C2351 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2351"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2351"
ms.assetid: 5439ccf6-66f6-4859-964c-c73f5eddfc1b
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器错误 C2351
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

过时的 C\+\+ 构造函数初始化语法  
  
 在构造函数的新样式初始化列表中，必须显式命名每个直接基类，即使它是唯一基类。  
  
 下面的示例生成 C2351：  
  
```  
// C2351.cpp  
// compile with: /c  
class B {  
public:   
   B() : () {}   // C2351  
   B() {}   // OK  
};  
```
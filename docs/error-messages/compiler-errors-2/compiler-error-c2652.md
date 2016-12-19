---
title: "编译器错误 C2652 | Microsoft Docs"
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
  - "C2652"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2652"
ms.assetid: 6e3d1a90-a989-4088-8afd-dc82f6a2d66f
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2652
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”: 非法的复制构造函数: 第一个参数不能是“identifier”  
  
 对于为其定义了复制构造函数的类、结构或联合，该复制构造函数中的第一个参数的类型与该类、结构或联合相同。  第一个参数可以是对该类型的引用，而不能是该类型本身。  
  
 下面的示例生成 C2651：  
  
```  
// C2652.cpp  
// compile with: /c  
class A {  
   A( A );   // C2652 takes an A  
};  
class B {  
   B( B& );   // OK, reference to B  
};  
```
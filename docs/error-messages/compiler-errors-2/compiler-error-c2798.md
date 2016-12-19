---
title: "编译器错误 C2798 | Microsoft Docs"
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
  - "C2798"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2798"
ms.assetid: fb0cd861-b228-4f81-8090-e28344a727e0
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2798
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“super::member”不明确  
  
 多个继承结构包含使用 [super](../../cpp/super.md) 引用的成员。  可通过下面两种方法之一修复该错误：  
  
-   从 D 的继承列表中移除 B1 或 B2。  
  
-   更改 B1 或 B2 中数据成员的名称。  
  
 下面的示例生成 C2798：  
  
```  
// C2798.cpp  
struct B1 {  
   int i;  
};  
  
struct B2 {  
   int i;  
};  
  
struct D : B1, B2 {  
   void g() {  
      __super::i = 4; // C2798  
   }  
};  
```
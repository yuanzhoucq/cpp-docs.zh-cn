---
title: "编译器错误 C2646 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2646"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2646"
ms.assetid: 92ff1f02-5eaf-40a5-8b7a-a682f149e967
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# 编译器错误 C2646
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

全局或命名空间范围的匿名结构或联合必须声明为静态  
  
 匿名结构或联合具有全局或命名空间范围，但未被声明为 `static`。  
  
 下面的示例生成 C2646，并演示如何修复此错误：  
  
```  
// C2646.cpp  
// compile with: /c  
union { int i; };   // C2646 not static  
  
// OK  
static union { int j; };  
union U { int i; };  
```
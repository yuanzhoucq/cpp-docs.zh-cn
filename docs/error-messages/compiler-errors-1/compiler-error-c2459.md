---
title: "编译器错误 C2459 | Microsoft Docs"
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
  - "C2459"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2459"
ms.assetid: 81e29f4c-5b60-40fb-9557-1cdc630d77e8
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2459
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”: 正被定义；无法作为匿名成员添加  
  
 通过匿名联合的某成员，在类、结构或联合自己的范围内重新定义了该类、结构或联合。  
  
 下面的示例生成 C2459：  
  
```  
// C2459.cpp  
// compile with: /c  
class C {  
   union { int C; };   // C2459  
   union { int D; };  
};  
```
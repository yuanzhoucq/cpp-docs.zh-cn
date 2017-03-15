---
title: "编译器警告（等级 1）C4440 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4440"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4440"
ms.assetid: 78b9642a-a93e-401e-9d92-372f6451bc5d
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器警告（等级 1）C4440
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

忽略从“calling\_convention1”到“calling\_convention2”的调用约定重定义  
  
 更改调用约定的尝试被忽略。  
  
 下面的示例生成 C4440：  
  
```  
// C4440.cpp  
// compile with: /W1 /LD /clr  
typedef void __clrcall F();  
typedef F __cdecl *PFV;   // C4440  
```
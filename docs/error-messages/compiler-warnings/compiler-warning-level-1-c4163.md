---
title: "编译器警告（等级 1）C4163 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4163"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4163"
ms.assetid: b08413fd-03fc-4f41-9167-a98976ac12f2
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4163
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”：不可用作内部函数  
  
 指定的函数不能用作 [intrinsic](../../preprocessor/intrinsic.md) 函数。 编译器将忽略无效的函数名称。  
  
 以下示例生成 C4163：  
  
```  
// C4163.cpp // compile with: /W1 /LD #include <math.h> #pragma intrinsic(mysin)   // C4163 // try the following line instead // #pragma intrinsic(sin)  
```
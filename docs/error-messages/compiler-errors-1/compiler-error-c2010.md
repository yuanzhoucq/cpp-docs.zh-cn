---
title: "编译器错误 C2010 | Microsoft Docs"
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
  - "C2010"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2010"
ms.assetid: 5795ed1d-e206-410b-b7b4-528d125c67b4
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2010
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“character”: 宏形参表中的意外  
  
 该字符在宏定义的形参表中使用不正确。  移除该字符以解决该错误。  
  
 下面的示例生成 C2010：  
  
```  
// C2010.cpp  
// compile with: /c  
#define mymacro(a|) (2*a)   // C2010  
#define mymacro(a) (2*a)   // OK  
```
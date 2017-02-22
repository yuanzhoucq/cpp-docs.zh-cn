---
title: "编译器警告（等级 1）C4616 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4616"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4616"
ms.assetid: 71e15265-c5bc-42ce-a6a9-4879892472b1
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器警告（等级 1）C4616
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\#pragma Warning : 警告编号“number”不是有效的编译器警告  
  
 不能重新分配 [警告](../../preprocessor/warning.md) 杂注中指定的警告编号。  杂注已被忽略。  
  
 下面的示例生成 C4616：  
  
```  
// C4616.cpp  
// compile with: /W1 /c  
#pragma warning( disable : 0 )   // C4616  
#pragma warning( disable : 999 )   // OK  
#pragma warning( disable : 4998 )   // OK  
```
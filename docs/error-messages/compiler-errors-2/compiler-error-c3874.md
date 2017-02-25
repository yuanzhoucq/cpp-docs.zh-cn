---
title: "编译器错误 C3874 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3874"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3874"
ms.assetid: fd55fc05-69a7-4237-b3b7-dca1d5400b4f
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器错误 C3874
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”的返回类型应为“int”而非“type”  
  
 函数没有编译器所需的返回类型。  
  
 下面的示例生成 C3874：  
  
```  
// C3874b.cpp  
double main()  
{   // C3874  
}  
```
---
title: "编译器警告（等级 1）C4087 | Microsoft Docs"
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
  - "C4087"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4087"
ms.assetid: 546e4d57-5c8e-422c-8ef1-92657336dad5
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4087
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”：用“void”参数列表声明  
  
 函数声明没有形参，而函数调用具有实参。 根据该函数的调用约定传递了额外的参数。  
  
 此警告针对 C 编译器。  
  
## 示例  
  
```  
// C4087.c // compile with: /W1 int f1( void ) { } int main() { f1( 10 );   // C4087 }  
```
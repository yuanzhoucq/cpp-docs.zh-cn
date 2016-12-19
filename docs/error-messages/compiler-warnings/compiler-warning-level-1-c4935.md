---
title: "编译器警告（等级 1）C4935 | Microsoft Docs"
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
  - "C4935"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4935"
ms.assetid: a36c56d3-571a-44dd-bb0f-bcc6b020e134
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4935
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

程序集访问说明符已从“access”修改  
  
 已修改一个类型的程序集可见性。 编译器将使用它所遇到的最后一个说明符。 例如，前向声明的程序集可见性可能与类定义的程序集可见性不同。  
  
 只能使用 **\/clr:oldSyntax** 访问 C4935。  
  
 以下示例生成 C4935：  
  
```  
// C4935.cpp // compile with: /clr:oldSyntax /W1 /c public __gc public class X {   // C4935 int i; };  
```
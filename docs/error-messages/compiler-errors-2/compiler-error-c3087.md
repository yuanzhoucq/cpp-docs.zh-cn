---
title: "编译器错误 C3087 | Microsoft Docs"
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
  - "C3087"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3087"
ms.assetid: 4f5bdd52-a853-4f02-b160-6868e9190b9d
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3087
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“named\_argument”：对“attribute”的调用已将此成员初始化  
  
 在同一值的未命名参数所在的特性快中指定了已命名参数。 仅指定一个已命名或未命名参数。  
  
## 示例  
 下面的示例生成 C3087。  
  
```  
// C3087.cpp // compile with: /c [idl_quote("quote1", text="quote2")];   // C3087 [idl_quote(text="quote3")];   // OK [idl_quote("quote4")];   // OK  
```
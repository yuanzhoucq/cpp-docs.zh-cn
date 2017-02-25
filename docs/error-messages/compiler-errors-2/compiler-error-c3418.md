---
title: "编译器错误 C3418 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3418"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3418"
ms.assetid: 54042c04-3c45-41c1-bad7-90f9ee05a21b
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# 编译器错误 C3418
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

不支持访问说明符“specifier”  
  
 不正确地指定了 CLR 访问说明符。  有关详细信息，请参阅[类型和成员可见性](../../misc/type-and-member-visibility.md)。  
  
## 示例  
 下面的示例生成 C3418。  
  
```  
// C3418.cpp // compile with: /clr /c ref struct m { internal public:   // C3418 void test(){} }; ref struct n { internal:   // OK void test(){} };  
```
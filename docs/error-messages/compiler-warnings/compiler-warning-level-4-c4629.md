---
title: "编译器警告（等级 4）C4629 | Microsoft Docs"
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
  - "C4629"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4629"
ms.assetid: 158cde12-bae5-4d43-b575-b52b35aaa0b9
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 4）C4629
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用了有向图，字符序列“digraph”解释为标记“char”（如果这不是你想要的，请在这两个字符之间插入一个空格）  
  
 在 [\/Za](../../build/reference/za-ze-disable-language-extensions.md) 下，当编译器检测到有向图时会发出警告。  
  
 以下示例生成 C4629：  
  
```  
// C4629.cpp // compile with: /Za /W4 int main() <%   // C4629 <% digraph for { }  
```
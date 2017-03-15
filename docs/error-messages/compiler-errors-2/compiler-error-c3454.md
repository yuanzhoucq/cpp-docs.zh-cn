---
title: "编译器错误 C3454 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3454"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3454"
ms.assetid: dc4e6d57-5b4d-4114-8d6f-22f9ae62925b
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器错误 C3454
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

类声明中不允许出现 \[attribute\]  
  
 必须为它定义一个类，使其成为特性。  
  
 有关更多信息，请参见[attribute](../../windows/attribute.md)。  
  
## 示例  
 下面的示例生成 C3454。  
  
```  
// C3454.cpp // compile with: /clr /c using namespace System; [attribute]   // C3454 ref class Attr1; [attribute]   // OK ref class Attr2 {};  
```
---
title: "编译器警告（等级 1）C4176 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4176"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4176"
ms.assetid: cfffb934-219a-4a63-9df6-ba54405bf766
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器警告（等级 1）C4176
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“subcomponent”: \#pragma component browser 的未知子组件  
  
 **component** 杂注包含无效子组件。 若要排除对特定名称的引用，必须在名称前使用 **references** 选项。  
  
## 示例  
  
```  
// C4176.cpp // compile with: /W1 /LD #pragma component(browser, off, i)  // C4176 #pragma component(browser, off, references, i) // ok  
```
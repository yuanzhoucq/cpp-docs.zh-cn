---
title: "编译器警告（等级 1）C4033 | Microsoft Docs"
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
  - "C4033"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4033"
ms.assetid: 189a9ec3-ff6d-49dd-b9b2-530b28bbb7c9
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4033
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”必须返回值  
  
 此函数未返回值。 返回了一个未定义的值。  
  
 必须将使用 `return` 且没有返回值的函数声明为 `void` 类型。  
  
 此错误针对 C 语言代码。  
  
 以下示例生成 C4033：  
  
```  
// C4033.c // compile with: /W1 /LD int test_1(int x)   // C4033 expected { if (x) { return;   // C4033 } }  
```
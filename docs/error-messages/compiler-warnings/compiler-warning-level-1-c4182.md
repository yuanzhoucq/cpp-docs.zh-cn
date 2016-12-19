---
title: "编译器警告（等级 1）C4182 | Microsoft Docs"
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
  - "C4182"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4182"
ms.assetid: 8970f3c6-e2dd-407e-b2ec-964360eb8b43
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4182
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\#include 嵌套深度为“number”层；可能的无限递归  
  
 由于嵌套的包含文件数量过多，编译器用尽了堆上的空间。 当包含文件包含在另一个包含文件中时，它就是嵌套的。  
  
 此消息是信息性消息，出现在错误 [C1076](../../error-messages/compiler-errors-1/fatal-error-c1076.md) 之前。
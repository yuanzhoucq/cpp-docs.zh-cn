---
title: "错误 C1077 | Microsoft Docs"
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
  - "C1077"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1077"
ms.assetid: 514d66f4-b512-479a-b793-ebf45c91e15b
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 错误 C1077
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

编译器限制：命令行选项数不得超过其限定值  
  
 命令行选项数超过了内部限制。  
  
 可能多用 [\/D](../../build/reference/d-preprocessor-definitions.md) 定义的符号太多。 （改为将定义放置在头文件中。）
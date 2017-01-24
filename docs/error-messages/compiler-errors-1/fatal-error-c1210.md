---
title: "错误 C1210 | Microsoft Docs"
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
  - "C1210"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1210"
ms.assetid: e2208309-c284-425c-a7e8-48e96e66f35b
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 错误 C1210
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

安装的运行时版本不支持 \/clr:pure 和 \/clr:safe  
  
 使用的编译器是当前版本而公共语言运行时是早期版本时将发生 C1210。  
  
 编译器的一些功能在早期的运行时版本中可能无效。  
  
 若要解决 C1210，请安装适用于你的编译器的公共语言运行时版本。
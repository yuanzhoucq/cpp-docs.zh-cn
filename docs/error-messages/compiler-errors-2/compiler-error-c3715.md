---
title: "编译器错误 C3715 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3715"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3715"
ms.assetid: ee5dce88-ddc4-4bdb-9464-47467ce1674f
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3715
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“pointer”: 必须是指向“class”的指针  
  
 您在 [\_\_hook](../../cpp/hook.md) 或 [\_\_unhook](../../cpp/unhook.md) 中指定的指针未指向有效的类。  若要修复此错误，请确保 `__hook` 和 `__unhook` 调用指定了指向有效类的指针。
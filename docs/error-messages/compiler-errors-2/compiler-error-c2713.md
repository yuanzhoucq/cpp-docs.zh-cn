---
title: "编译器错误 C2713 | Microsoft Docs"
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
  - "C2713"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2713"
ms.assetid: bae9bee3-b4b8-4be5-b6a5-02df587a7278
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2713
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

每个函数只允许一种异常处理方式  
  
 在同一函数中不能同时使用结构化异常处理 \(`__try`\/`__except`\) 和 C\+\+ 异常处理 \(`try`\/`catch`\)。
---
title: "错误 C1046 | Microsoft Docs"
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
  - "C1046"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1046"
ms.assetid: 822ec5f5-b0b0-4711-99e1-fc237b619af6
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 错误 C1046
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

编译器限制 : 结构嵌套太深  
  
 结构、联合或类超过了 15 级的嵌套限制。  重写定义以减少嵌套级。  通过使用 `typedef`  定义一个或多个嵌套结构，将结构、联合或类拆分成两个或更多的部分。
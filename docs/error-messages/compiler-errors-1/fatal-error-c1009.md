---
title: "错误 C1009 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1009"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1009"
ms.assetid: dcc8383c-3362-4c47-9c26-25d2451ebd53
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 错误 C1009
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

编译器限制 : 宏嵌套太深  
  
 编译器尝试同时扩展太多的宏。  编译器有 256 级嵌套宏限制。  将嵌套宏拆分为更简单的宏。
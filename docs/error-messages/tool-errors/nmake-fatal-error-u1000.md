---
title: "NMAKE 错误 U1000 | Microsoft Docs"
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
  - "U1000"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "U1000"
ms.assetid: 49b9bd9e-f1bc-4b55-a171-c748e40b195e
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# NMAKE 错误 U1000
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

语法错误 : 宏调用中缺少“\)”  
  
 在宏调用中出现左圆括号“**\(**”，却没有相应的右圆括号“**\)**”。  正确的格式为 **$\(***name***\)**；而单字符名称允许使用 `$`*n*。
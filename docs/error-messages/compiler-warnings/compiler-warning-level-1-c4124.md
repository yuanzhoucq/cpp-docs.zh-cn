---
title: "编译器警告（等级 1）C4124 | Microsoft Docs"
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
  - "C4124"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4124"
ms.assetid: c08c3a65-9584-47a1-a147-44f00c4b230e
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4124
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

带有堆栈检查的 \_\_fastcall 是低效的  
  
 在启用堆栈检查情况下使用 `__fastcall` 关键字。  
  
 `__fastcall` 约定生成代码较快，而堆栈检查导致代码较慢。  使用 `__fastcall` 时，请用 **check\_stack** 杂注或 \/Gs 关闭堆栈检查。  
  
 只对在这些条件下声明的第一个函数发出该警告。
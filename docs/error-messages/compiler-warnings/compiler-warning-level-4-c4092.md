---
title: "编译器警告（等级 4）C4092 | Microsoft Docs"
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
  - "C4092"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4092"
ms.assetid: 396ae826-a892-4327-bd66-f4762376d72b
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 4）C4092
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

sizeof 返回“unsigned long”  
  
 `sizeof` 运算符的操作数很大，因此 `sizeof` 返回一个无符号的 **long**。  该警告只在 Microsoft 扩展 \([\/Ze](../../build/reference/za-ze-disable-language-extensions.md)\) 下出现。  在 ANSI 兼容性 \(\/Za\) 下，则结果被截断。
---
title: "数学错误 M6202 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "M6202"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "M6202"
ms.assetid: 4d17045f-c6dc-4705-9512-e9af12c35fb4
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 数学错误 M6202
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: \_SING 错误  
  
 给定函数的参数是该函数的奇点值。  没有为此参数定义该函数。  
  
 该错误用函数名、它的参数以及错误类型调用 `_matherr` 函数。  可以重写 `_matherr` 函数，以自定义某些运行时浮点数学错误的处理方法。
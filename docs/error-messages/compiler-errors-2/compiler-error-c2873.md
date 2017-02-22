---
title: "编译器错误 C2873 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2873"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2873"
ms.assetid: 7a10036b-400e-4364-bd2f-dcd7370c5e28
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器错误 C2873
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“symbol”: 符号不能在 using 声明中使用  
  
 `using` 指令缺少 [namespace](../../misc/namespace-declaration.md) 关键字。  这导致编译器将该代码曲解为 [using 声明](../../cpp/using-declaration.md)而不是 [using 指令](../../misc/using-directive-cpp.md)。
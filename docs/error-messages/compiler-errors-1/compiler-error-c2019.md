---
title: "编译器错误 C2019 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2019"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2019"
ms.assetid: 4f37b1e1-9eca-418f-a4c3-141e8512d7b6
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器错误 C2019
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

应找到预处理器指令，却找到“character”  
  
 该字符跟在 `#` 符号的后面，但它不是预处理器指令的第一个字母。  
  
 下面的示例生成 C2019：  
  
```  
// C2019.cpp  
#!define TRUE 1   // C2019  
```  
  
 可能的解决方案：  
  
```  
// C2019b.cpp  
// compile with: /c  
#define TRUE 1  
```
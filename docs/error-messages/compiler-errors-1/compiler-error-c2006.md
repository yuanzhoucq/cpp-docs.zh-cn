---
title: "编译器错误 C2006 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2006"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2006"
ms.assetid: caaed6f7-ceb9-4742-8820-d66657c0b04d
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器错误 C2006
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“directive”应输入文件名，却找到“token”  
  
 诸如 [\#include](../../preprocessor/hash-include-directive-c-cpp.md) 或 [\#import](../../preprocessor/hash-import-directive-cpp.md) 等指令需要文件名。  若要解决该错误，请确保 *token* 是一个有效文件名。  并且将该文件名放在双引号或尖括号中。  
  
 下面的示例生成 C2006：  
  
```  
// C2006.cpp  
#include stdio.h   // C2006  
```  
  
 可能的解决方案：  
  
```  
// C2006b.cpp  
// compile with: /c  
#include <stdio.h>  
```
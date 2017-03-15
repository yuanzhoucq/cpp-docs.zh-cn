---
title: "编译器错误 C2013 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2013"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2013"
ms.assetid: 6b5c955c-53da-48ee-8533-64ef5b905173
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器错误 C2013
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

缺少“\>”  
  
 `#include` 指令缺少右尖括号。 添加右括号可解决该错误。  
  
 下面的示例生成 C2013：  
  
```  
// C2013.cpp #include <stdio.h    // C2013  
```  
  
 可能的解决方法：  
  
```  
// C2013b.cpp // compile with: /c #include <stdio.h>  
```
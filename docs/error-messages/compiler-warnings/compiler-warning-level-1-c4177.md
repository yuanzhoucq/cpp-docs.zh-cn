---
title: "编译器警告（等级 1）C4177 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4177"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4177"
ms.assetid: 2b05a5b3-696e-4f21-818e-227b9335e748
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器警告（等级 1）C4177
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\#pragma 杂注应在全局范围内使用  
  
 [pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md) 杂注不应在局部范围内使用。 只有在当前范围后遇到全局范围时，**杂注**才有效。  
  
 下面的示例生成 C4177：  
  
```  
// C4177.cpp // compile with: /W1 // #pragma bss_seg("global")   // OK int main() { #pragma bss_seg("local")    // C4177 }  
```
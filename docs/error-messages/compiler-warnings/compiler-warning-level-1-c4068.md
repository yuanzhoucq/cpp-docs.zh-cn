---
title: "编译器警告（等级 1）C4068 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4068"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4068"
ms.assetid: 96a7397a-4eab-44ab-b3bb-36747503f7e5
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4068
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

未知的杂注  
  
 编译器忽略了无法识别的[杂注](../../preprocessor/pragma-directives-and-the-pragma-keyword.md)。 请确保所使用的的编译器允许使用该**杂注**。 下面的示例生成 C4068：  
  
```  
// C4068.cpp // compile with: /W1 #pragma NotAValidPragmaName   // C4068, use valid name to resolve int main() { }  
```
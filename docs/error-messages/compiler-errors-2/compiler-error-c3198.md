---
title: "编译器错误 C3198 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3198"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3198"
ms.assetid: ec4ecf61-0067-4aa4-b443-a91013a1e59d
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器错误 C3198
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用浮点 pragma 无效: fenv\_access pragma 只在精确模式下运行  
  
 将 [fenv\_access](../../preprocessor/fenv-access.md) 杂注用在了 [\/fp](../../build/reference/fp-specify-floating-point-behavior.md) 设置而非 **\/fp:precise** 设置下。  
  
 下面的示例生成 C3198：  
  
```  
// C3198.cpp  
// compile with: /fp:fast  
#pragma fenv_access(on)   // C3198  
```
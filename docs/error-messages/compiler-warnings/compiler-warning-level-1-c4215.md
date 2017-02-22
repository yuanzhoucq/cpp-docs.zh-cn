---
title: "编译器警告（等级 1）C4215 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4215"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4215"
ms.assetid: f2aab64d-1bab-4f75-95ee-89e1263047b1
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器警告（等级 1）C4215
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用了非标准扩展 : 长浮点  
  
 默认 Microsoft 扩展 \(\/Ze\) 将 **long float** 视为 **double**。  ANSI 兼容性 \([\/Za](../../build/reference/za-ze-disable-language-extensions.md)\) 则不是这样。  请使用 **double** 以维护兼容性。  
  
 下面的示例生成 C4215：  
  
```  
// C4215.cpp  
// compile with: /W1 /LD  
long float a;   // C4215  
  
// use the line below to resolve the warning  
// double a;  
```
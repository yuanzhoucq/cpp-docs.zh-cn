---
title: "编译器错误 C2812 | Microsoft Docs"
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
  - "C2812"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2812"
ms.assetid: 22aadb8c-7232-489d-a3ad-60662dda30a8
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2812
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\/clr:pure 和 \/clr:safe 不支持 \#import  
  
 **\/clr:pure** 和 **\/clr:safe** 不支持 [\#import 指令](../../preprocessor/hash-import-directive-cpp.md)，因为 `#import` 要求使用本机编译器支持库。  
  
## 示例  
 下面的示例生成 C2812。  
  
```  
// C2812.cpp  
// compile with: /clr:pure /c  
#import "importlib.tlb"   // C2812  
```
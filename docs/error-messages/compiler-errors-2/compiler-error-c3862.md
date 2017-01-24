---
title: "编译器错误 C3862 | Microsoft Docs"
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
  - "C3862"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3862"
ms.assetid: ba547366-4189-4077-8c00-ab45e08a9533
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3862
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: 不能使用 \/clr:pure 或 \/clr:safe 编译非托管函数  
  
 使用 **\/clr:pure** 或 **\/clr:safe** 编译将只生成没有本机（非托管）代码的 MSIL 映像。因此，不能在 **\/clr:pure** 或 **\/clr:safe**  编译中使用 `unmanaged` 杂注。  
  
 有关更多信息，请参见[\/clr（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)和[managed、unmanaged](../../preprocessor/managed-unmanaged.md)。  
  
## 示例  
 下面的示例生成 C3862：  
  
```  
// C3862.cpp  
// compile with: /clr:pure /c  
#pragma unmanaged  
void f() {}   // C3862  
```
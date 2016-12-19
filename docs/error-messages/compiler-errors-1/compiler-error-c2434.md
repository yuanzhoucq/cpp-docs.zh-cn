---
title: "编译器错误 C2434 | Microsoft Docs"
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
  - "C2434"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2434"
ms.assetid: 01329e26-7c74-4219-b74f-69e3a40c9738
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2434
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“symbol”: 用 \_\_declspec\(process\) 声明的符号无法在 \/clr:pure 模式下动态初始化  
  
 per\-process 变量不能在 **\/clr:pure** 下动态初始化.  有关更多信息，请参见[\/clr（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)和[进程](../../cpp/process.md)。  
  
## 示例  
 下面的示例生成 C2434。  
  
```  
// C2434.cpp  
// compile with: /clr:pure /c  
int f() { return 0; }  
__declspec(process) int i = f();   // C2434  
__declspec(process) int i2 = 0;   // OK  
```
---
title: "编译器错误 C2441 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2441"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2441"
ms.assetid: ffbd6573-777a-48dd-892f-5cf4a758dcab
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器错误 C2441
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“variable”: 使用 \_\_declspec\(process\) 声明的符号必须是 \/clr:pure 模式中的常量  
  
 默认情况下，在 **\/clr:pure** 下依照应用程序域对变量进行处理。  如果在某个应用程序域中对 **\/clr:pure** 下标记为 `__declspec(process)` 的变量进行修改，而在另一个应用程序域中进行读取，则容易引发错误。  
  
 因此，在 **\/clr:pure** 下，编译器会将依照进程进行处理的变量强制为 `const`，使它们仅在所有应用程序域中读取。  
  
 有关更多信息，请参见[进程](../../cpp/process.md)和[\/clr（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
## 示例  
 下面的示例生成 C2441。  
  
```  
// C2441.cpp  
// compile with: /clr:pure /c  
__declspec(process) int i;   // C2441  
__declspec(process) const int j = 0;   // OK  
```
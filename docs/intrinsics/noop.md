---
title: "__noop | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__noop_cpp"
  - "__noop"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__noop 关键字 [C++]"
ms.assetid: 81ac6e97-7bf8-496b-b3c4-fd02837573e5
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# __noop
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 `__noop` 内部指定应忽略功能，并且参数列表进行分析，但代码没有为参数生成。  能在全局范围使用调试带参数数目可变的功能。  
  
 编译器将 `__noop` 内部为 0 在编译时。  
  
## 示例  
 下面的代码演示了如何使用 `__noop`。  
  
```  
// compiler_intrinsics__noop.cpp  
// compile with or without /DDEBUG  
#include <stdio.h>  
  
#if DEBUG  
   #define PRINT   printf_s  
#else  
   #define PRINT   __noop  
#endif  
  
int main() {  
   PRINT("\nhello\n");  
}  
```  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)   
 [C\+\+ 关键字](../cpp/keywords-cpp.md)
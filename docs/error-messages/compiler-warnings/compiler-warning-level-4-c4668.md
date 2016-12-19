---
title: "编译器警告（等级 4）C4668 | Microsoft Docs"
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
  - "C4668"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4668"
ms.assetid: c6585460-bc4a-4a15-9242-4cbfce53c961
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 4）C4668
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

没有将“symbol”定义为预处理器宏，用“0”替换“directives”  
  
 未定义的符号与预处理器指令一起使用。  符号将计算为假。  若要定义符号，您可以使用 [\#define directive](../../preprocessor/hash-define-directive-c-cpp.md) 或 [\/D](../../build/reference/d-preprocessor-definitions.md) 编译器选项。  
  
 默认情况下关闭此警告。  有关更多信息，请参见[默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。  
  
## 示例  
 下面的示例生成 C4668：  
  
```  
// C4668.cpp  
// compile with: /W4  
#include <stdio.h>  
  
#pragma warning (default : 4668)   // turn warning on  
  
int main()   
{  
    #if q   // C4668, q is not defined  
        printf_s("defined");  
    #else  
        printf_s("undefined");  
    #endif  
}  
```
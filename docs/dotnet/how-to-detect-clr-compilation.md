---
title: "如何：检测 /clr 编译 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/clr 编译器选项 [C++], 检测使用"
  - "编译, 检测 /clr"
ms.assetid: a9310045-4810-4637-a64a-0b31a08791c1
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：检测 /clr 编译
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用 `_MANAGED` 或 `_M_CEE` 宏查看模块是否是使用 **\/clr** 进行编译的。  有关详细信息，请参阅[\/clr（公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md)。  
  
 有关宏的更多信息，请参见 [预定义的宏](../preprocessor/predefined-macros.md)。  
  
## 示例  
  
```  
// detect_CLR_compilation.cpp  
// compile with: /clr  
#include <stdio.h>  
  
int main() {  
   #if (_MANAGED == 1) || (_M_CEE == 1)  
      printf_s("compiling with /clr\n");  
   #else  
      printf_s("compiling without /clr\n");  
   #endif  
}  
```  
  
## 请参阅  
 [使用 C\+\+ 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)
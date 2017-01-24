---
title: "编译器错误 C2457 | Microsoft Docs"
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
  - "C2457"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2457"
ms.assetid: 347e169d-23ad-434f-8836-5b09b53980ff
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2457
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“macro”: 预定义的宏不能出现在函数体的外部  
  
 尝试在全局空间中使用预定义的宏，如 [\_\_FUNCTION\_\_](../../preprocessor/predefined-macros.md)。  
  
## 示例  
 下面的示例生成 C2457：  
  
```  
// C2457.cpp  
#include <stdio.h>  
  
__FUNCTION__;   // C2457, cannot be global  
  
int main()   
{  
    printf_s("\n%s",__FUNCTION__);   // OK  
}  
```
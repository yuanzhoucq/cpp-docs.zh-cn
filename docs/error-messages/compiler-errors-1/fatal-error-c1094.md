---
title: "错误 C1094 | Microsoft Docs"
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
  - "C1094"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1094"
ms.assetid: 9e1193b2-cb95-44f9-bf6f-019e0d41dd97
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 错误 C1094
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“\-Zmval1”: 命令行选项与用于生成预编译头\(“\-Zmval2”\)的值不一致  
  
 传递给 [\/Yc](../../build/reference/yc-create-precompiled-header-file.md) 的值必须与传递给 [\/Yu](../../build/reference/yu-use-precompiled-header-file.md) 的值相同（在使用或创建相同预编译头文件的所有编译中，**\/Zm** 值都必须相同）。  
  
 下面的示例生成 C1094：  
  
```  
// C1094.h  
int func1();  
```  
  
 然后，  
  
```  
// C1094.cpp  
// compile with: /Yc"C1094.h" /Zm200  
int u;  
int main() {  
   int sd = 32;  
}  
#include "C1094.h"  
```  
  
 然后，  
  
```  
// C1094b.cpp  
// compile with: /Yu"C1094.h" /Zm300 /c  
#include "C1094.h"   // C1094 compile with /Zm200  
void Test() {}  
```
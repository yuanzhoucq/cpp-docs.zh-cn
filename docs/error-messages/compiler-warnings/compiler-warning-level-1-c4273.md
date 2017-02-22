---
title: "编译器警告（等级 1）C4273 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4273"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4273"
ms.assetid: cc18611d-9454-40a4-ad73-69823d5888fb
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器警告（等级 1）C4273
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: DLL 链接不一致  
  
 文件中的两个定义在 [DllImport](../../cpp/dllexport-dllimport.md) 的使用上不同。  
  
## 示例  
 下面的示例生成 C4273。  
  
```  
// C4273.cpp  
// compile with: /W1 /c  
char __declspec(dllimport) c;  
char c;   // C4273, delete this line or the line above to resolve  
```  
  
## 示例  
 下面的示例生成 C4273。  
  
```  
// C4273_b.cpp  
// compile with: /W1 /clr /c  
#include <stdio.h>  
extern "C" int printf_s(const char *, ...);   // C4273  
```
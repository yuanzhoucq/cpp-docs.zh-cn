---
title: "编译器错误 C3395 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3395"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3395"
ms.assetid: 26a9ebc9-ed97-47ce-b436-19aa2bcf6e50
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器错误 C3395
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: \_\_declspec\(dllexport\) 不能应用于具有 \_\_clrcall 调用约定的函数  
  
 `__declspec(dllexport)` 和 [\_\_clrcall](../../cpp/clrcall.md) 不兼容。有关详细信息，请参阅[dllexport、dllimport](../../cpp/dllexport-dllimport.md)。  
  
 下面的示例生成 C3395：  
  
```  
// C3395.cpp  
// compile with: /clr /c  
  
__declspec(dllexport) void __clrcall Test(){}   // C3395  
void __clrcall Test2(){}   // OK  
__declspec(dllexport) void Test3(){}   // OK  
```
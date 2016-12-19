---
title: "编译器错误 C2435 | Microsoft Docs"
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
  - "C2435"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2435"
ms.assetid: be6aa8f8-579b-42ea-bdd8-2d01393646ad
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2435
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“var”: 动态初始化需要托管的 CRT，不能使用 \/clr:safe 进行编译  
  
 每个应用程序的全局域变量的初始化要求使用 `/clr:pure` 编译 CRT，这不会产生可验证映像。  
  
 有关更多信息，请参见 [appdomain](../../cpp/appdomain.md) 和[process](../../cpp/process.md)。  
  
 下面的示例生成 C2435：  
  
```  
// C2435.cpp  
// compile with: /clr:safe /c  
int globalvar = 0;   // C2435  
  
__declspec(process)  
int globalvar2 = 0;  
```
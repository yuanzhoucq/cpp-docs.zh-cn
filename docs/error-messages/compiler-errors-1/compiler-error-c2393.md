---
title: "编译器错误 C2393 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2393"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2393"
ms.assetid: 4bd95728-e813-4ce8-844a-c6ebe235ca82
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# 编译器错误 C2393
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“symbol”: 不能在段“segment”中分配 per\-appdomain 符号  
  
 使用 [appdomain](../../cpp/appdomain.md) 变量意味着您正在用 **\/clr:pure** 或 **\/clr:safe** 进行编译，并且安全或纯映像不能包含数据段。  
  
 有关更多信息，请参见[\/clr（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
## 示例  
 下面的示例生成 C2393。  
  
```  
// C2393.cpp  
// compile with: /clr:pure /c  
#pragma data_seg("myseg")  
int n = 0;   // C2393  
```
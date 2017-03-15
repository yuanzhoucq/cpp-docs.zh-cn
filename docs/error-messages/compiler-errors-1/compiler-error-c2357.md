---
title: "编译器错误 C2357 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2357"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2357"
ms.assetid: d1083945-0ea2-4385-9e66-8c665978806c
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C2357
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”: 必须是“type”类型的函数  
  
 代码声明的 `atexit` 函数的版本与编译器在内部声明的版本不匹配。  按如下所示声明 `atexit`：  
  
```  
int __cdecl atexit(void (__cdecl *)());  
```  
  
 有关更多信息，请参见 [init\_seg](../../preprocessor/init-seg.md)。  
  
 下面的示例生成 C2357：  
  
```  
// C2357.cpp  
// compile with: /c  
// C2357 expected  
#pragma warning(disable : 4075)  
// Uncomment the following line to resolve.  
// int __cdecl myexit(void (__cdecl *)());  
#pragma init_seg(".mine$m",myexit)  
```
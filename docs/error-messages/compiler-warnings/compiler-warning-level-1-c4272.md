---
title: "编译器警告（等级 1）C4272 | Microsoft Docs"
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
  - "C4272"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4272"
ms.assetid: 0d6c1de4-2eef-42c4-b861-c221f8b495ef
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4272
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: 被标记为 \_\_declspec\(dllimport\)；当导入函数时，必须指定本机调用约定。  
  
 导出带 [\_\_clrcall](../../cpp/clrcall.md) 调用约定标记的函数是错误的，而且如果尝试导入标记为 `__clrcall` 的函数，编译器会发出此警告。  
  
 下面的示例生成 C4272：  
  
```  
// C4272.cpp  
// compile with: /c /W1 /clr  
__declspec(dllimport) void __clrcall Test();   // C4272  
__declspec(dllimport) void Test2();   // OK  
```
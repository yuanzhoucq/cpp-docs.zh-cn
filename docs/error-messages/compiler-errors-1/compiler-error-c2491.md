---
title: "编译器错误 C2491 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2491"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2491"
ms.assetid: 4e5a8f81-124e-402c-a5ec-d35a89b5469e
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# 编译器错误 C2491
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“标识符”：不允许使用 dllimport 函数的定义  
  
 可以将数据、静态数据成员和函数声明为 `dllimport`，但不能定义为 `dllimport`。  
  
 若要解决此问题，请从函数定义中 `__declspec(dllimport)` 删除说明符。  
  
 以下示例生成 C2491：  
  
```  
// C2491.cpp  
// compile with: /c  
// function definition  
void __declspec(dllimport) funcB() {}   // C2491  
  
// function declaration  
void __declspec(dllimport) funcB();   // OK  
```
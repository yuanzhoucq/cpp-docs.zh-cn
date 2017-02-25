---
title: "编译器警告（等级 4）C4232 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4232"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4232"
ms.assetid: f92028a5-4ddd-43c1-97f5-4f724e5e14af
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器警告（等级 4）C4232
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用了非标准扩展 :“identifier”: dllimport“dllimport”的地址是非静态，不保证标识  
  
 在 Microsoft 扩展 \(\/Ze\) 下，可以提供非静态值作为用 **dllimport** 修饰符声明的函数的地址。  在 ANSI 兼容性 \([\/Za](../../build/reference/za-ze-disable-language-extensions.md)\) 下，这将导致错误。  
  
 下面的示例生成 C4232：  
  
```  
// C4232.c  
// compile with: /W4 /Ze /c  
int __declspec(dllimport) f();  
int (*pfunc)() = &f;   // C4232  
```
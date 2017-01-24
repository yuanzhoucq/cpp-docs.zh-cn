---
title: "编译器错误 C2084 | Microsoft Docs"
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
  - "C2084"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2084"
ms.assetid: 990b107f-3721-4851-ae8b-4b69a8c149ed
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2084
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

函数“function”已有主体  
  
 函数已经定义。  
  
 在以前的 Visual C\+\+ 版本中，  
  
-   编译器将接受解析为同一实际类型的多个模板的专用化，尽管附加的定义将永远不可用。  现在编译器将检测这些多重定义。  
  
-   \_\_int32 和 int 已被视为单独的类型。  编译器现在将 \_\_int32 作为 int 的同义词处理。  这意味着，如果函数同时在 \_\_int32 和 int 上重载，编译器将检测多个定义，并提供一个错误。  
  
 下面的示例生成 C2084：  
  
```  
// C2084.cpp  
void Func(int);  
void Func(int) {}   // define function  
void Func(int) {}   // C2084 second definition  
```  
  
 可能的解决方案：  
  
```  
// C2084b.cpp  
// compile with: /c  
void Func(int);  
void Func(int) {}  
```
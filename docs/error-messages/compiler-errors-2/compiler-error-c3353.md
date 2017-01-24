---
title: "Compiler Error C3353 | Microsoft Docs"
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
  - "C3353"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3353"
ms.assetid: 5699c04b-d504-46ce-bf71-c200318fed71
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Compiler Error C3353
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“delegate”: 委托只能从全局函数或者托管或 WinRT 类型的成员函数中创建  
  
 使用 [\_\_delegate](../../misc/delegate.md) 或 [委托](../../windows/delegate-cpp-component-extensions.md) 关键字声明的委托只能在全局范围上声明。  
  
 以下示例生成 C3353：  
  
```  
// C3353.cpp  
// compile with: /clr  
delegate int f;   // C3353  
```
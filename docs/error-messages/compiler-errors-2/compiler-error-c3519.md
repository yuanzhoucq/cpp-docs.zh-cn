---
title: "编译器错误 C3519 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3519"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3519"
ms.assetid: ca24b2bc-7e90-4448-ae84-3fedddf9bca7
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器错误 C3519
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“invalid\_param”: embedded\_idl 特性的参数无效  
  
 向 [\#import](../../preprocessor/hash-import-directive-cpp.md) 的 `embedded_idl` 特性传递了一个参数，但编译器未识别该参数。  
  
 允许用于 `embedded_idl` 的仅有参数是 `emitidl` 和 `no_emitidl`。  
  
 下面的示例生成 C3519：  
  
```  
// C3519.cpp  
// compile with: /LD  
[module(name="MyLib2")];  
#import "C:\testdir\bin\importlib.tlb" embedded_idl("no_emitidcl")     
// C3519  
#import "C:\testdir\bin\importlib.tlb" embedded_idl("no_emitidl")     
// OK  
```
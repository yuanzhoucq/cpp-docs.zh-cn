---
title: "编译器警告（等级 1）C4711 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4711"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4711"
ms.assetid: 270506ab-fead-4328-b714-2978113be238
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器警告（等级 1）C4711
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

为内联展开选定了函数“function”  
  
 虽然给定函数未标记为内联，但编译器在该函数上执行了内联。  
  
 如果指定了 [\/Ob2](../../build/reference/ob-inline-function-expansion.md)，则启用 C4711。  
  
 内联由编译器自行执行。  此警告是信息式的。  
  
 默认情况下关闭此警告。  若要启用警告，请使用 [\#pragma warning](../../preprocessor/warning.md)。  有关更多信息，请参见[默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。
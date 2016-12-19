---
title: "编译器错误 C2379 | Microsoft Docs"
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
  - "C2379"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2379"
ms.assetid: 37dc3015-a4af-4341-bbf3-da6150df7e51
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2379
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提升后形参 number 具有不同的类型  
  
 通过默认提升后，指定参数的类型与以前声明中的类型不兼容。  这在 ANSI C \([\/Za](../../build/reference/za-ze-disable-language-extensions.md)\) 中是错误，而在 Microsoft 扩展 \(**\/Ze**\) 中是警告。  
  
 下面的示例生成 C2379：  
  
```  
// C2379.c  
// compile with: /Za  
void func();  
void func(char);   // C2379, char promotes to int  
```
---
title: "编译器错误 C2711 | Microsoft Docs"
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
  - "C2711"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2711"
ms.assetid: 9df9f808-7419-4e63-abdd-e6538ff0871f
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2711
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: 不能将此函数编译为托管，请考虑使用 \#pragma 非托管  
  
 有些指令将阻止编译器为封闭函数生成 MSIL。  
  
 下面的示例生成 C2711：  
  
```  
// C2711.cpp  
// compile with: /clr  
// processor: x86  
using namespace System;  
value struct V {  
   static const t = 10;  
};  
  
void bar() {  
   V::t;  
   __asm int 3   // C2711 inline asm can't be compiled managed  
}  
```
---
title: "编译器错误 C2448 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2448"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2448"
ms.assetid: e255df3c-f861-4b4d-a193-8768cef061a5
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器错误 C2448
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”: 函数样式初始值设定项类似函数定义  
  
 该函数的定义不正确。  
  
 此错误可能由旧式 C 语言格式列表引起。  
  
 下面的示例生成 C2448：  
  
```  
// C2448.cpp  
void func(c)  
   int c;  
{}   // C2448  
```
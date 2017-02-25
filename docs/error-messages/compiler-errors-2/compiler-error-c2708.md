---
title: "编译器错误 C2708 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2708"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2708"
ms.assetid: d52d3088-1141-42f4-829c-74755a7fcc3a
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器错误 C2708
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”: 实参的字节长度不同于以前的调用或引用  
  
 [\_\_stdcall](../../cpp/stdcall.md) 函数前面必须有一个原型。  否则，编译器将对该函数的第一个调用解释为原型，当编译器遇到不匹配的调用时，发生此错误。  
  
 若要修复此错误，请添加一个函数原型。
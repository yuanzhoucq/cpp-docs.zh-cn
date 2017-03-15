---
title: "Compiler Error C3550 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3550"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3550"
ms.assetid: 9f2d5ffc-e429-41a1-89e3-7acc4fd47e14
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Compiler Error C3550
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此上下文只允许纯“decltype\(auto\)”  
  
 如果 `decltype(auto)` 用作函数的返回类型的占位符，则它必须被其自身使用。  它无法用作指针声明 \(`decltype(auto*)`\)、引用声明 \(`decltype(auto&)`\) 或其他此类限定的一部分。  
  
## 请参阅  
 [auto](../../cpp/auto-cpp.md)
---
title: "编译器错误 C2174 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2174"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2174"
ms.assetid: 161d563c-76e9-47e9-9142-7812e9ea169e
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器错误 C2174
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: 实参具有类型“void”: 参数 number1，参数列表 number2  
  
 传递给参数列表 `number2` 的参数 `number1` 是 `void` 参数。  参数类型不能是 `void`。  请改用 `void*`。
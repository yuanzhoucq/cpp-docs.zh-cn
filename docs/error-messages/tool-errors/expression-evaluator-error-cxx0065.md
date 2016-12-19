---
title: "表达式计算器错误 CXX0065 | Microsoft Docs"
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
  - "CXX0065"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAN0065"
  - "CXX0065"
ms.assetid: aac68f87-0b90-4c19-afa6-1c587625a5fd
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 表达式计算器错误 CXX0065
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

变量需要堆栈帧  
  
 表达式包含的某个变量存在于当前范围内但尚未被创建。  
  
 当已单步执行函数的序言但尚未设置该函数的堆栈帧时，或者如果已单步执行该函数的退出代码时会发生该错误。  
  
 逐句通过序言码，直到在计算表达式之前设置了堆栈帧。  
  
 该错误与 CAN0065 相同。
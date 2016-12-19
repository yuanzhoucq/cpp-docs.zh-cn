---
title: "表达式计算器错误 CXX0066 | Microsoft Docs"
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
  - "CXX0066"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAN0066"
  - "CXX0066"
ms.assetid: 1321e4e1-b441-424b-9e76-c208d4a6f6ea
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 表达式计算器错误 CXX0066
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

静态成员不存在  
  
 未能找到类的静态成员或该静态成员未定义。  造成这一错误的原因会是，已经声明了静态类成员，但没有对它作定义，或仅仅在不包含调试信息的模块中定义和引用了静态类成员。  
  
 该错误与 CAN0066 相同。
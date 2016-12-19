---
title: "表达式计算器错误 CXX0052 | Microsoft Docs"
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
  - "CXX0052"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAN0052"
  - "CXX0052"
ms.assetid: 5060d479-d0a4-4682-b858-c8b9a4f324e6
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 表达式计算器错误 CXX0052
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

成员函数不存在  
  
 一个成员函数被指定为了断点，但未能找到该函数。  在已内联的函数中设置断点会导致该错误。  
  
 通过内联强行关闭 \(\/Ob0\) 重新编译文件以在该函数中设置断点。  
  
 表达式调用了未定义的函数。  
  
 该错误与 CAN0052 相同。
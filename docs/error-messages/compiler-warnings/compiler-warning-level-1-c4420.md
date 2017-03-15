---
title: "编译器警告（等级 1）C4420 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4420"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4420"
ms.assetid: 44a37754-7ddd-4764-a5f7-d33e05c20091
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器警告（等级 1）C4420
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“operator”: 运算符不可用，改用“operator”；可能会危及运行时检查的安全性  
  
 当使用 [\/RTCv](../../build/reference/rtc-run-time-error-checks.md)（向量 new\/delete 检查）且未找到任何向量形式时，生成此警告。  在这种情况下使用非向量形式。  
  
 为了使 \/RTCv 正确工作，编译器应总是调用 [new](../../cpp/new-operator-cpp.md) \/[delete](../../cpp/delete-operator-cpp.md) 的向量形式（如果使用向量语法）。
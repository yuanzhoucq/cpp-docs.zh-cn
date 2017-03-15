---
title: "编译器错误 C3180 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3180"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3180"
ms.assetid: 5281f583-7df7-418a-8507-d4da67ed6572
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器错误 C3180
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“type name”: 名称超出了“limit”个字符的元数据限制  
  
 编译器截断了元数据中托管类型的名称。  截断将使该类型无法通过 `#using` 指令（或其他语言中的等效指令）使用。  
  
 类型名称限制包含任何命名空间限定。
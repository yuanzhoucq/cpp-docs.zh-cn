---
title: "错误 C1055 | Microsoft Docs"
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
  - "C1055"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1055"
ms.assetid: a9fb9190-d7eb-4d5f-b1a2-a41e584a28c1
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 错误 C1055
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

编译器限制 : 超出键范围  
  
 源文件包含的符号太多。  编译器用完了符号表的哈希键。  
  
### 通过使用下面可能的解决方案进行修复  
  
1.  将源文件拆分成更小的文件。  
  
2.  消除不需要的头文件。  
  
3.  重用临时变量和全局变量，而不是创建新的变量。
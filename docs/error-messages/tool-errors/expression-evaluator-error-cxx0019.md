---
title: "表达式计算器错误 CXX0019 | Microsoft Docs"
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
  - "CXX0019"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAN0019"
  - "CXX0019"
ms.assetid: 4c6431fd-3310-4a61-934d-58b070b330fe
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 表达式计算器错误 CXX0019
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

错误的类型转换  
  
 C 表达式计算器无法如所写执行类型转换。  
  
 该错误与 CAN0019 相同。  
  
### 通过检查以下可能的原因进行修复  
  
1.  指定类型未知。  
  
2.  指针类型级数太多。  例如，类型转换  
  
    ```  
    (char **)h_message  
    ```  
  
     无法由 C 表达式计算器计算。
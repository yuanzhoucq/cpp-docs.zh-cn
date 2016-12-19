---
title: "错误 C1311 | Microsoft Docs"
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
  - "C1311"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1311"
ms.assetid: 6590a06c-ce9d-4f17-8f62-c809343143b8
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 错误 C1311
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

COFF 格式无法静态初始化具有 number 个字节地址的“var”  
  
 无法对类型存储少于 4 个字节的变量静态分配在编译时其值未知的地址。  
  
 此错误可能出现在原本有效的 C\+\+ 代码上。  
  
 下列示例显示了可能导致 C1311 的一种情况。  
  
```  
char c = (char)"Hello, world";   // C1311  
char *d = (char*)"Hello, world";   // OK  
```
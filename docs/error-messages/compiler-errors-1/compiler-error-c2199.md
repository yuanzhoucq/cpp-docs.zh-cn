---
title: "编译器错误 C2199 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2199"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2199"
ms.assetid: 6a92a1b7-7906-49e6-a31f-e8bffbc7706a
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器错误 C2199
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

语法错误 : 在全局范围内找到“identifier \(”\(是否为有意的声明？\)  
  
 指定的上下文导致语法错误。  可能存在不正确的声明语法。  
  
 下面的示例生成 C2199：  
  
```  
// C2199.cpp  
// compile with: /c  
int j = int(1) int(1);   // C2199  
int j = 1;   // OK  
```
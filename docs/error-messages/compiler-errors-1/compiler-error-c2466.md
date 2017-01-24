---
title: "编译器错误 C2466 | Microsoft Docs"
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
  - "C2466"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2466"
ms.assetid: 75b251d1-7d0b-4a86-afca-26adedf74486
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2466
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

不能分配常数大小为 0 的数组  
  
 分配或声明了大小为零的数组。  数组大小的常数表达式必须为大于零的整数。  具有零下标的数组声明仅对类成员、结构成员或联合成员合法，而且仅可与 Microsoft 扩展 \([\/Ze](../../build/reference/za-ze-disable-language-extensions.md)\) 一起使用。  
  
 下面的示例生成 C2466：  
  
```  
// C2466.cpp  
// compile with: /c  
int i[0];   // C2466  
int j[1];   // OK  
char *p;  
```
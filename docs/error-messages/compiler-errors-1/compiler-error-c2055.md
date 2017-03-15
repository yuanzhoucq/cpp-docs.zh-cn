---
title: "编译器错误 C2055 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2055"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2055"
ms.assetid: 6cec79cc-6bec-443f-9897-fbf5452718c7
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器错误 C2055
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

应输入形参表，而不是类型表  
  
 函数定义包含参数类型列表而不包含形参表。  ANSI C 需要命名的形参，除非它们是 void 或是省略号 \(`...`\)。  
  
 下面的示例生成 C2055：  
  
```  
// C2055.c  
// compile with: /c  
void func(int, char) {}  // C2055  
void func (int i, char c) {}   // OK  
```
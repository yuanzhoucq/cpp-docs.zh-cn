---
title: "编译器错误 C2095 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2095"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2095"
ms.assetid: 44f8ada1-974f-4e81-a408-33ac6695aa53
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器错误 C2095
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: 实参具有类型“void”:“number”参数  
  
 传递给函数的参数为 `void` 类型，这是不允许的。  请改为使用指向 void 的指针 \(`void *`\)。  
  
 `number` 指示哪一个参数为 `void`。
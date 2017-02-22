---
title: "编译器错误 C2585 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2585"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2585"
ms.assetid: 05bb1a9c-28fb-4a88-a1b5-aea85ebdee1c
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器错误 C2585
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

到“type”的显式转换不明确  
  
 该类型转换可生成多种结果。  
  
### 通过检查以下可能的原因进行修复  
  
1.  从基于多重继承的类或结构进行转换。  如果该类型多次继承同一基类，则转换函数或运算符必须使用范围解析 \(`::`\) 指定在该转换中使用哪个继承类。  
  
2.  定义了进行同一转换的转换运算符和构造函数。
---
title: "语法摘要的定义 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "预处理器"
  - "预处理器, 定义"
ms.assetid: cc752dc8-6f4e-4347-a556-e0d9ef4c46bd
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 语法摘要的定义
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

终止符是语法定义中的终结点。  不提供其他解决方法。  终止符包括保留字和用户定义的标识符的集。  
  
 非终止符是语法中的占位符。  它们中的大多数是在此语法摘要中的其他位置定义的。  定义可是递归的。  在《C\+\+ 语言参考》的[语法摘要](../misc/grammar-summary-cpp.md)中定义以下非终止符：  
  
 `constant`、*constant\-expression*、*identifier*、*keyword*、`operator`、`punctuator`  
  
 可选组件由带下标的 opt 指示。  例如，下面指示包含在大括号中的可选表达式：  
  
 **{** *expression*opt **}**  
  
## 请参阅  
 [语法摘要](../preprocessor/grammar-summary-c-cpp.md)
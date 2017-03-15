---
title: "abort 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Abort"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "abort 函数"
ms.assetid: 3352bcc4-1a8a-4e1f-8dcc-fe30f6b50f2d
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# abort 函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

同样在标准包含文件 STDLIB.H 中声明的 **abort** 函数用于终止 C\+\+ 程序。  **exit** 与 **abort** 之间的差异在于，**exit** 允许执行 C\+\+ 运行时终止处理（将调用全局对象析构函数），而 **abort** 将立即终止程序。  有关详细信息，请参阅《运行时库参考》中的 [abort](../c-runtime-library/reference/abort.md)。  
  
## 请参阅  
 [程序终止](../cpp/program-termination.md)
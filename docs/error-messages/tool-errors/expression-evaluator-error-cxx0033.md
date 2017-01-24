---
title: "表达式计算器错误 CXX0033 | Microsoft Docs"
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
  - "CXX0033"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAN0033"
  - "CXX0033"
ms.assetid: 0bd62c5b-de89-481f-9b12-88fe84805afe
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 表达式计算器错误 CXX0033
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在 OMF 类型信息中的错误  
  
 可执行文件没有用于调试的有效对象模块格式 \(OMF\)。  
  
 该错误与 CAN0033 相同。  
  
### 通过检查以下可能的原因进行修复  
  
1.  该可执行文件不是用和此版 Visual C\+\+ 一同发行的链接器创建的。  使用 LINK.exe 的当前版本重新链接对象代码。  
  
2.  .exe 文件可能已损坏。  重新编译并重新链接程序。
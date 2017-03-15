---
title: "assert 函数输出的诊断 | Microsoft Docs"
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
ms.assetid: 78b64200-520d-40da-9a61-71553f411d4f
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# assert 函数输出的诊断
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**ANSI 4.2 assert** 函数的打印诊断依据和终止行为  
  
 如果表达式为 false \(0\)，则 **assert** 函数将打印诊断信息并调用 **abort** 例程。  诊断消息具有以下形式  
  
 **Assertion failed**: *expression***, file** *filename***, line** *linenumber*  
  
 其中，filename 是源文件的名称，linenumber 是源文件中失败的断言的行号。  如果表达式为 true（非零），则不执行任何操作。  
  
## 请参阅  
 [库函数](../c-language/library-functions.md)
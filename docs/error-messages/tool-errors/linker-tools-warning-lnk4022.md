---
title: "链接器工具警告 LNK4022 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4022"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4022"
ms.assetid: 890f487e-db98-45dd-a226-c7ccead82b1e
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 链接器工具警告 LNK4022
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

无法找到符号“symbol”的唯一匹配项  
  
 LINK 或 LIB 找到了给定未修饰符号的多个匹配项，但未能解决多义性。  没有生成任何输出文件（.exe、.dll、.exp 或 .lib）。  该警告之后，每个重复符号都有一个警告 [LNK4002](../../error-messages/tool-errors/linker-tools-warning-lnk4002.md)，最后是错误 [LNK1152](../../error-messages/tool-errors/linker-tools-error-lnk1152.md)。  
  
 若要防止此警告，请指定修饰形式的符号。  在对象上运行 [Dumpbin](../../build/reference/dumpbin-options.md) 以查看修饰名。
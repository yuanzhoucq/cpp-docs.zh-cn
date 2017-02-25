---
title: "库结构 | Microsoft Docs"
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
  - "库, 结构"
ms.assetid: a5fda8e8-4a1b-4499-9095-0df935262ce4
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 库结构
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

库包含 COFF 对象。  库中的对象包含函数和数据，程序中的其他对象可从外部引用这些函数和数据。  库中的对象有时称为库成员。  
  
 通过运行带 \/LINKERMEMBER 选项的 DUMPBIN 工具，可以获得有关库内容的附加信息。  有关此选项的更多信息，请参见 [DUMPBIN 参考](../../build/reference/dumpbin-reference.md)。  
  
## 请参阅  
 [LIB 概述](../../build/reference/overview-of-lib.md)
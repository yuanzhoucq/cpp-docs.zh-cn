---
title: "重复使用内联文件 | Microsoft Docs"
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
  - "内联文件, 重用 NMAKE"
  - "NMAKE 程序, 内联文件"
  - "修订内联文件"
ms.assetid: d42dbffb-2cef-4ccb-9a1f-20b8ef81481c
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 重复使用内联文件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要重新使用内联文件，请在定义并首次使用该文件的位置指定 \<\<*filename* ，稍后再在同一命令或其他命令中重新使用不带\<\< 的*filename*。  创建内联文件的命令必须在使用该文件的所有命令运行之前运行。  
  
## 请参阅  
 [生成文件中的内联文件](../build/inline-files-in-a-makefile.md)
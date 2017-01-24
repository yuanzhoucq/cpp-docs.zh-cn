---
title: "null 宏和未定义的宏 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "宏, null 和未定义"
  - "NMAKE 程序, null 宏"
  - "NMAKE 程序, 未定义的宏"
  - "NMAKE 中的 Null 宏"
  - "未定义的宏和 NMAKE"
ms.assetid: 1db4611a-1755-4328-b00f-d35365af8b6c
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# null 宏和未定义的宏
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

空宏和未定义的宏都展开为空字符串，但定义为空字符串的宏被视为是在预处理表达式中定义的。  若要将宏定义为空字符串，请不要在命令行或命令文件中的等号 \(\=\) 后面指定除空格或制表符以外的任何字符，并将空字符串或定义引在双引号 \(" "\) 内。  若要取消定义宏，请使用 **\!UNDEF**。有关更多信息，请参见[生成文件预处理指令](../build/makefile-preprocessing-directives.md)。  
  
## 请参阅  
 [定义 NMAKE 宏](../build/defining-an-nmake-macro.md)
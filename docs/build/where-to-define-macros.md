---
title: "定义宏的位置 | Microsoft Docs"
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
  - "定义宏"
  - "宏, NMAKE"
  - "NMAKE 程序, 定义宏"
ms.assetid: 0fc59ec5-5f58-4644-b7da-7b021f7001af
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 定义宏的位置
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在命令行、命令文件、生成文件或 Tools.ini 文件中定义宏。  
  
 在生成文件或 Tools.ini 文件中，每个宏定义都必须显示在不同的行上，并且不能以空格或制表符开头。  等号两旁的空格或制表符被忽略。  所有[字符串字符](../build/defining-an-nmake-macro.md)都是文本，包括两旁的引号和嵌入的空格。  
  
 在命令行或命令文件中，空格和制表符分隔参数并且不能出现在等号两旁。  如果 `string` 有嵌入的空格或制表符，则将字符串本身或整个宏引在双引号 \(" "\) 内。  
  
## 请参阅  
 [定义 NMAKE 宏](../build/defining-an-nmake-macro.md)
---
title: "在预处理中执行程序 | Microsoft Docs"
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
  - "程序执行 [C++]"
ms.assetid: 5ecf123a-20e5-40cd-b8d8-dd5a9fdd4b24
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 在预处理中执行程序
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要在预处理期间使用命令的退出代码，请在中括号 \(\[ \]\) 内用任意参数指定命令。  任何宏都在命令执行前展开。  NMAKE 用命令的退出代码替换命令指定，此代码可用在控制预处理的表达式中。  
  
## 请参阅  
 [生成文件预处理中的表达式](../build/expressions-in-makefile-preprocessing.md)
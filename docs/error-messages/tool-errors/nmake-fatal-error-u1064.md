---
title: "NMAKE 错误 U1064 | Microsoft Docs"
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
  - "U1064"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "U1064"
ms.assetid: 7141e66e-cde6-4173-84df-a391f3ebcdd1
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# NMAKE 错误 U1064
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

未找到 MAKEFILE 并且未指定目标  
  
 NMAKE 命令行未指定生成文件或目标，并且当前目录未包含名为 MAKEFILE 的文件。  
  
 NMAKE 要求生成文件或命令行目标（或两者都要求）。  若要使生成文件可用于 NMAKE，请指定 \/F 选项或将名为 MAKEFILE 的文件放在当前目录中。  如果没有提供生成文件，NMAKE 可通过使用推理规则来创建命令行目标。
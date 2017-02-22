---
title: "伪目标 | Microsoft Docs"
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
  - "生成文件, 伪目标"
  - "NMAKE 程序, 伪目标"
  - "NMAKE 程序, 目标"
  - "伪目标和 NMAKE"
  - "时间戳, 生成文件伪目标"
ms.assetid: c8c479dc-0129-4186-8366-bc6251f2b494
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 伪目标
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

伪目标是用于替换依赖项行中的文件名的标签。  它被解释为不存在的一个文件，因此是过期的。  NMAKE 假定伪目标的时间戳在它的所有依赖项中是最新的。  如果它没有依赖项，则采用当前的时间。  如果将伪目标用作目标，则总是执行它的命令。  用作依赖项的伪目标还必须显示为其他依赖项中的目标。  但是，该依赖项不需要有命令块。  
  
 伪目标名遵循目标的文件名语法规则。  但是，如果名称没有扩展名（即不包含句点），则可以超过 8 个字符的文件名长度限制，最长可以达到 256 个字符。  
  
## 请参阅  
 [目标](../build/targets.md)
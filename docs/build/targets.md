---
title: "目标 | Microsoft Docs"
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
  - "目标, 在 NMAKE 中指定"
ms.assetid: 826ee849-4278-4c6e-97c3-79a2b5fe6463
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 目标
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在依赖项行中，使用任何有效的文件名、目录名或[伪目标](../build/pseudotargets.md)指定一个或多个目标。  用一或多个空格或制表符分隔多个目标。  目标不区分大小写。  允许在文件名中使用路径。  目标不能超过 256 个字符。  如果位于冒号之前的目标是单个字符，则使用分隔空格；否则，NMAKE 将字母与冒号的组合解释为驱动器说明符。  
  
## 您想进一步了解什么？  
 [伪目标](../build/pseudotargets.md)  
  
 [多个目标](../build/multiple-targets.md)  
  
 [累计依赖项](../build/cumulative-dependencies.md)  
  
 [多个描述块中的目标](../build/targets-in-multiple-description-blocks.md)  
  
 [依赖项副作用](../build/dependency-side-effects.md)  
  
## 请参阅  
 [描述块](../build/description-blocks.md)
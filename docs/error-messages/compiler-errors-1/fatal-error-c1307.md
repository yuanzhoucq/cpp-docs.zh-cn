---
title: "错误 C1307 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1307"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1307"
ms.assetid: 6f77d3d4-ba8a-476c-b540-aff19eb4efc4
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 错误 C1307
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

自收集配置文件数据后已编辑过程序  
  
 在使用 [\/LTCG:PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md) 时，链接器检测到在 \/LTCG:PGINSTRUMENT 之后重新编译的输入模块，而且该模块更改到了与现有配置文件数据不再相关的点。  例如，如果调用关系图在重新编译的模块中发生了更改，则编译器将生成 C1307。  
  
 若要解决此错误，请运行 \/LTCG:PGINSTRUMENT，重新执行所有测试运行，并运行 \/LTCG:PGOPTIMIZE。  如果无法运行 \/LTCG:PGINSTRUMENT 和重新执行所有测试运行，请使用 \/LTCG:PGUPDATE 代替 \/LTCG:PGOPTIMIZE 来创建优化的映像。
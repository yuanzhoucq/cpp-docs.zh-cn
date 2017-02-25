---
title: "BSCMAKE 警告 BK4504 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "BK4504"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BK4504"
ms.assetid: b56ee2d4-ad44-40f4-98c0-75934ea44a6c
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# BSCMAKE 警告 BK4504
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

文件包含的引用太多；忽略来自此源的进一步引用  
  
 .cpp 文件包含超过 64,000 符号引用。  BSCMAKE 当遇到文件中时的 64,000 引用，则忽略所有进一步引用。  
  
 更正问题，要么文件拆分为两个或更多个文件，每一个都具有小于 64,000 符号引用，或使用 `#pragma component(browser)` 预处理器指令限制为特定引用生成的符号。  有关详细信息，请参阅[组件](../../preprocessor/component.md)。
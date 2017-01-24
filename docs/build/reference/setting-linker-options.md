---
title: "设置链接器选项 | Microsoft Docs"
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
  - "文件 [C++], LINK"
  - "输入文件 [C++]"
  - "输入文件 [C++], 链接器"
  - "链接器 [C++], 开关"
  - "链接器 [C++], 设置选项的方法"
  - "对象/库模块"
ms.assetid: e08fb487-0f2e-4f24-87db-232dbc8bd2e2
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 设置链接器选项
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

可在开发环境内部或外部设置链接器选项。  每个链接器选项的主题讨论如何在开发环境中设置该选项。  有关完整的列表，请参见[链接器选项](../../build/reference/linker-options.md)。  
  
 当您在开发环境外部运行 LINK 时，可以用一种或多种方法指定输入：  
  
-   在[命令行](../../build/reference/linker-command-line-syntax.md)上  
  
-   使用[命令文件](../../build/reference/link-command-files.md)  
  
-   在[环境变量](../../build/reference/link-environment-variables.md)中  
  
 LINK 首先处理在 LINK 环境变量中指定的选项，然后按照选项在命令行上和命令文件中的指定顺序处理这些选项。  如果某个选项带有多个不同的参数，则要优先处理最后一个参数。  
  
 选项将应用于整个生成；任何选项都不能应用于某个特定输入文件。  
  
## 请参阅  
 [C\/C\+\+ 生成参考](../../build/reference/c-cpp-building-reference.md)   
 [链接器选项](../../build/reference/linker-options.md)
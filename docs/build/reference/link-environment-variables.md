---
title: "LINK 环境变量 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "link"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "环境变量 [C++], LINK"
  - "LIB 环境变量"
  - "LINK 工具 [C++], 环境变量"
  - "变量, 环境"
ms.assetid: 9a3d3291-0cc4-4a7d-9d50-80e351b90708
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# LINK 环境变量
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

LINK 工具使用以下环境变量：  
  
-   LINK 和 \_LINK\_（如已定义）。  LINK 工具预置 LINK 环境变量中定义的选项和参数并在处理之前将 \_LINK\_ 环境变量中定义的选项和参数附加到命令行。  
  
-   LIB（如已定义）。  当 LINK 工具搜索在命令行上指定的对象、库或其他文件时或通过 [\/base](../../build/reference/base-base-address.md) 选项进行搜索时会使用 LIB 路径。  它还可使用 LIB 路径查找在对象上命名的 .pdb 文件。  LIB 变量可以包含一个或多个路径规范，用分号分隔。  一个路径必须指向 Visual C\+\+ 安装的 \\lib 子目录。  
  
-   PATH，如果该工具需要运行 CVTRES 并在与 LINK 自身相同的目录中找不到文件。  （LINK 需要 CVTRES 链接 .res 文件。） PATH 必须指向 Visual C\+\+ 安装的 \\bin 子目录。  
  
-   TMP，用于链接 OMF 或.res 文件时指定目录。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)   
 [为命令行生成设置路径和环境变量](../../build/setting-the-path-and-environment-variables-for-command-line-builds.md)
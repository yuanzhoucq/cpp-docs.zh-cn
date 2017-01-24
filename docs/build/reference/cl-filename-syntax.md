---
title: "CL 文件名语法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cl.exe 编译器, 文件名语法"
  - "扩展, 指定到编译器"
  - "文件名 [C++]"
  - "文件名 [C++], CL 编译器"
  - "路径, CL 编译器文件名语法"
  - "语法, 编译器文件名"
ms.assetid: 3ca72586-75be-4477-b323-a1be232e80d4
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# CL 文件名语法
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

CL 接受具有遵循 FAT、HPFS 或 NTFS 命名约定的名称的文件。  任何文件名均可以包含完整或部分路径。  完整路径包括驱动器名和一个或多个目录名。  CL 接受由反斜杠 \(\\\) 或正斜杠 \(\/\) 分隔的文件名。  包含空格文件名必须用双引号字符引起来。  部分路径忽略 CL 假定为当前驱动器的驱动器名。  如果不指定路径，则 CL 假定该文件位于当前目录。  
  
 文件扩展名确定处理文件的方式。  已编译具有扩展名 .c、.cxx 或 .cpp 的 C 和 C\+\+ 文件。  将其他文件（包括 .obj 文件、库 \(.lib\) 和模块定义 \(.def\) 文件）传递给链接器而无需处理。  
  
## 请参阅  
 [编译器命令行语法](../../build/reference/compiler-command-line-syntax.md)
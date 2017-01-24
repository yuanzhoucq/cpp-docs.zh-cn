---
title: "生成过程中的 PCH 文件 | Microsoft Docs"
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
  - "pch"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".pch 文件, 生成进程"
  - "生成文件, 生成过程中的 PCH 文件"
  - "PCH 文件, 生成进程"
ms.assetid: ebb4b368-8a11-4009-b347-01e79af02fbc
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 生成过程中的 PCH 文件
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

软件项目的代码基础通常包含在多个 C 或 C\+\+ 源文件、对象文件、库和头文件中。  通常情况下，生成文件将这些元素的组合整理到一个可执行文件中。  下图显示了使用预编译头文件的生成文件结构。  此关系图中的 NMAKE 宏名和文件名与 [PCH 的示例生成文件](../../build/reference/sample-makefile-for-pch.md)和 [PCH 的代码示例](../../build/reference/example-code-for-pch.md)中的代码示例中的名称一致。  
  
 此图使用三个关系图设备显示生成过程的流程。  命名矩形表示每个文件或宏；三个宏表示一个或多个文件。  灰色区域表示每个编译或链接操作。  箭头指示在编译或链接过程中组合的文件和宏。  
  
 ![使用预编译头文件的生成文件](../../build/reference/media/vc30ow1.png "vc30OW1")  
使用预编译头文件的生成文件结构  
  
 从关系图顶部开始，STABLEHDRS 和 BOUNDRY 都是 NMAKE 宏，您在这些宏中列出不大可能需要重新编译的文件。  只有在预编译头文件 \(STABLE.pch\) 不存在或对两个宏中列出的文件进行更改时，才使用命令字符串  
  
```  
CL /c /W3 /Yc$(BOUNDRY) applib.cpp myapp.cpp  
```  
  
 编译这些文件。  无论在哪一种情况下，预编译头文件都将只包含来自 STABLEHDRS 宏中所列文件的代码。  在 BOUNDRY 宏中列出最后一个想预编译的文件。  
  
 在这些宏中列出的文件可以是头文件，也可以是 C 或 C\+\+ 源文件。（单个 .pch 文件不能同时用于 C 和 C\+\+ 模块。）请注意，可以使用 **hdrstop** 宏使预编译在 BOUNDRY 文件中的某个位置停止。  有关更多信息，请参见 [hdrstop](../../preprocessor/hdrstop.md)。  
  
 在关系图中继续向下，APPLIB.obj 表示在最终应用程序中使用的支持代码。  它是从 APPLIB.cpp、UNSTABLEHDRS 宏中列出的文件以及来自预编译头的预编译代码创建的。  
  
 MYAPP.obj 表示最终应用程序。  它是从 MYAPP.cpp、UNSTABLEHDRS 宏中列出的文件以及来自预编译头的预编译代码创建的。  
  
 最后，通过链接 OBJS 宏中列出的文件（APPLIB.obj 和 MYAPP.obj）创建可执行文件 \(MYAPP.EXE\)。  
  
 有关此图的进一步讨论，请参见：  
  
-   [PCH 的示例生成文件](../../build/reference/sample-makefile-for-pch.md)  
  
-   [PCH 的代码示例](../../build/reference/example-code-for-pch.md)  
  
## 请参阅  
 [在项目中使用预编译头](../../build/reference/using-precompiled-headers-in-a-project.md)
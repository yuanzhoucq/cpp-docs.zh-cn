---
title: "生成浏览信息文件：概述 | Microsoft Docs"
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
  - ".bsc 文件, 关于 .bsc 文件"
  - "浏览信息文件 (.bsc)"
  - "浏览信息文件 (.bsc), 创建"
  - "bsc 文件, 关于 bsc 文件"
ms.assetid: b5c12832-51f6-4953-8044-4264dd0fb242
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 生成浏览信息文件：概述
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

为了创建符号浏览的浏览信息，编译器为项目中的每个源文件创建一个 .sbr 文件，然后 BSCMAKE.EXE 将 .sbr 文件连接成一个 .bsc 文件中。  
  
 生成 .sbr 和 .bsc 文件需要一些时间，因此默认情况下 Visual C\+\+ 关闭这些函数。  如果要浏览当前信息，必须打开浏览选项并再次生成项目。  
  
 使用 [\/FR](../../build/reference/fr-fr-create-dot-sbr-file.md) 或 [\/FR](../../build/reference/fr-fr-create-dot-sbr-file.md) 通知编译器创建 .sbr 文件。  若要创建 .bsc 文件，可以从命令行调用 [BSCMAKE](../../build/reference/bscmake-command-line.md)。  使用来自命令行的 BSCMAKE 使您能够更精确地控制对浏览信息文件的操作。  有关更多信息，请参见 [BSCMAKE 参考](../../build/reference/bscmake-reference.md)。  
  
> [!TIP]
>  可以打开 .sbr 文件生成，而使 .bsc 文件生成处于关闭状态。  这使生成文件的速度更快，还使您能够通过打开 .bsc 文件生成并生成项目来快速创建新的 .bsc 文件。  
  
 可以通过减小 .bsc 文件的大小来减少生成 .bsc 文件所需的时间、内存和磁盘空间。  
  
 有关如何在开发环境中生成浏览器文件的信息，请参见[“常规”属性页（项目）](../../ide/general-property-page-project.md)。  
  
### 创建较小的 .bsc 文件  
  
1.  使用 [BSCMAKE 命令行选项](../../build/reference/bscmake-options.md)从浏览信息文件中排除信息。  
  
2.  在编译或汇编时省略一或多个 .sbr 文件中的本地符号。  
  
3.  如果某个对象文件不包含当前调试阶段所需的信息，则在重新生成浏览信息文件时从 BSCMAKE 命令中省略此对象文件的 .sbr 文件。  
  
### 将几个项目中的浏览信息组合到一个浏览器文件 \(.bsc\) 中  
  
1.  或者不在项目级生成 .bsc 文件，或者使用 \/n 开关防止 .sbr 文件被截断。  
  
2.  所有项目生成后，将所有 .sbr 文件作为输入来运行 BSCMAKE。  接受通配符。  例如，如果有包含 .sbr 文件的项目目录 C:\\X、C:\\Y 和 C:\\Z，并且想要将这些 .sbr 文件合并到一个 .bsc 文件中，则可以使用 BSCMAKE C:\\X\\\*.sbr C:\\Y\\\*.sbr C:\\Z\\\*.sbr \/o c:\\whatever\_directory\\combined.bsc 生成组合 .bsc 文件。  
  
## 请参阅  
 [C\/C\+\+ 生成工具](../../build/reference/c-cpp-build-tools.md)   
 [BSCMAKE 参考](../../build/reference/bscmake-reference.md)
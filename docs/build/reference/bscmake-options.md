---
title: "BSCMAKE 选项 | Microsoft Docs"
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
  - "VC.Project.VCBscMakeTool.OutputFile"
  - "VC.Project.VCBscMakeTool.SuppressStartupBanner"
  - "VC.Project.VCBscMakeTool.PreserveSBR"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/v BSCMAKE 选项"
  - "Iu BSCMAKE 选项"
  - "浏览信息文件 (.bsc), 内容"
  - "/Er BSCMAKE 选项"
  - "NOLOGO BSCMAKE 选项"
  - "/s BSCMAKE 选项"
  - "/Ei BSCMAKE 选项"
  - "/o BSCMAKE 选项"
  - "/NOLOGO BSCMAKE 选项"
  - "/Iu BSCMAKE 选项"
  - "s BSCMAKE 选项 (/s)"
  - "/Em BSCMAKE 选项"
  - "Em BSCMAKE 选项"
  - "Es BSCMAKE 选项"
  - "文件 [C++], BSCMAKE"
  - "Er BSCMAKE 选项"
  - "BSCMAKE, 用于控制文件的选项"
  - "控制 BSCMAKE 选项"
  - "El BSCMAKE 选项"
  - "/El BSCMAKE 选项"
  - "/Es BSCMAKE 选项"
  - "Ei BSCMAKE 选项"
ms.assetid: fa2f1e06-c684-41cf-80dd-6a554835ebd2
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# BSCMAKE 选项
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本节描述可用于控制 BSCMAKE 的选项。  几个选项通过排除或包含某些信息来控制浏览信息文件的内容。  排除选项可以使 BSCMAKE 的运行速度更快，并且可能使 .bsc 文件更小。  选项名区分大小写（**\/HELP** 和 **\/NOLOGO**除外）  
  
 在 Visual Studio 开发环境中仅有**\/NOLOGO** 和 **\/o**可用。有关访问项目属性页的信息，请参见[设置 Visual C\+\+ 项目属性](../../ide/working-with-project-properties.md)。  
  
 \/Ei \( `filename`...\)  
 从浏览信息文件中排除指定包含文件的内容。  若要指定多个文件，请用空格分隔名称并将列表括在圆括号内。  如果仅指定一个 `filename`，则无需使用圆括号。  使用**\/Ei**和**\/Es**选项排除不排除**\/Es**。  
  
 \/El  
 排除本地符号。  默认情况是包含本地符号。  有关本地符号的更多信息，请参见[创建 .sbr 文件](../../build/reference/creating-an-dot-sbr-file.md)。  
  
 \/Em  
 排除宏体中的符号。  使用 **\/Em**只将宏名称包含到浏览信息文件中。  默认情况是既包括宏名称也包括宏展开的结果。  
  
 \/Er \(`symbol`...\)  
 从浏览信息文件中排除指定符号。  若要指定多个符号名称，请用空格分隔名称并将列表括在圆括号内。  如果仅指定一个 `symbol`，则无需使用圆括号。  
  
 \/Es  
 从浏览信息文件中排除用绝对路径指定的每个包含文件，或在 INCLUDE 环境变量中指定的绝对路径里找到的每个包含文件。（通常，这些是系统包含文件，包含许多您在浏览信息文件中可能不需要的信息。）此选项不排除未用路径指定的文件、用相对路径指定的文件或在 INCLUDE 的相对路径中找到的文件。  可以将 **\/Ei** 选项与 **\/Es** 选项一起使用以排除 **\/Es** 不排除的文件。  如果只想排除 **\/Es** 排除的某些文件，则使用 **\/Ei** 选项而非 **\/Es** 选项，并列出要排除的文件。  
  
 \/errorreport:\[none &#124; prompt &#124; queue &#124; send\]  
 允许您向 Microsoft 发送有关 bscmake.exe 中的内部错误的信息。  
  
 有关 **\/errorreport** 的更多信息，请参见 [\/errorReport（报告内部编译器错误）](../../build/reference/errorreport-report-internal-compiler-errors.md)。  
  
 \/HELP  
 显示 BSCMAKE 命令行语法的摘要。  
  
 \/Iu  
 包括未引用符号。  默认情况下，BSCMAKE 不记录已定义但未引用的任何符号。  如果某个 .sbr 文件已压缩，由于编译器已移除未引用符号，则此选项对该输入文件无效。  
  
 \/n  
 强制非增量编译。  使用 **\/n** 强制浏览信息文件的完全生成（不管 .bsc 文件是否存在）并防止 .sbr 文件被截断。  请参见 [BSCMAKE 生成 .bsc 文件的方式](../../build/reference/how-bscmake-builds-a-dot-bsc-file.md)。  
  
 \/NOLOGO  
 取消 BSCMAKE 版权信息。  
  
 \/o `filename`  
 指定浏览信息文件的名称。  默认情况下，BSCMAKE 给浏览信息文件提供第一个 .sbr 文件的基名称和一个 .bsc 扩展名。  
  
 \/S \( `filename`...\)  
 通知 BSCMAKE 在第一次遇到指定的包含文件时处理该文件，其他情况下排除此文件。  如果某个文件（如 .c 或 .cpp 源文件的头或 .h 文件）包括在几个源文件内但每次都不被预处理指令更改，则使用此选项以节省处理时间。  如果文件的更改方式对于正在创建的浏览信息文件并不重要，则可能也要使用此选项。  若要指定多个文件，请用空格分隔名称并将列表括在圆括号内。  如果仅指定一个 `filename`，则无需使用圆括号。  如果要在文件每次被包含时排除该文件，请使用 **\/Ei** 或 **\/Es** 选项。  
  
 \/v  
 提供详细输出，其中包括正在处理的每个 .sbr 文件的名称和有关完整 BSCMAKE 运行的信息。  
  
 \/?  
 显示 BSCMAKE 命令行语法的简短摘要。  
  
 下列命令行通知 BSCMAKE 从三个 .sbr 文件执行 MAIN.bsc 的完全编译。  还通知 BSCMAKE 排除 TOOLBOX.h 的重复实例：  
  
```  
BSCMAKE /n /S toolbox.h /o main.bsc file1.sbr file2.sbr file3.sbr  
```  
  
## 请参阅  
 [BSCMAKE 参考](../../build/reference/bscmake-reference.md)
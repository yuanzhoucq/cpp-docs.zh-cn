---
title: BSCMAKE 选项 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCBscMakeTool.OutputFile
- VC.Project.VCBscMakeTool.SuppressStartupBanner
- VC.Project.VCBscMakeTool.PreserveSBR
dev_langs:
- C++
helpviewer_keywords:
- /v BSCMAKE option
- Iu BSCMAKE option
- browse information files (.bsc), content
- /Er BSCMAKE option
- NOLOGO BSCMAKE option
- /s BSCMAKE option
- /Ei BSCMAKE option
- /o BSCMAKE option
- /NOLOGO BSCMAKE option
- /Iu BSCMAKE option
- s BSCMAKE option (/s)
- /Em BSCMAKE option
- Em BSCMAKE option
- Es BSCMAKE option
- files [C++], BSCMAKE
- Er BSCMAKE option
- BSCMAKE, options for controlling files
- controlling BSCMAKE options
- El BSCMAKE option
- /El BSCMAKE option
- /Es BSCMAKE option
- Ei BSCMAKE option
ms.assetid: fa2f1e06-c684-41cf-80dd-6a554835ebd2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 16fd9bc8813179d23e83ab0a21a84ad815501bf6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="bscmake-options"></a>BSCMAKE 选项
本部分介绍可用于控制 BSCMAKE 选项。 多个选项控制通过排除或包括某些信息的浏览信息文件的内容。 排除选项可以允许 BSCMAKE 运行更快，并可能会导致较小的.bsc 文件。 选项名称不区分大小写 (除 **/帮助**和 **/NOLOGO**)。  
  
 仅 **/NOLOGO**和 **/o**可从 Visual Studio 开发环境中。  请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)有关的信息访问项目的属性页。  
  
 /Ei ( `filename`...)  
 从浏览信息文件排除指定的包含文件的内容。 若要指定多个文件，用空格分隔这些名称，并将列表括在括号中。 括号，则不需要如果只指定一个`filename`。 使用 **/Ei**连同 **/Es**选项以排除未排除的文件 **/Es**。  
  
 /El  
 排除本地符号。 默认值是包含本地符号。 有关本地符号的详细信息，请参阅[创建.sbr 文件](../../build/reference/creating-an-dot-sbr-file.md)。  
  
 /Em  
 排除宏的正文中的符号。 使用 **/Em**以在浏览信息文件中包含宏的名称。 默认值是包括宏名称和宏展开的结果。  
  
 /Er ( `symbol`...)  
 从浏览信息文件排除指定的符号。 若要指定多个符号名，请用空格分隔这些名称，并将列表括在括号中。 括号，则不需要如果只指定一个`symbol`。  
  
 /Es  
 从浏览信息文件不包括每个包含文件使用绝对路径指定或在 INCLUDE 环境变量中指定的绝对路径中找到。 (通常，这是系统包括文件，其中包含大量你可能不需要在你浏览信息文件中的信息。)此选项不排除不含路径或相对路径或文件中包括的相对路径中找到与指定的文件。 你可以使用 **/Ei**选项和 **/Es**排除的文件 **/Es**不排除。 如果你想要排除只有某些文件， **/Es**不包括，使用 **/Ei**而不是 **/Es**和列出你想要排除的文件。  
  
 /errorreport: [无&#124;提示符&#124;队列&#124;发送]  
 可以将信息发送给 Microsoft，有关 bscmake.exe 中的内部错误。  
  
 有关详细信息 **/errorreport**，请参阅[/errorReport （报告内部编译器错误）](../../build/reference/errorreport-report-internal-compiler-errors.md)。  
  
 /HELP  
 显示 BSCMAKE 命令行语法的摘要。  
  
 /Iu  
 包括未引用的符号。 默认情况下，BSCMAKE 不会记录任何已定义，但未引用的符号。 如果已打包的.sbr 文件，此选项不起该输入文件因为编译器已移除未引用的符号。  
  
 /n  
 强制非增量生成。 使用 **/n**强制完全生成浏览信息文件.bsc 文件是否存在并防止.sbr 文件被截断。 请参阅[BSCMAKE 如何生成.bsc 文件](../../build/reference/how-bscmake-builds-a-dot-bsc-file.md)。  
  
 /NOLOGO  
 禁止 BSCMAKE 版权信息。  
  
 /o `filename`  
 指定的浏览信息文件的名称。 默认情况下，BSCMAKE 为浏览信息文件的第一个的.sbr 文件和.bsc 扩展名的基名称。  
  
 /S ( `filename`...)  
 告知 BSCMAKE 来处理指定的包含文件时遇到的第一个时间并否则排除。 使用此选项以节省处理时间 （如标头，或.h、.c 或.cpp 源文件） 的文件，包含在多个源文件但因预处理指令每次更改时。 你可能还想要使用此选项，如果文件更改对你创建的浏览信息文件并不重要的方式。 若要指定多个文件，用空格分隔这些名称，并将列表括在括号中。 括号，则不需要如果只指定一个`filename`。 如果你想要排除的文件，每次包含它是，请使用 **/Ei**或 **/Es**选项。  
  
 /v  
 提供详细输出，其中包括正在处理每个.sbr 文件的名称和完整 BSCMAKE 运行有关的信息。  
  
 /?  
 显示 BSCMAKE 命令行语法的简短摘要。  
  
 下面的命令行告知 BSCMAKE 如何 MAIN.bsc 完全生成从三个.sbr 文件。 它还指示 BSCMAKE 要排除的 TOOLBOX.h 重复实例：  
  
```  
BSCMAKE /n /S toolbox.h /o main.bsc file1.sbr file2.sbr file3.sbr  
```  
  
## <a name="see-also"></a>请参阅  
 [BSCMAKE 参考](../../build/reference/bscmake-reference.md)
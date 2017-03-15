---
title: "运行 LIB | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLibrarianTool.TargetMachine"
  - "Lib"
  - "VC.Project.VCLibrarianTool.PrintProgress"
  - "VC.Project.VCLibrarianTool.SuppressStartupBanner"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/ 命令文件"
  - "/MACHINE 目标平台选项"
  - "/NOLOGO 库管理器选项"
  - "/VERBOSE 库管理器选项"
  - "冒号命令文件"
  - "命令文件"
  - "命令文件, LIB"
  - "短划线选项说明符"
  - "正斜杠 (/) 选项说明符"
  - "LIB [C++], 运行 LIB"
  - "MACHINE 目标平台选项"
  - "-MACHINE 目标平台选项"
  - "NOLOGO 库管理器选项"
  - "-NOLOGO 库管理器选项"
  - "分号, 命令文件"
  - "斜杠 (/)"
  - "VERBOSE 库管理器选项"
  - "-VERBOSE 库管理器选项"
ms.assetid: d54f5c81-7147-4b2c-a8db-68ce6eb1eabd
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 运行 LIB
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

可使用各种命令行选项来控制 LIB。  
  
## LIB 命令行  
 若要运行 LIB，请键入命令 `lib`，后跟用 LIB 执行的任务的选项和文件名。  LIB 也接受命令文件中的命令行输入，详见下节中的说明。  LIB 不使用环境变量。  
  
> [!NOTE]
>  如果您习惯于使用 LINK32.exe 和 LIB32.exe 工具（随 Windows NT 的 Microsoft Win32 软件开发工具包一起提供），您可能一直在使用 `link32 -lib` 命令或 `lib32` 命令来管理库及创建导入库。  请务必更改您的生成文件和批处理文件以改用 `lib` 命令。  
  
## LIB 命令文件  
 可使用下列语法在命令文件中将命令行参数传递给 LIB：  
  
```  
LIB @commandfile  
```  
  
 `commandfile` 文件是文本文件。  在 @ 符和文件名之间不允许有空格和制表符。  不存在默认扩展名；必须指定完整的文件名，包括任何扩展名。  不能使用通配符。  可使用文件名指定绝对路径或相对路径。  
  
 与在命令行上一样，在命令文件中也可以使用空格或制表符分隔参数；也可以用换行符分隔参数。  使用分号 \(;\) 标记注释。  LIB 忽略从分号到行尾的所有文本。  
  
 在命令文件中可指定所有命令行或部分命令行，并且在 LIB 命令中可使用一个以上的命令文件。  LIB 接受命令文件输入，如同它是在命令行中的那个位置指定的一样。  命令文件不能嵌套。  LIB 回显命令文件的内容（除非使用了 \/NOLOGO 选项）。  
  
## 使用 LIB 选项  
 选项由选项说明符（短划线 \(–\) 或正斜杠 \(\/\)）后跟选项的名称组成。  选项名不能缩写。  某些选项带参数，参数在冒号 \(:\) 后指定。  在选项规范内不允许有空格或制表符。  使用一个或多个空格或制表符来分隔命令行中的选项规范。  选项名及其关键字或文件名参数不区分大小写，但用作参数的标识符区分大小写。  LIB 按照命令行和命令文件中指定的顺序处理选项。  如果某个选项带多个不同的参数，则要处理的最后一个参数优先。  
  
 下列选项适用于所有的 LIB 模式：  
  
 \/ERRORREPORT \[NONE &#124; PROMPT &#124; QUEUE &#124; SEND\]  
 如果 lib.exe 在运行时失败，则可使用 \/ERRORREPORT 将有关这些内部错误的信息发送给 Microsoft。  
  
 有关 \/ERRORREPORT 的更多信息，请参见 [\/errorReport（报告内部编译器错误）](../../build/reference/errorreport-report-internal-compiler-errors.md)。  
  
 \/LTCG  
 导致使用链接时代码生成机制生成库。有关更多信息，请参见 [\/LTCG](../../build/reference/ltcg-link-time-code-generation.md)。  
  
 \/MACHINE  
 指定程序的目标平台。  通常情况下，不需要指定 \/MACHINE。  LIB 从 .obj 文件中推断出计算机类型。  但是，在某些情况下，LIB 因不能确定计算机类型而发出错误信息。  如果发生了此类错误，请指定 \/MACHINE。  在 \/EXTRACT 模式下，此模式只用于验证。  在命令行中使用 `lib /?`  来查看可用的计算机类型。  
  
 \/NOLOGO  
 取消显示 LIB 版权信息和版本号，并防止回显命令文件。  
  
 \/VERBOSE  
 显示有关会话进度的详细信息，其中包括所添加的 .obj 文件的名称。  该信息发送到标准输出，并可重定向到文件。  
  
 \/WX\[:NO\]  
 将警告视为错误。  有关更多信息，请参见[\/WX（将链接器警告视为错误）](../../build/reference/wx-treat-linker-warnings-as-errors.md)。  
  
 其他选项只适用于特定的 LIB 模式。  在描述每种模式的节中对这些选项进行了讨论。  
  
## 请参阅  
 [LIB 引用](../../build/reference/lib-reference.md)
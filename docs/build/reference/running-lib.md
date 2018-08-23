---
title: 运行 LIB |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLibrarianTool.TargetMachine
- Lib
- VC.Project.VCLibrarianTool.PrintProgress
- VC.Project.VCLibrarianTool.SuppressStartupBanner
dev_langs:
- C++
helpviewer_keywords:
- -MACHINE target platform option
- command files, LIB
- MACHINE target platform option
- colon command files
- VERBOSE library manager option
- /NOLOGO library manager option
- dash option specifier
- /MACHINE target platform option
- forward slash option specifier
- -NOLOGO library manager option
- LIB [C++], running LIB
- -VERBOSE library manager option
- /VERBOSE library manager option
- command files
- NOLOGO library manager option
- slash (/)
- semicolon, command files
- / command files
ms.assetid: d54f5c81-7147-4b2c-a8db-68ce6eb1eabd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c306ba58bfef11f92d7e861272aad2aa605c8fde
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32377569"
---
# <a name="running-lib"></a>运行 LIB
来控制 LIB，可以使用各种命令行选项。  
  
## <a name="lib-command-line"></a>LIB 命令行  
 若要运行 LIB，键入命令`lib`跟选项和任务的文件名称使用 LIB 执行。 LIB 还接受以下部分所述的命令文件中的命令行输入。 LIB 不使用环境变量。  
  
> [!NOTE]
>  如果您习惯于 LINK32.exe 和 LIB32.exe 工具提供与 Microsoft Win32 软件开发工具包的 Windows NT 中，您可能一直使用这两个命令`link32 -lib`或命令`lib32`管理库和创建导入库。 请务必更改你的生成文件和批处理文件使用`lib`命令。  
  
## <a name="lib-command-files"></a>LIB 命令文件  
 可以将命令行自变量传递到命令文件使用以下语法中的 LIB:  
  
```  
LIB @commandfile  
```  
  
 文件`commandfile`是一个文本文件。 之间允许有空格或制表符 at 符号 (@) 和文件名称。 不存在默认扩展;必须指定完整的文件名，包括任何扩展。 不能使用通配符。 你可以使用的文件名称指定的绝对或相对路径。  
  
 在命令文件中，自变量可以由空格或分隔选项卡上，因为它们可以在命令行中;它们还可以由换行符分隔。 使用分号 （;） 来标记注释。 LIB 忽略从分号到行的末尾的所有文本。  
  
 你可以在命令文件中，指定所有或命令行的一部分，并且可以使用多个 LIB 命令中的命令文件。 LIB 接受命令文件输入，如同它在命令行上的位置中指定。 不能嵌套命令文件。 LIB 回显命令文件的内容，除非使用 /NOLOGO 选项。  
  
## <a name="using-lib-options"></a>使用 LIB 选项  
 选项包括选项说明符，它是短划线 （-） 或正斜杠 （/） 后, 跟选项的名称。 选项名不能缩写。 某些选项带自变量，冒号 （:） 后指定。 中的选项规范所允许空格或制表符。 使用一个或多个空格或制表符分隔命令行上的选项规范。 选项名称，而其关键字或文件的名称自变量不区分大小写，但使用作为自变量标识符都是区分大小写。 LIB 处理在命令行上指定的顺序和命令文件中的选项。 一个选项重复使用不同的自变量，如果要处理的最后一个优先。  
  
 下列选项适用于所有的 LIB 模式：  
  
 /ERRORREPORT [NONE&AMP;#124;提示&AMP;#124;队列&AMP;#124;发送]  
 如果 lib.exe 在运行时失败，你可以使用 /ERRORREPORT 信息向 Microsoft 发送有关这些内部错误。  
  
 /ERRORREPORT 有关的详细信息，请参阅[/errorReport （报告内部编译器错误）](../../build/reference/errorreport-report-internal-compiler-errors.md)。  
  
 /clr  
 导致要生成使用的链接时代码生成的库。  有关详细信息，请参阅[/LTCG](../../build/reference/ltcg-link-time-code-generation.md)。  
  
 /MACHINE  
 指定程序的目标平台。 通常情况下，你不必指定 /MACHINE。 LIB 机从推断类型的.obj 文件。 但是，在某些情况下，LIB 无法确定计算机类型并发出错误消息。 如果发生此类错误，则指定 /MACHINE。 在 /extract، 模式下，此选项适用于仅验证。 使用`lib /?`在命令行来查看可用的计算机类型。  
  
 /NOLOGO  
 取消显示 LIB 版权消息和版本，并防止回显的命令文件。  
  
 /VERBOSE  
 显示有关会话，包括所添加的.obj 文件的名称的进度的详细信息。 信息被发送到标准输出，并可重定向到文件。  
  
 /WX [: NO]  
 将警告视为错误。 请参阅[/WX （将链接器警告视为错误）](../../build/reference/wx-treat-linker-warnings-as-errors.md)有关详细信息。  
  
 其他选项仅适用于特定的 LIB 模式。 描述每种模式节中讨论了这些选项。  
  
## <a name="see-also"></a>请参阅  
 [LIB 引用](../../build/reference/lib-reference.md)
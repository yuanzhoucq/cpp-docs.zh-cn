---
title: 生成文件预处理指令
ms.date: 06/14/2018
f1_keywords:
- '!UNDEF'
- '!INCLUDE'
- '!IFNDEF'
- '!MESSAGE'
helpviewer_keywords:
- ERROR directive
- '!MESSAGE directive'
- IF directive
- '!UNDEF directive'
- IFDEF directive
- '!ELSEIF directive'
- '!IFDEF directive'
- '!IF directive'
- UNDEF directive
- '!CMDSWITCHES directive'
- ENDIF directive
- directives, makefile preprocessing
- INCLUDE directive
- IFNDEF directive
- preprocessing directives, makefiles
- '!IFNDEF directive'
- ELSEIFNDEF directive
- NMAKE program, expressions
- ELSEIF directive
- '!ERROR directive'
- '!ENDIF directive'
- MESSAGE directive
- '!INCLUDE directive'
- '!ELSEIFNDEF directive'
- CMDSWITCHES directive
- '!ELSEIFDEF directive'
- '!ELSE directive'
- NMAKE program, preprocessor directives
- makefiles, preprocessing directives
- ELSE directive
- ELSEIFDEF directive
ms.assetid: bcedeccb-d981-469d-b9e8-ab5d097fd8c2
ms.openlocfilehash: 0945d0e1c149b7e1ab31b0dbbd5003f8b15a1e4d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62321550"
---
# <a name="makefile-preprocessing-directives"></a>生成文件预处理指令

预处理指令不区分大小写。 初始惊叹号 （！） 必须位于一行的开头。 零个或多个空格或选项卡可以显示感叹号的缩进的后面。

- **!CMDSWITCHES** {**+** &#124; **-**}*option* ...

   将每个*选项*列出打开或关闭。 空格或制表符必须在其之前显示 + 或-运算符;无运算符之间会出现并[选项字母](nmake-options.md)。 字母不区分大小写，不含斜杠 （/） 指定。 若要打开上的某些选项而关闭，另外一些使用 **！CMDSWITCHES**。

   仅 /D，/ 生成文件中可以使用我、 /N 和 /S。 Tools.ini 中的所有选项都允许除 /F、 /HELP、 /NOLOGO，/，X 和 /？。 描述块中指定的更改直到下一步的描述块不会生效。 此指令更新**MAKEFLAGS**; 如果更改在递归期间继承**MAKEFLAGS**指定。

- **!ERROR**  *text*

   显示*文本*错误 U1050，然后中止程序 NMAKE，即使 /K，/ I， **。忽略**， **！CMDSWITCHES**，或使用短划线 （-） 命令修饰符。 包含空格或选项卡之前*文本*将被忽略。

- **!MESSAGE**  *text*

   显示*文本*到标准输出。 包含空格或选项卡之前*文本*将被忽略。

- **!INCLUDE** [ **\<** ] *filename* [ **>** ]

   读取*文件名*作为生成文件，然后继续执行当前生成文件。 NMAKE 中搜索*文件名*首先在指定或当前目录中，然后以递归方式通过目录的任何父生成文件，然后，如果*filename*都括在尖括号 (\<>)，指定目录中**INCLUDE**宏，最初设置为 INCLUDE 环境变量。 对于将 **。后缀**设置， **。宝贵**，和推理规则来递归生成文件。

- **!IF** *constant_expression*

   如果前面的 **！如果**和下一页 **！其他**或 **！ENDIF**如果*constant_expression*计算结果为非零值。

- **!IFDEF**  *macroname*

   如果前面的 **！IFDEF**和下一页 **！其他**或 **！ENDIF**如果*macroname*定义。 Null 宏被视为已定义。

- **!IFNDEF**  *macroname*

   如果前面的 **！IFNDEF**和下一页 **！其他**或 **！ENDIF**如果*macroname*未定义。

- **!ELSE** [**IF** *constant_expression* &#124; **IFDEF** *macroname* &#124; **IFNDEF** *macroname*]

   如果前面的 **！其他**和下一页 **！ENDIF**如果之前的 **！如果**， **！IFDEF**，或 **！IFNDEF**语句的计算结果为零。 可选关键字提供了进一步的预处理的控件。

- **!ELSEIF**

   同义词 **！ELSE IF**。

- **!ELSEIFDEF**

   同义词 **！其他 IFDEF**。

- **!ELSEIFNDEF**

   同义词 **！其他 IFNDEF**。

- **!ENDIF**

   标记的末尾 **！如果**， **！IFDEF**，或 **！IFNDEF**块。 后的任何文本 **！ENDIF**在同一行上被忽略。

- **!UNDEF**  *macroname*

   取消定义*macroname*。

## <a name="see-also"></a>请参阅

- [生成文件预处理](makefile-preprocessing.md)
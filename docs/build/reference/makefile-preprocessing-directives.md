---
title: 生成文件预处理指令
ms.date: 08/11/2019
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
ms.openlocfilehash: 4825ca180cb1b419a9ffa5232575ba1a24f8805d
ms.sourcegitcommit: db1ed91fa7451ade91c3fb76bc7a2b857f8a5eef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/13/2019
ms.locfileid: "68980515"
---
# <a name="makefile-preprocessing-directives"></a>生成文件预处理指令

预处理指令不区分大小写。 初始惊叹号 (!) 必须出现在行的开头。 在感叹号后, 对于缩进, 零个或多个空格或制表符可以出现。

- `!CMDSWITCHES`{`+` &#124; } 选项 ... `-`

   打开或关闭每个*选项*。 空格或制表符必须出现在`+` or `-`运算符之前; 运算符和[选项字母](running-nmake.md#nmake-options)之间不能出现空格或制表符。 字母不区分大小写, 并且不以斜杠 (`/`) 指定。 若要打开某些选项并关闭其他选项, 请使用的`!CMDSWITCHES`单独规范。

   只能在生成文件中使用/D、/I、/N 和/S。 在 schema.ini 中, 除/F、/HELP、/NOLOGO、/X 和/？之外的所有选项都是允许的。 在说明块中指定的更改在下一个描述块之前不会生效。 此指令更新**MAKEFLAGS**;如果指定了**MAKEFLAGS** , 则在递归期间会继承更改。

- `!ERROR`*文本*

   显示错误 U1050 中的*文本*, 然后停止 NMAKE, 即使使用的是/k `.IGNORE`、 `!CMDSWITCHES`/i、、或短`-`划线 () 命令修饰符。 忽略*文本*之前的空格或制表符。

- `!MESSAGE`*文本*

   将*文本*显示到标准输出。 忽略*文本*之前的空格或制表符。

- `!INCLUDE`[ `<` ]*文件名*[ `>` ]

   将*filename*作为生成文件读取, 然后继续当前的生成文件。 NMAKE 首先在指定的目录或当前目录中搜索*文件名*, 然后以递归方式在任何父生成文件的目录中进行搜索, 然后, 如果`< >` *filename*由尖括号 () 括起来, 则在指定**的目录中INCLUDE**宏, 最初设置为 INCLUDE 环境变量。 向递归生成`.SUFFIXES`的传递`.PRECIOUS`设置、和推理规则非常有用。

- `!IF`*constant_expression*

   在和下`!IF`一个`!ELSE` or `!ENDIF`之间处理语句, 如果*constant_expression*的计算结果为非零值。

- `!IFDEF`*macroname*

   在定义了`!IFDEF`和下一个`!ELSE`之间`!ENDIF`或如果定义了*macroname* 。 空宏被视为已定义。

- `!IFNDEF`*macroname*

   `!IFNDEF`在和`!ELSE` 下一个之间处理语句,如果未定义macroname,则`!ENDIF`为。

- `!ELSE`[`IF` &#124; *constant_expression* &#124; *macroname* macroname] `IFDEF` `IFNDEF`

   `!ELSE`如果上一个、`!IFDEF`或`!ENDIF` 语句`!IFNDEF`的计算结果为零, 则在和下一个语句之间进行处理。 `!IF` 可选关键字可进一步控制预处理。

- `!ELSEIF`

   `!ELSE IF` 的同义词。

- `!ELSEIFDEF`

   `!ELSE IFDEF` 的同义词。

- `!ELSEIFNDEF`

   `!ELSE IFNDEF` 的同义词。

- `!ENDIF`

   标记`!IF`、 `!IFDEF`或块的结尾。`!IFNDEF` 位于同一行`!ENDIF`后面的任何文本都将被忽略。

- `!UNDEF`*macroname*

   取消*macroname*。

## <a name="see-also"></a>请参阅

- [生成文件预处理](makefile-preprocessing.md)
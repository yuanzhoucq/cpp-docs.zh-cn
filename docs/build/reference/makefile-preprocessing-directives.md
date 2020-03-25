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
ms.openlocfilehash: 1dd30c8e338343626d8a8cc3157d118e44f0ea18
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170483"
---
# <a name="makefile-preprocessing-directives"></a>生成文件预处理指令

预处理指令不区分大小写。 初始惊叹号（！）必须出现在行的开头。 在感叹号后，对于缩进，零个或多个空格或制表符可以出现。

- `!CMDSWITCHES` {`+` &#124; `-`}*选项*。

   打开或关闭每个*选项*。 空格或制表符必须出现在 `+` 或 `-` 运算符之前;运算符和[选项字母](running-nmake.md#nmake-options)之间不能出现 "无"。 字母不区分大小写，但未指定斜线（`/`）。 若要打开某些选项并关闭其他选项，请使用 `!CMDSWITCHES`的单独规范。

   只能在生成文件中使用/D、/I、/N 和/S。 在 schema.ini 中，除/F、/HELP、/NOLOGO、/X 和/？之外的所有选项都是允许的。 在说明块中指定的更改在下一个描述块之前不会生效。 此指令更新**MAKEFLAGS**;如果指定了**MAKEFLAGS** ，则在递归期间会继承更改。

- `!ERROR`*文本*

   显示错误 U1050 中的*文本*，然后暂停 NMAKE，即使使用/K、/i、`.IGNORE`、`!CMDSWITCHES`或短划线（`-`）命令修饰符也是如此。 忽略*文本*之前的空格或制表符。

- `!MESSAGE`*文本*

   将*文本*显示到标准输出。 忽略*文本*之前的空格或制表符。

- `!INCLUDE` [`<`]*文件名*[`>`]

   将*filename*作为生成文件读取，然后继续当前的生成文件。 NMAKE 首先在指定的目录或当前目录中搜索*文件名*，然后以递归方式在任何父生成文件的目录中进行搜索，然后，如果*filename*由尖括号（`< >`）括起来，则在由**include**宏指定的目录中，该宏最初设置为 INCLUDE 环境变量。 向递归生成的传递 `.SUFFIXES` 设置、`.PRECIOUS`和推理规则非常有用。

- `!IF` *constant_expression*

   如果*constant_expression*的计算结果为非零值，则将在 `!IF` 和下一个 `!ELSE` 或 `!ENDIF` 之间处理语句。

- `!IFDEF` *macroname*

   如果定义了*macroname* ，则将在 `!IFDEF` 和下一个 `!ELSE` 或 `!ENDIF` 之间处理语句。 空宏被视为已定义。

- `!IFNDEF` *macroname*

   如果未定义*macroname* ，则在 `!IFNDEF` 和下一个 `!ELSE` 或 `!ENDIF` 之间处理语句。

- `!ELSE` [`IF` *constant_expression* &#124; `IFDEF` *macroname* &#124; `IFNDEF` *macroname*]

   如果之前的 `!IF`、`!IFDEF`或 `!IFNDEF` 语句的计算结果为零，则在 `!ELSE` 和下一 `!ENDIF` 之间处理语句。 可选关键字可进一步控制预处理。

- `!ELSEIF`

   `!ELSE IF` 的同义词。

- `!ELSEIFDEF`

   `!ELSE IFDEF` 的同义词。

- `!ELSEIFNDEF`

   `!ELSE IFNDEF` 的同义词。

- `!ENDIF`

   标记 `!IF`、`!IFDEF`或 `!IFNDEF` 块的结尾。 同一行 `!ENDIF` 后面的任何文本都将被忽略。

- `!UNDEF` *macroname*

   取消*macroname*。

## <a name="see-also"></a>另请参阅

- [生成文件预处理](makefile-preprocessing.md)

---
title: "生成文件预处理指令 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- '!UNDEF'
- '!INCLUDE'
- '!IFNDEF'
- '!MESSAGE'
dev_langs: C++
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
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1bc73a86b0772b13731aaf7ac4e2ef0760caa8a5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="makefile-preprocessing-directives"></a>生成文件预处理指令
预处理指令不区分大小写。 初始感叹号 （！） 必须出现在行开头。 零个或多个空格或选项卡可以显示感叹号来缩进的后面。  
  
 **!CMDSWITCHES**  
 {**+**&#124; **-** }*选项*...将每个*选项*列出打开或关闭。 空格或制表符必须之前出现 + 或-运算符;无运算符之间可能会出现与[选项字母](../build/nmake-options.md)。 字母不区分大小写，并且不用反斜杠 （/） 指定。 若要打开上的某些选项而关闭，另外一些选项使用的**！CMDSWITCHES**。  
  
 仅 /D，/ I、 /N 和 /S 都可以在生成文件中使用。 Tools.ini，在所有选项都允许 /F、 /HELP、 /NOLOGO，除/X，和 /？。 描述块中指定的更改直到下一步的描述块不会生效。 此指令更新**MAKEFLAGS**; 如果更改期间递归继承**MAKEFLAGS**指定。  
  
 **!错误***文本*   
 显示*文本*错误 U1050，然后暂停 NMAKE，即使 /K，/ I， **。忽略**， **！CMDSWITCHES**，或使用短划线 （-） 命令修饰符。 包含空格或制表符之前*文本*将被忽略。  
  
 **!消息***文本*   
 显示*文本*到标准输出。 包含空格或制表符之前*文本*将被忽略。  
  
 **!包括**[  **\<** ] *filename*[  **>** ]  
 读取*filename*作为生成文件，然后继续执行当前生成文件。 NMAKE 中搜索*filename*首先在指定或当前目录中，然后以递归方式通过目录的任何父生成文件，然后，如果*filename*用尖括号括 (\<>)，指定目录中**包括**宏，最初设置为 INCLUDE 环境变量。 对于将**。后缀**设置， **。宝贵**，和为递归生成文件的推理规则。  
  
 **!如果**  `constantexpression`  
 如果前面的**！如果**和下一页**！其他**或`!ENDIF`如果`constantexpression`计算结果为一个非零值。  
  
 **!IFDEF***macroname*   
 如果前面的`!IFDEF`和下一页**！其他**或`!ENDIF`如果*macroname*定义。 Null 宏被视为已定义。  
  
 **!IFNDEF***macroname*   
 如果前面的**！IFNDEF**和下一页**！其他**或`!ENDIF`如果*macroname*未定义。  
  
 **!其他**[**如果***常数表达式*&#124;**IFDEF** *macroname*&#124;**IFNDEF** *macroname*]  
 如果前面的**！其他**和下一页`!ENDIF`如果事先**！如果**， `!IFDEF`，或**！IFNDEF**计算结果为零的语句。 可选关键字提供了进一步的预处理的控件。  
  
 **!ELSEIF**  
 同义词**！ELSE IF**。  
  
 **!ELSEIFDEF**  
 同义词**！其他 IFDEF**。  
  
 **!ELSEIFNDEF**  
 同义词**！其他 IFNDEF**。  
  
 `!ENDIF`  
 标记的结束**！如果**， `!IFDEF`，或**！IFNDEF**块。 之后的任何文本`!ENDIF`同一行上将被忽略。  
  
 **!UNDEF***macroname*   
 取消定义*macroname*。  
  
## <a name="see-also"></a>请参阅  
 [生成文件预处理](../build/makefile-preprocessing.md)
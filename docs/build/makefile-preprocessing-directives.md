---
title: "生成文件预处理指令 | Microsoft Docs"
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
  - "!UNDEF"
  - "!INCLUDE"
  - "!IFNDEF"
  - "!MESSAGE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "!CMDSWITCHES 指令"
  - "!ELSE 指令"
  - "!ELSEIF 指令"
  - "!ELSEIFDEF 指令"
  - "!ELSEIFNDEF 指令"
  - "!ENDIF 指令"
  - "!ERROR 指令"
  - "!IF 指令"
  - "!IFDEF 指令"
  - "!IFNDEF 指令"
  - "!INCLUDE 指令"
  - "!MESSAGE 指令"
  - "!UNDEF 指令"
  - "CMDSWITCHES 指令"
  - "指令, 生成文件预处理"
  - "ELSE 指令"
  - "ELSEIF 指令"
  - "ELSEIFDEF 指令"
  - "ELSEIFNDEF 指令"
  - "ENDIF 指令"
  - "ERROR 指令"
  - "IF 指令"
  - "IFDEF 指令"
  - "IFNDEF 指令"
  - "INCLUDE 指令"
  - "生成文件, 预处理指令"
  - "MESSAGE 指令"
  - "NMAKE 程序, 表达式"
  - "NMAKE 程序, 预处理器指令"
  - "预处理指令, 生成文件"
  - "UNDEF 指令"
ms.assetid: bcedeccb-d981-469d-b9e8-ab5d097fd8c2
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 生成文件预处理指令
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

预处理指令不区分大小写。  初始感叹号 \(\!\) 必须出现在行首。  感叹号后面可以有零个或多个空格或制表符，用于缩进。  
  
 **\!CMDSWITCHES**  
 {**\+**&#124;**–**}*option*...  打开或关闭列出的每个 *option*。  空格或制表符必须出现在 \+ 或 \- 运算符前面；运算符和[选项字母](../build/nmake-options.md)之间不能出现任何内容。  字母不区分大小写，并且不用反斜杠 \( \/ \) 指定。  若要打开某些选项而关闭另外一些选项，请使用 **\!CMDSWITCHES** 的分别指定。  
  
 生成文件中只能使用 \/D、\/I、\/N 和 \/S 选项。  在 Tools.ini 文件中可以使用除 \/F、\/HELP、\/NOLOGO、\/X 和 \/? 选项外的其他所有选项。  一个描述块中指定的更改直到下一个描述块时才生效。  该指令更新 **MAKEFLAGS**；如果指定了 **MAKEFLAGS**，则在递归期间继承更改。  
  
 **\!ERROR**  *text*  
 显示错误 U1050 中的 *text*，然后暂停 NMAKE，即便使用了 \/K、\/I、**.IGNORE**、**\!CMDSWITCHES** 或短划线 \(\-\) 命令修饰符。  位于 *text* 之前的空格或制表符被忽略。  
  
 **\!MESSAGE**  *text*  
 显示标准输出的 *text*。  位于 *text* 之前的空格或制表符被忽略。  
  
 **\!INCLUDE**\[ **\<**\] *filename*\[ **\>**\]  
 将 *filename* 作为生成文件读取，然后继续当前的生成文件。  NMAKE 首先在指定或当前目录中搜索 *filename*，然后在任何父生成文件的目录中递归搜索，最后，如果 *filename* 括在尖括号 \(\< \>\) 内，则在由 **INCLUDE**宏（最初设置为 INCLUDE 环境变量）指定的目录中搜索。  对于将 **.SUFFIXES** 设置、**.PRECIOUS** 和推理规则传递给递归生成文件很有用。  
  
 **\!IF**  `constantexpression`  
 如果 `constantexpression` 计算结果为非零值，则处理 **\!IF** 和下一个 **\!ELSE** 或 `!ENDIF` 之间的语句。  
  
 **\!IFDEF**  *macroname*  
 如果定义了 *macroname*，则处理 `!IFDEF` 和下一个 **\!ELSE** 或 `!ENDIF` 之间的语句。  空宏将被视为尚待定义。  
  
 **\!IFNDEF**  *macroname*  
 如果没有定义 *macroname*，则处理 **\!IFNDEF** 和下一个 **\!ELSE** 或 `!ENDIF` 之间的语句。  
  
 **\!ELSE**\[**IF** *constantexpression* &#124; **IFDEF** *macroname*&#124; **IFNDEF** *macroname*\]  
 如果前面的 **\!IF**、`!IFDEF` 或 **\!IFNDEF** 语句计算结果为零值，则处理 **\!ELSE** 和下一个 `!ENDIF` 之间的语句。  可选关键字提供了进一步的预处理控制。  
  
 **\!ELSEIF**  
 **\!ELSE IF** 的同义词。  
  
 **\!ELSEIFDEF**  
 **\!ELSE IFDEF** 的同义词。  
  
 **\!ELSEIFNDEF**  
 **\!ELSE IFNDEF** 的同义词。  
  
 `!ENDIF`  
 标记 **\!IF**、`!IFDEF` 或 **\!IFNDEF** 块的结尾。  同一行上 `!ENDIF` 后面的所有文本被忽略。  
  
 **\!UNDEF**  *macroname*  
 取消定义 *macroname*。  
  
## 请参阅  
 [生成文件预处理](../build/makefile-preprocessing.md)
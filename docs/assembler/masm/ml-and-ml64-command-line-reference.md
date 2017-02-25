---
title: "ML and ML64 Command-Line Reference | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ML"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/W* MASM compiler option"
  - "/c MASM compiler option"
  - "/EP MASM compiler option"
  - "/Fe MASM compiler option"
  - "/Zp MASM compiler option"
  - "/AT MASM compiler option"
  - "/Zm MASM compiler option"
  - "/Sf MASM compiler option"
  - "/Sp MASM compiler option"
  - "/w MASM compiler option"
  - "/Fl MASM compiler option"
  - "/coff MASM compiler option"
  - "/St MASM compiler option"
  - "/Cx MASM compiler option"
  - "/Sl MASM compiler option"
  - "/Cu MASM compiler option"
  - "MASM (Microsoft Macro Assembler), ML command-line reference"
  - "/FPi MASM compiler option"
  - "/Zf MASM compiler option"
  - "ML environment variable"
  - "/Fr MASM compiler option"
  - "/help MASM compiler option"
  - "/Sa MASM compiler option"
  - "/Zd MASM compiler option"
  - "/I MASM compiler option"
  - "/? MASM compiler option"
  - "/Bl MASM compiler option"
  - "/Fm MASM compiler option"
  - "/Fo MASM compiler option"
  - "command-line reference [ML]"
  - "/Sn MASM compiler option"
  - "/Gd MASM compiler option"
  - "/D* MASM compiler option"
  - "environment variables, ML"
  - "/Gc MASM compiler option"
  - "/F* MASM compiler option"
  - "/Sc MASM compiler option"
  - "/H MASM compiler option"
  - "/Zs MASM compiler option"
  - "/omf MASM compiler option"
  - "/Sg MASM compiler option"
  - "/Cp MASM compiler option"
  - "/Zi MASM compiler option"
  - "/nologo MASM compiler option"
  - "/Sx MASM compiler option"
  - "/WX MASM compiler option"
  - "/Ss MASM compiler option"
  - "command line, reference [ML]"
  - "/Ta MASM compiler option"
ms.assetid: 712623c6-f77e-47ea-a945-089e57c50b40
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# ML and ML64 Command-Line Reference
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

程序集并链接到一个或多个汇编语言的源文件。  命令行选项区分大小写。  
  
 有关 ml64.exe 的更多信息，请参见 [MASM for x64 \(ml64.exe\)](../../assembler/masm/masm-for-x64-ml64-exe.md)。  
  
## 语法  
  
```  
ML [[options]] filename [[ [[options]]  filename]]  
ML64 [[options]] filename [[ [[options]]  filename]]  
...  
[[/link linkoptions]]  
```  
  
#### 参数  
 `options`  
 下表中列出的选项。  
  
|选项|操作|  
|--------|--------|  
|**\/AT**|启用细微内存模型支持。  启用违反 .com 格式文件的要求的代码构造的错误消息。  请注意这与 [.MODEL](../../assembler/masm/dot-model.md) **TINY** 指令不是等效的。<br /><br /> 不能用于 ml64.exe。|  
|**\/Bl** `filename`|选择备用链接器。|  
|**\/c**|只有聚合。  不链接。|  
|**\/coff**|生成对象模块的通用对象文件格式 \(COFF\)类型。  通常需要使用 Win32 汇编语言开发。<br /><br /> 不能用于 ml64.exe。|  
|**\/Cp**|保留用例所有用户 ID。|  
|**\/Cu**|映射所有标识符为大写 \(默认值\)。<br /><br /> 不能用于 ml64.exe。|  
|**\/Cx**|在公共和外部符号保留大小写。|  
|**\/D** `symbol`\[\[\=`value`\]\]|定义具有能有一个文本宏。  如果 `value` 缺少，该列为空。  必须用引号空格分隔的多个标记。|  
|**\/EP**|生成一个预处理源列表 \(发送到 STDOUT\)。  请参见 **\/Sf**。|  
|**\/ERRORREPORT** \[ **NONE** &#124; **PROMPT** &#124; **QUEUE** &#124;**SEND** \]|如果 ml.exe 或 ml64.exe 会在运行时，可以使用 **\/ERRORREPORT** 将信息发送到有关这些内部错误的 Microsoft。<br /><br /> 有关 **\/ERRORREPORT**的更多信息，请参见[\/errorReport（报告内部编译器错误）](../../build/reference/errorreport-report-internal-compiler-errors.md)。|  
|**\/F** `hexnum`|设置堆栈大小。 `hexnum` 字节 \(这是一样的。 **\/link\/STACK**:`number`\)。  必须使用十六进制表示法表示值。  必须在 **\/F** 和 `hexnum`之间的一个空格。|  
|**\/Fe** `filename`|将可执行文件。|  
|**\/Fl**\[\[`filename`\]\]|生成一个汇编的代码清单。  请参见 **\/Sf**。|  
|**\/Fm**\[\[`filename`\]\]|创建一个链接器映射文件。|  
|**\/Fo** `filename`|给定对象文件。  请参见 " 备注 " 部分有关更多信息。|  
|**\/FPi**|生成模拟器浮点数学 \(仅混合语言解决引发\)。<br /><br /> 不能用于 ml64.exe。|  
|**\/Fr**\[\[`filename`\]\]|生成一个源浏览器 .sbr 文件。|  
|**\/FR**\[\[`filename`\]\]|生成源浏览器 .sbr 文件的一个扩展的窗体。|  
|**\/Gc**|指定要编写或 Pascal 样式函数调用的和命名约定的使用。  和 **OPTION LANGUAGE:PASCAL**相同。<br /><br /> 不能用于 ml64.exe。|  
|**\/Gd**|指定对 C 样式函数调用的和命名约定的使用。  和 **OPTION LANGUAGE:C**相同。<br /><br /> 不能用于 ml64.exe。|  
|**\/GZ**|指定要 \_\_stdcall 函数调用的和命名约定的使用。  和 **OPTION LANGUAGE:STCALL**相同。<br /><br /> 不能用于 ml64.exe。|  
|**\/H** `number`|限制外部名称计算重要的字符。  默认值为 31 个字符。<br /><br /> 不能用于 ml64.exe。|  
|**\/help**|调用帮助的 QuickHelp 在语言。|  
|**\/I** `pathname`|设置路径为包含文件。  最多 10 个 **\/I** 选项卡。|  
|**\/nologo**|取消成功的程序集的消息。|  
|**\/omf**|生成对象模块 \(OMF\)对象模块的文件格式类型。  **\/omf** 提示 **\/c**;ML.exe 不支持链接 OMF 对象。<br /><br /> 不能用于 ml64.exe。|  
|**\/Sa**|启用列出所有可用的信息。|  
|**\/safeseh**|不标记对象转换为包含异常处理程序或包含整个声明 [.SAFESEH](../../assembler/masm/dot-safeseh.md)的异常处理程序。<br /><br /> 不能用于 ml64.exe。|  
|**\/Sf**|添加初始通过列表到列表文件。|  
|**\/Sl** `width`|设置列表中字符的源的线条宽度每行。  范围为 60 到 255 或 0。  默认值为 0。  和 [页](../../assembler/masm/page.md) 宽度相同。|  
|**\/Sn**|导致时，列表时，关闭符号表。|  
|**\/Sp** `length`|设置列表中每页行数的源的页长。  范围为 10 到 255 或 0。  默认值为 0。  和 [页](../../assembler/masm/page.md) 长度相同。|  
|**\/Ss** `text`|为源中指定的文本。  和 [子标题](../../assembler/masm/subtitle.md) 文本相同。|  
|**\/St** `text`|为源中指定的前缀。  和 [前缀](../../assembler/masm/title.md) 文本相同。|  
|**\/Sx**|打开列表中的错误条件。|  
|**\/Ta** `filename`|程序集名称以 .asm 扩展不关闭的源文件。|  
|**\/w**|和 **\/W0\/WX**相同。|  
|**\/W** `level`|设置警告等级， `level` \= 0， 1， 2 或 3。|  
|**\/WX**|，如果将生成警告，返回错误代码。|  
|**\/X**|忽略包括环境路径。|  
|**\/Zd**|生成在对象文件中的行号信息。|  
|**\/Zf**|使所有公共符号。|  
|**\/Zi**|生成在对象文件的 CodeView 信息。|  
|**\/Zm**|启用最大的兼容性**M510** 选项与 MASM 5.1。<br /><br /> 不能用于 ml64.exe。|  
|**\/Zp**\[\[`alignment`\]\]|封装在指定的字节界的结构。  `alignment` 可以是 1， 2 或 4。|  
|**\/Zs**|仅执行一语法检查。|  
|**\/?**|显示语言命令行语法摘要。|  
  
 `filename`  
 文件名。  
  
 `linkoptions`  
 LINK 选项。  有关更多信息，请参见[链接器选项](../../build/reference/linker-options.md)。  
  
## 备注  
 对语言和 ML64 的命令行选项是位置区分。  例如，在中，因为语言和 ML64 可以接受多种 **\/c** 选项，必须在 **\/c**之前指定任何对应的 **\/Fo** 选项。  下面的命令行示例演示每个程序集文件规范的对象文件规范:  
  
 **ml.exe \/Fo a1.obj \/c a.asm \/Fo b1.obj \/c b.asm**  
  
## 环境变量  
  
|变量|说明|  
|--------|--------|  
|包含|指定搜索路径为包含文件。|  
|语言|指定默认命令行选项。|  
|TMP|用于临时文件指定路径。|  
  
## 请参阅  
 [ML Error Messages](../../assembler/masm/ml-error-messages.md)   
 [Microsoft Macro Assembler Reference](../../assembler/masm/microsoft-macro-assembler-reference.md)
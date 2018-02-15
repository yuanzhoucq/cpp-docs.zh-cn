---
title: "ML 和 ML64 命令行参考 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ML
dev_langs:
- C++
helpviewer_keywords:
- /W* MASM compiler option
- /c MASM compiler option
- /EP MASM compiler option
- /Fe MASM compiler option
- /Zp MASM compiler option
- /AT MASM compiler option
- /Zm MASM compiler option
- /Sf MASM compiler option
- /Sp MASM compiler option
- /w MASM compiler option
- /Fl MASM compiler option
- /coff MASM compiler option
- /St MASM compiler option
- /Cx MASM compiler option
- /Sl MASM compiler option
- /Cu MASM compiler option
- MASM (Microsoft Macro Assembler), ML command-line reference
- /FPi MASM compiler option
- /Zf MASM compiler option
- ML environment variable
- /Fr MASM compiler option
- /help MASM compiler option
- /Sa MASM compiler option
- /Zd MASM compiler option
- /I MASM compiler option
- /? MASM compiler option
- /Bl MASM compiler option
- /Fm MASM compiler option
- /Fo MASM compiler option
- command-line reference [ML]
- /Sn MASM compiler option
- /Gd MASM compiler option
- /D* MASM compiler option
- environment variables, ML
- /Gc MASM compiler option
- /F* MASM compiler option
- /Sc MASM compiler option
- /H MASM compiler option
- /Zs MASM compiler option
- /omf MASM compiler option
- /Sg MASM compiler option
- /Cp MASM compiler option
- /Zi MASM compiler option
- /nologo MASM compiler option
- /Sx MASM compiler option
- /WX MASM compiler option
- /Ss MASM compiler option
- command line, reference [ML]
- /Ta MASM compiler option
ms.assetid: 712623c6-f77e-47ea-a945-089e57c50b40
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: edb7f0c19e9517b1bcefcc2400542f910a73c8f0
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="ml-and-ml64-command-line-reference"></a>ML 和 ML64 命令行参考
汇编，并链接一个或多个程序集语言源文件。 命令行选项是区分大小写。  
  
 Ml64.exe 的详细信息，请参阅[x64 (ml64.exe) 的 MASM](../../assembler/masm/masm-for-x64-ml64-exe.md)。  
  
## <a name="syntax"></a>语法  
  
```  
ML [[options]] filename [[ [[options]]  filename]]  
ML64 [[options]] filename [[ [[options]]  filename]]  
...  
[[/link linkoptions]]  
```  
  
#### <a name="parameters"></a>参数  
 `options`  
 下表中列出的选项。  
  
|选项|操作|  
|------------|------------|  
|**/AT**|小内存模型支持。 启用对违反.com 格式化文件的要求的代码构造的错误消息。 请注意，这是不等效于[。模型](../../assembler/masm/dot-model.md)**微小**指令。<br /><br /> 在 ml64.exe 中不可用。|  
|**/Bl** `filename`|选择备用的链接器。|  
|**/c**|仅汇编。 没有链接。|  
|**/coff**|生成对象模块的通用对象文件格式 (COFF) 的类型。 通常所需的 Win32 程序集语言开发。<br /><br /> 在 ml64.exe 中不可用。|  
|**/Cp**|保留所有用户标识符的大小的写。|  
|**/Cu**|将所有标识符都映射为大写形式 （默认值）。<br /><br /> 在 ml64.exe 中不可用。|  
|**/Cx**|保留大小写的公共和外部符号。|  
|**/D** `symbol`[[=`value`]]|定义具有给定名称的文本宏。 如果`value`是缺少，此字段为空。 用空格分隔的多个令牌都必须用引号引起来。|  
|**/EP**|生成 （发送到 STDOUT） 的预处理的源列表。 请参阅**/Sf**。|  
|**/ERRORREPORT** [ **NONE** &#124; **PROMPT** &#124; **QUEUE** &#124; **SEND** ]|如果 ml.exe 或 ml64.exe 运行时失败，则可以使用**/ERRORREPORT**信息向 Microsoft 发送有关这些内部错误。<br /><br /> 有关详细信息**/ERRORREPORT**，请参阅[/errorReport （报告内部编译器错误）](../../build/reference/errorreport-report-internal-compiler-errors.md)。|  
|**/F** `hexnum`|设置堆栈大小为`hexnum`字节 (这是与相同**/链接/堆栈**:`number`)。 值必须用十六进制表示法表示。 必须有之间留一个空格**/F**和`hexnum`。|  
|**/Fe** `filename`|命名的可执行文件。|  
|**/Fl**[[`filename`]]|生成装配的代码列表。 请参阅**/Sf**。|  
|**/Fm**[[`filename`]]|创建链接器映射文件。|  
|**/Fo** `filename`|命名的对象文件。 有关详细信息，请参阅备注部分。|  
|**/FPi**|生成仿真程序修复增量备份的浮点算术 （仅混合语言）。<br /><br /> 在 ml64.exe 中不可用。|  
|**/Fr**[[`filename`]]|生成源浏览器.sbr 文件。|  
|**/FR**[[`filename`]]|生成源浏览器.sbr 文件以扩展的形式。|  
|**/Gc**|指定使用 FORTRAN 或 Pascal 样式函数调用和命名约定。 与相同**选项语言： PASCAL**。<br /><br /> 在 ml64.exe 中不可用。|  
|**/Gd**|指定使用 C 样式函数调用和命名约定。 与相同**选项语言： C**。<br /><br /> 在 ml64.exe 中不可用。|  
|**/GZ**|指定使用 __stdcall 函数调用和命名约定。  与相同**选项语言： STCALL**。<br /><br /> 在 ml64.exe 中不可用。|  
|**/H** `number`|将数字的重要字符限制外部名称。 默认值为 31 个字符。<br /><br /> 在 ml64.exe 中不可用。|  
|**/help**|有关帮助 ML 调用 QuickHelp。|  
|**/I** `pathname`|包含文件的集路径。 最多 10 个**/I**允许选项。|  
|**/nologo**|禁止显示成功的程序集的消息。|  
|**/omf**|生成对象模块对象模块文件格式 (OMF) 的类型。  **/omf**意味着**/c**;ML.exe 不支持链接 OMF 对象。<br /><br /> 在 ml64.exe 中不可用。|  
|**/Sa**|打开的所有可用信息的列表。|  
|**/safeseh**|将标记为包含没有异常处理程序或包含异常处理程序的所有声明的对象[。SAFESEH](../../assembler/masm/dot-safeseh.md)。<br /><br /> 在 ml64.exe 中不可用。|  
|**/Sf**|添加第一个过程列表到列表文件。|  
|**/Sl** `width`|设置源列表中每行的字符的线条宽度。 范围是 60 到 255 个或 0。 默认值为 0。 与相同[页](../../assembler/masm/page.md)宽度。|  
|**/Sn**|用于符号表关闭时生成列表。|  
|**/Sp** `length`|设置页长度的源列表中每页行数。 范围是 10 到 255 个或 0。 默认值为 0。 与相同[页](../../assembler/masm/page.md)长度。|  
|**/Ss** `text`|指定有关源列表的文本。 与相同[副标题](../../assembler/masm/subtitle.md)文本。|  
|**/St** `text`|指定源列表的标题。 与相同[标题](../../assembler/masm/title.md)文本。|  
|**/Sx**|打开在列表中的 false 条件语句。|  
|**/Ta** `filename`|汇编其名称不是以.asm 扩展名结尾的源文件。|  
|**/w**|与相同**/W0/WX**。|  
|**/W** `level`|设置警告等级，其中`level`= 0、 1、 2 或 3。|  
|**/WX**|如果不生成警告，则返回错误代码。|  
|**/X**|忽略 INCLUDE 环境路径。|  
|**/Zd**|在对象文件中生成行号信息。|  
|**/Zf**|使所有符号公共。|  
|**/Zi**|在对象文件中生成的 CodeView 信息。|  
|**/Zm**|使**M510** MASM 5.1 的最大兼容性的选项。<br /><br /> 在 ml64.exe 中不可用。|  
|**/Zp**[[`alignment`]]|在指定的字节边界上的包结构。 `alignment`可以是 1、 2 或 4。|  
|**/Zs**|执行语法检查。|  
|**/?**|显示 ML 命令行语法的摘要。|  
  
 `filename`  
 文件的名称。  
  
 `linkoptions`  
 链接选项。  请参阅[链接器选项](../../build/reference/linker-options.md)有关详细信息。  
  
## <a name="remarks"></a>备注  
 ML 和 ML64 某些命令行选项是放置区分。 例如，因为 ML 和 ML64 可以接受多个**/c**选项，任何对应**/Fo**之前，必须指定选项**/c**。 下面的命令行示例阐释了每个程序集文件规格的对象文件规范：  
  
 **ml.exe /Fo a1.obj /c a.asm /Fo b1.obj /c b.asm**  
  
## <a name="environment-variables"></a>环境变量  
  
|变量|描述|  
|--------------|-----------------|  
|INCLUDE|指定包含文件的搜索路径。|  
|ML|指定默认命令行选项。|  
|TMP|指定临时文件的路径。|  
  
## <a name="see-also"></a>请参阅  
 [ML 错误消息](../../assembler/masm/ml-error-messages.md)   
 [Microsoft 宏汇编程序参考](../../assembler/masm/microsoft-macro-assembler-reference.md)
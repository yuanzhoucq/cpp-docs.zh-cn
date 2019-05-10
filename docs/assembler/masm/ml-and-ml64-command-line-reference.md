---
title: ML 和 ML64 命令行参考
ms.date: 08/30/2018
f1_keywords:
- ML
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
ms.openlocfilehash: a452bab03e31436ee5dde476117bce8b73c7571f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62178106"
---
# <a name="ml-and-ml64-command-line-reference"></a>ML 和 ML64 命令行参考

组装并链接一个或多个程序集语言源代码文件。 命令行选项是区分大小写。

Ml64.exe 的详细信息，请参阅[MASM 的 x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md)。

## <a name="syntax"></a>语法

> ML \[*options*] *filename* \[ \[*options*]  *filename*]
>
> ML64 \[*选项*] *filename* \[ \[*选项*]*文件名*]...\[/link *linkoptions*]

### <a name="parameters"></a>参数

*options*<br/>
下表中列出的选项。

|选项|操作|
|------------|------------|
|**/AT**|小内存模型支持。 使违反.com 格式化文件的要求的代码构造的错误消息。 请注意这并不等同于[。模型](../../assembler/masm/dot-model.md)**微小**指令。<br /><br /> Ml64.exe 中不可用。|
|**/Bl** *文件名*|选择备用的链接器。|
|**/c**|仅汇编。 没有链接。|
|**/coff**|生成通用对象文件格式 (COFF) 类型的对象模块。 通常所需的 Win32 程序集语言开发。<br /><br /> Ml64.exe 中不可用。|
|**/Cp**|将保留所有的用户标识符的大小写。|
|**/Cu**|将所有标识符都映射为大写 （默认值）。<br /><br /> Ml64.exe 中不可用。|
|**/Cx**|保留在公共和外部符号的大小写。|
|**/D** *符号*[[=*值*]]|定义具有给定名称的文本宏。 如果*值*是缺失、 为空。 由空格分隔的多个令牌必须括在引号中。|
|**/EP**|生成预处理过的源列表 （发送到 STDOUT）。 请参阅 **/Sf**。|
|**/ERRORREPORT** [ **NONE** &#124; **PROMPT** &#124; **QUEUE** &#124; **SEND** ]|如果 ml.exe 或 ml64.exe 在运行时失败，则可以使用 **/ERRORREPORT**有关这些内部错误向 Microsoft 发送信息。<br /><br /> 有关详细信息 **/ERRORREPORT**，请参阅[/errorReport （报告内部编译器错误）](../../build/reference/errorreport-report-internal-compiler-errors.md)。|
|**/F** *hexnum*|设置堆栈大小不超过*hexnum*字节 (这是与相同 **/链接/堆栈**:*数*)。 值必须以十六进制表示法表示。 必须有之间有空格 **/F**并*hexnum*。|
|**/Fe** *filename*|命名的可执行文件。|
|**/Fl**[[*filename*]]|生成的已组装的代码的列表。 请参阅 **/Sf**。|
|**/Fm**[[*filename*]]|创建链接器映射文件。|
|**/Fo** *文件名*|命名的对象文件。 有关详细信息，请参阅备注部分。|
|**/FPi**|生成仿真程序修补程序-ups 以获取浮点运算 （仅混合语言）。<br /><br /> Ml64.exe 中不可用。|
|**/Fr**[[*filename*]]|生成源浏览器的.sbr 文件。|
|**/FR**[[*filename*]]|生成源浏览器的.sbr 文件的扩展窗体。|
|**/Gc**|指定使用 FORTRAN 或 Pascal 样式的函数调用和命名约定。 与相同**选项语言： PASCAL**。<br /><br /> Ml64.exe 中不可用。|
|**/Gd**|指定使用 C 样式函数调用和命名约定。 与相同**选项语言： C**。<br /><br /> Ml64.exe 中不可用。|
|**/GZ**|指定使用 __stdcall 函数调用和命名约定。  与相同**选项语言： STCALL**。<br /><br /> Ml64.exe 中不可用。|
|**/H** *number*|将外部名称限制为数字的重要字符。 默认值为 31 个字符。<br /><br /> Ml64.exe 中不可用。|
|**/help**|调用 QuickHelp 有关机器学习的帮助。|
|**/I** *pathname*|设置包含文件的路径。 最多 10 个 **/I**允许选项。|
|**/nologo**|禁止显示成功的程序集的消息。|
|**/omf**|生成对象模块文件格式 (OMF) 类型的对象模块。  **/omf**意味着 **/c**;ML.exe 不支持链接 OMF 对象。<br /><br /> Ml64.exe 中不可用。|
|**/Sa**|打开的所有可用信息的列表。|
|**/safeseh**|将标记为包含没有异常处理程序或包含异常处理程序使用而声明对象[。SAFESEH](../../assembler/masm/dot-safeseh.md)。<br /><br /> Ml64.exe 中不可用。|
|**/Sf**|添加第一次通过列表到列表文件。|
|**/Sl** *width*|设置源列表中每行字符的线条宽度。 范围是 60 至 255 个或 0。 默认值为 0。 与相同[页](../../assembler/masm/page.md)宽度。|
|**/Sn**|如果在生成列表，请关闭符号表。|
|**/Sp** *长度*|设置页面长度的源列表中每页行数。 范围是 10 到 255 个或 0。 默认值为 0。 与相同[页](../../assembler/masm/page.md)长度。|
|**/Ss** *text*|指定源列表的文本。 与相同[副标题](../../assembler/masm/subtitle.md)文本。|
|**/St** *text*|指定源列表的标题。 与相同[标题](../../assembler/masm/title.md)文本。|
|**/Sx**|打开列表中的 false 条件语句。|
|**/Ta** *filename*|对源代码文件的名称不以.asm 扩展名结尾。|
|**/w**|与相同 **/W0/WX**。|
|**/W** *level*|设置警告级别，其中*级别*= 0、 1、 2 或 3。|
|**/WX**|如果将生成警告，则返回错误代码。|
|**/X**|忽略包含环境路径。|
|**/Zd**|在对象文件中生成行号信息。|
|**/Zf**|使所有符号公共。|
|**/Zi**|生成对象文件中的 CodeView 信息。|
|**/Zm**|使**M510** MASM 5.1 的最大兼容性的选项。<br /><br /> Ml64.exe 中不可用。|
|**/Zp**[[*alignment*]]|针对指定的字节边界将结构打包。 *对齐*可以是 1、 2 或 4。|
|**/Zs**|执行语法检查。|
|**/?**|显示机器学习命令行语法的摘要。|

*filename*<br/>
文件的名称。

*linkoptions*<br/>
链接选项。  请参阅[链接器选项](../../build/reference/linker-options.md)有关详细信息。

## <a name="remarks"></a>备注

ML 和 ML64 一些命令行选项是区分放置的。 例如，因为 ML 和 ML64 可接受多个 **/c**选项，任何对应 **/Fo**之前，必须指定选项 **/c**。 下面的命令行示例说明了每个程序集文件规范的对象文件规范：

**ml.exe /Fo a1.obj /c a.asm /Fo b1.obj /c b.asm**

## <a name="environment-variables"></a>环境变量

|变量|描述|
|--------------|-----------------|
|INCLUDE|指定包含文件的搜索路径。|
|ML|指定默认命令行选项。|
|TMP|指定临时文件的路径。|

## <a name="see-also"></a>请参阅

[ML 错误消息](../../assembler/masm/ml-error-messages.md)<br/>
[Microsoft 宏汇编程序参考](../../assembler/masm/microsoft-macro-assembler-reference.md)<br/>
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
ms.openlocfilehash: 470cad1be6fe314fde89ee144a8935664ead5953
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74397199"
---
# <a name="ml-and-ml64-command-line-reference"></a>ML 和 ML64 命令行参考

汇编和链接一个或多个汇编语言源文件。 命令行选项区分大小写。

有关 ml64.exe 的详细信息，请参阅[MASM for x64 （ml64.exe）](../../assembler/masm/masm-for-x64-ml64-exe.md)。

## <a name="syntax"></a>语法

> ML \[*选项*] *filename* \[ \[*选项*] *filename*]
>
> ML64.EXE \[*options*] *filename* \[ \[*选项*] *filename*] ... \[/link *linkoptions*]

### <a name="parameters"></a>参数

*选项*\
下表中列出的选项。

|选项|操作|
|------------|------------|
|**/AT**|启用小型内存模型支持。 启用违反 .com 格式文件要求的代码构造的错误消息。 请注意，这与不等效[。](../../assembler/masm/dot-model.md)对**小**指令建模。<br /><br /> 在 ml64.exe 中不可用。|
|**/Bl** *filename*|选择备用链接器。|
|**/c**|仅装配。 不链接。|
|**/coff**|生成对象模块的通用对象文件格式（COFF）类型。 通常，Win32 汇编语言开发需要。<br /><br /> 在 ml64.exe 中不可用。|
|**/Cp**|保留所有用户标识符的大小写。|
|**/Cu**|将所有标识符映射为大写（默认值）。<br /><br /> 在 ml64.exe 中不可用。|
|**/Cx**|保留公共和 extern 符号中的大小写。|
|**/D** *symbol*⟦ =*value*⟧|定义具有给定名称的文本宏。 如果缺少值，则*该值*为空。 用空格分隔的多个标记必须用引号引起来。|
|**/EP**|生成一个预处理的源列表（发送到 STDOUT）。 请参阅 **/Sf**。|
|**/ERRORREPORT** [**无** &#124; **提示** &#124;队列&#124; **发送**]|如果 ml 或 ml64.exe 在运行时失败，则可以使用 **/ERRORREPORT**向 Microsoft 发送有关这些内部错误的信息。<br /><br /> 有关 **/ERRORREPORT**的详细信息，请参阅[/ERRORREPORT （报告内部编译器错误）](../../build/reference/errorreport-report-internal-compiler-errors.md)。|
|**/F** *hexnum*|将堆栈大小设置为*hexnum*字节（与 **/link/STACK**：*number*相同）。 该值必须用十六进制表示法表示。 在 **/f**和*hexnum*之间必须有一个空格。|
|**/Fe** *filename*|命名可执行文件。|
|**/Fl**⟦*filename*⟧|生成汇编的代码清单。 请参阅 **/Sf**。|
|**/Fm**⟦*filename*⟧|创建链接器映射文件。|
|**/Fo** *filename*|命名对象文件。 有关详细信息，请参阅备注部分。|
|**/FPi**|为浮点运算生成模拟器修复方法（仅限混合语言）。<br /><br /> 在 ml64.exe 中不可用。|
|**/Fr**⟦*filename*⟧|生成源浏览器 .sbr 文件。|
|**/Fr**⟦*filename*⟧|生成源浏览器 .sbr 文件的扩展形式。|
|**/Gc**|指定使用 FORTRAN 或 Pascal 样式的函数调用和命名约定。 与**选项语言相同： PASCAL**。<br /><br /> 在 ml64.exe 中不可用。|
|**/Gd**|指定使用 C 样式函数调用和命名约定。 与**选项语言相同： C**。<br /><br /> 在 ml64.exe 中不可用。|
|**/GZ**|指定使用 __stdcall 函数调用和命名约定。  与**选项语言相同： STCALL**。<br /><br /> 在 ml64.exe 中不可用。|
|**/H** *数字*|限制外部名称为有效字符数。 默认值为31个字符。<br /><br /> 在 ml64.exe 中不可用。|
|**/help**|调用 QuickHelp 获取有关 ML 的帮助。|
|**/I** *路径名称*|设置包含文件的路径。 最多允许10个 **/i**选项。|
|**/nologo**|禁止成功的程序集的消息。|
|**/omf**|生成对象模块的对象模块文件格式（OMF）类型。  **/omf**表示 **/c**;ML 不支持链接 OMF 对象。<br /><br /> 在 ml64.exe 中不可用。|
|**/Sa**|打开列出所有可用信息。|
|**/safeseh**|将对象标记为不包含异常处理程序或包含所有声明为的异常处理程序[。SAFESEH](../../assembler/masm/dot-safeseh.md)。<br /><br /> 在 ml64.exe 中不可用。|
|**/Sf**|将第一个传递列表添加到列表文件中。|
|**/Sl** *宽度*|设置源列表的线条宽度（以字符为单位）。 范围为60到255或0。 默认值为0。 与[页面](../../assembler/masm/page.md)宽度相同。|
|**/Sn**|生成列表时关闭符号表。|
|**/Sp** *长度*|设置源列表的页面长度（以页为单位）。 范围为10到255或0。 默认值为0。 与[页面](../../assembler/masm/page.md)长度相同。|
|**/Ss** *文本*|指定源列表的文本。 与[副标题](../../assembler/masm/subtitle.md)文本相同。|
|**/St** *文本*|指定源列表的标题。 与[标题](../../assembler/masm/title.md)文本相同。|
|**/Sx**|在列表中打开 false 条件。|
|**/Ta** *filename*|汇编其名称不以 .asm 扩展名结尾的源文件。|
|**/w**|与 **/W0/WX**相同。|
|**/W** *级别*|设置警告等级，其中*level* = 0、1、2或3。|
|**/WX**|如果生成警告，则返回错误代码。|
|**/X**|忽略 INCLUDE 环境路径。|
|**/Zd**|在对象文件中生成行号信息。|
|**/Zf**|使所有符号成为公共的。|
|**/Zi**|生成对象文件中的 CodeView 信息。|
|**/Zm**|启用**M510**选项，以实现与 MASM 5.1 的最大兼容性。<br /><br /> 在 ml64.exe 中不可用。|
|⟧/Zp⟦|将结构打包到指定的字节边界上。 *对齐方式*可以是1、2或4。|
|**/Zs**|仅执行语法检查。|
|**/?**|显示 ML 命令行语法摘要。|

*文件名*\
文件的名称。

*linkoptions*\
链接选项。  有关详细信息，请参阅[链接器选项](../../build/reference/linker-options.md)。

## <a name="remarks"></a>备注

ML 和 ML64.EXE 的某些命令行选项是位置相关的。 例如，因为 ML 和 ML64.EXE 可以接受多个 **/c**选项，所以必须在 **/c**之前指定任何相应的 **/fo**选项。 以下命令行示例说明了每个程序集文件规范的对象文件规范：

**ml/Fo a1 .obj/c a .asm/Fo b1 .obj .obj**

## <a name="environment-variables"></a>环境变量

|变量|说明|
|--------------|-----------------|
|INCLUDE|指定包含文件的搜索路径。|
|ML|指定默认的命令行选项。|
|TMP|指定临时文件的路径。|

## <a name="see-also"></a>另请参阅

[ML 错误消息](../../assembler/masm/ml-error-messages.md)\
[Microsoft 宏汇编程序参考](../../assembler/masm/microsoft-macro-assembler-reference.md)

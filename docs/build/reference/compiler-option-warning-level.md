---
title: /w、/W0、/W1、/W2、/W3、/W4、/w1、/w2、/w3、/w4、/Wall、/wd、/we、/wo、/Wv、/WX（警告级别）
description: Microsoft C/C++编译器选项的参考：/W、/W0、/W1、/W2、/W3、/W4、/W1、/W2、/W3、/W4、/Wall、/wd、/we、/Wo、/WV 和/WX。
ms.date: 01/31/2020
f1_keywords:
- VC.Project.VCCLCompilerTool.DisableSpecificWarnings
- VC.Project.VCCLCompilerTool.WarningLevel
- VC.Project.VCCLWCECompilerTool.DisableSpecificWarnings
- VC.Project.VCCLCompilerTool.WarnAsError
- VC.Project.VCCLWCECompilerTool.WarnAsError
- /wx
- VC.Project.VCCLWCECompilerTool.WarningLevel
- /wall
- VC.Project.VCCLCompilerTool.TreatSpecificWarningsAsErrors
- /Wv
- /w0
- /w1
- /w2
- /w3
- /w4
- /wd
- /we
- /wo
helpviewer_keywords:
- /W1 compiler option [C++]
- w compiler option [C++]
- -wo compiler option [C++]
- Warning Level compiler option
- W1 compiler option [C++]
- -we compiler option [C++]
- /WX compiler option [C++]
- -wd compiler option [C++]
- WX compiler option [C++]
- wo compiler option [C++]
- Wall compiler option [C++]
- /w compiler option
- W2 compiler option [C++]
- -W2 compiler option [C++]
- wd compiler option [C++]
- /we compiler option [C++]
- we compiler option [C++]
- -W1 compiler option [C++]
- -W4 compiler option [C++]
- -Wall compiler option [C++]
- /Wall compiler option [C++]
- -W0 compiler option [C++]
- W0 compiler option [C++]
- -WX compiler option [C++]
- /wo compiler option [C++]
- W4 compiler option [C++]
- W3 compiler option [C++]
- /wd compiler option [C++]
- warnings, as errors compiler option
- /W3 compiler option [C++]
- /W0 compiler option [C++]
- /W4 compiler option [C++]
- -W3 compiler option [C++]
- -w compiler option [C++]
- /W2 compiler option [C++]
- /Wv compiler option [C++]
ms.openlocfilehash: 80b6d0c1fe684de9af62683a75f0fd1107a94089
ms.sourcegitcommit: ba4180a2d79d7e391f2f705797505d4aedbc2a5e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2020
ms.locfileid: "76972174"
---
# <a name="w-w0-w1-w2-w3-w4-w1-w2-w3-w4-wall-wd-we-wo-wv-wx-warning-level"></a>/w、/W0、/W1、/W2、/W3、/W4、/w1、/w2、/w3、/w4、/Wall、/wd、/we、/wo、/Wv、/WX（警告级别）

指定编译器如何为给定编译生成警告。

## <a name="syntax"></a>语法

> **/w**\
> **/W0**\
> **/W1**\
> **/W2**\
> **/W3**\
> **/W4**\
> **/Wall**\
> **/Wv**\[ **：** _版本_] \
> **/Wx**\
> **/w1**_警告_\
> **/w2**_警告_\
> **/w3**_警告_\
> **/w4**_警告_\
> **/wd**_警告_\
> **/we**_警告_\
> **/wo**_警告_

## <a name="remarks"></a>备注

警告选项指定要显示的编译器警告和整个编译的警告行为。

警告选项和相关参数在下表中进行了说明：

选项 | 描述
------ | -----------
**/w** | 禁止显示所有编译器警告。
**/W0**<br /><br /> **/W1**<br /><br /> **/W2**<br /><br /> **/W3**<br /><br /> **/W4** | 指定编译器生成的警告级别。 有效的警告等级范围为0到4：<br />**/W0**禁止显示所有警告。 它与 **/w**等效。<br />**/W1**显示等级1（严重）警告。 **/W1**是命令行编译器中的默认设置。<br />**/W2**显示 level 1 和 level 2 （重大）警告。<br />**/W3**显示1级、2级和3级（生产质量）警告。 **/W3**是 IDE 中的默认设置。<br />**/W4**显示级别1、级别2和级别3警告以及默认情况下未关闭的所有级别4（信息）警告。 建议使用此选项来提供不起毛的警告。 对于新项目，最好在所有编译中使用 **/W4** 。 此选项有助于确保最少的硬查找代码缺陷。
**/Wall** | 显示 **/W4**显示的所有警告以及 **/W4**不包括的所有其他警告，例如默认情况下处于关闭状态的警告。 有关详细信息，请参阅[默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。
**/Wv**\[ **:** _version_] | 仅显示*版本*编译器版本及更早版本中引入的警告。 当你迁移到较新版本的编译器时，可以使用此选项取消代码中的新警告。 它使您可以在修复现有的生成过程时维持现有的生成过程。 可选参数*版本*采用*nn*\[形式。*mm*\[。*aaaaa-bbbbb-ccccc-dddddd-eeeeee*]]，其中*nn*是主版本号， *mm*是可选次版本号， *aaaaa-bbbbb-ccccc-dddddd-eeeeee*是编译器的可选生成号。 例如，使用 **/Wv： 17**只显示 Visual Studio 2012 （主版本17）或更早版本中引入的警告。 也就是说，它显示的是版本号为17或更低的任何编译器版本的警告。 它抑制 Visual Studio 2013 （主要版本18）和更高版本中引入的警告。 默认情况下， **/Wv**使用当前编译器版本号，不会禁止显示任何警告。 有关编译器版本禁止显示的警告的信息，请参阅编译器[警告（按编译器版本](../../error-messages/compiler-warnings/compiler-warnings-by-compiler-version.md)）。
**/WX** | 将所有编译器警告视为错误。 对于新项目，最好在所有编译中使用 **/wx** ;解决所有警告可确保最少的硬查找代码缺陷。<br /><br /> 链接器还具有 **/wx**选项。 有关详细信息，请参阅 [/WX（将链接器警告视为错误）](wx-treat-linker-warnings-as-errors.md)。

以下选项互相排斥。 此组中指定的最后一个选项是应用的选项：

选项 | 描述
------ | -----------
**/w1**_nnnn_<br /><br /> **/w2**_nnnn_<br /><br /> **/w3**_nnnn_<br /><br /> **/w4**_nnnn_ | 为_nnnn_指定的警告编号设置警告等级。 通过这些选项，可以在设置特定警告级别时更改该警告的编译器行为。 可以结合使用这些选项和其他警告选项来强制执行你自己的警告编码标准，而不是 Visual Studio 提供的默认值。<br /><br /> 例如， **/w34326**使 C4326 生成为等级3警告而不是级别1。 如果使用 **/w34326**选项和 **/W2**选项进行编译，则不会生成警告 C4326。
**/wd**_nnnn_ | 取消_nnnn_指定的编译器警告。<br /><br /> 例如， **/wd4326**禁止显示编译器警告 C4326。
**/we**_nnnn_ | 将_nnnn_指定的编译器警告视为错误。<br /><br /> 例如， **/we4326**导致编译器将警告号 C4326 视为错误。
**/wo**_nnnn_ | 报告由_nnnn_指定的编译器警告。<br /><br /> 例如， **/wo4326**使警告 C4326 仅在编译器第一次遇到时报告一次。

如果在创建预编译标头时使用任何警告选项，则会保留这些设置。 使用预编译标头会使这些相同的警告选项再次生效。 若要重写预编译标头警告选项，请在命令行上设置其他警告选项。

您可以使用[#pragma warning](../../preprocessor/warning.md)指令来控制在编译时在特定源文件中报告的警告级别。

源代码中的警告杂注指令不受 **/w**选项的影响。

[生成错误文档](../../error-messages/compiler-errors-1/c-cpp-build-errors.md)描述了警告和警告级别，并指示某些语句可能不会按预期方式编译。

### <a name="to-set-the-compiler-options-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置编译器选项

1. 打开项目的“属性页” 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 若要设置 **"/W0**"、" **/W1**"、" **/W2**"、" **/W3**"、" **/W4** **"、"/Wall"** 、" **/Wv**"**或**" **/WX-** " 选项，请选择 "**配置属性** ** > C++ > "**

   - 若要设置 **/W0**、 **/W1**、 **/W2**、 **/W3**、 **/W4**或 **/Wall**选项，请修改**警告等级**属性。

   - 若要设置 **/wx**或 **/WX-** 选项，请修改 "将**警告视为错误**" 属性。

   - 若要设置 **/Wv**选项的版本，请在 "**警告版本**" 属性中输入编译器版本号。

1. 若要设置 " **/wd** " 或 " **/we** " 选项，请选择 "**配置属性**" > **C/C++**  > "**高级**" 属性页。

   - 若要设置 **/wd**选项，请选择 "**禁用特定的警告**属性" 下拉控件，然后选择 "**编辑**"。 在 "**禁用特定警告**" 对话框的 "编辑" 框中，输入警告编号。 若要输入多个警告，请使用分号（ **;** ）分隔值。 例如，若要禁用 C4001 和 C4010，请输入**4001; 4010**。 选择 **"确定"** 保存更改并返回到 "**属性页**" 对话框。

   - 若要设置 **/we**选项，请选择 "将**特定警告视为错误**" 下拉控件，然后选择 "**编辑**"。 在 "将**特定警告视为错误**" 对话框中的 "编辑" 框中，输入警告编号。 若要输入多个警告，请使用分号（ **;** ）分隔值。 例如，若要将 C4001 和 C4010 视为错误，请输入**4001; 4010**。 选择 **"确定"** 保存更改并返回到 "**属性页**" 对话框。

1. 若要设置 **/wo**选项，请选择 "**配置属性**" > **C++ C/**  > "**命令行**" 属性页。 在 "**附加选项**" 框中输入编译器选项。

1. 选择“确定”以保存更改。

### <a name="to-set-the-compiler-option-programmatically"></a>以编程方式设置编译器选项

- 请参阅<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WarningLevel%2A>、<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WarnAsError%2A>、<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DisableSpecificWarnings%2A>和<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另请参阅

[MSVC 编译器选项](compiler-options.md)\
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)

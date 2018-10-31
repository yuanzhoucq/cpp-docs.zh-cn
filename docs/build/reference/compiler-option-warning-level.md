---
title: /w、 /W0、 /W1、 /W2、 /W3、 / w4、 /w1、 /w2、 /w3、 /w4、 /Wall、 /wd、 / /we、 /wo、 /Wv、 /WX （警告级别）
ms.date: 01/31/2018
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
ms.openlocfilehash: 4842e845013bf69a7bc033ba7b6abf5ecc7d5079
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50441738"
---
# <a name="w-w0-w1-w2-w3-w4-w1-w2-w3-w4-wall-wd-we-wo-wv-wx-warning-level"></a>/w、 /W0、 /W1、 /W2、 /W3、 / w4、 /w1、 /w2、 /w3、 /w4、 /Wall、 /wd、 / /we、 /wo、 /Wv、 /WX （警告级别）

指定编译器如何为给定编译生成警告。

## <a name="syntax"></a>语法

> **/w**
>  **/W0**
>  **/W1**
>  **/W2**
>  **/W3** 
>  **/W4**
>  **/wall**
>  **/Wv**\[**:**_版本_] **/WX**
>  **/w1**_警告_
>  **/w2** _警告_
>  **/w3**_警告_
>  **/w4**_警告_
>  **/wd**_警告_
>  **/we**_警告_
>  **/wo**_警告_

## <a name="remarks"></a>备注

警告选项指定为显示和整个编译警告行为的编译器警告。

下表中介绍的警告选项和相关自变量：

|选项|描述|
------------|-----------------|
|**/w**|禁止显示所有编译器警告。|
|**/W0**<br /><br /> **/W1**<br /><br /> **/W2**<br /><br /> **/W3**<br /><br /> **/W4**|指定要由编译器生成的警告级别。 有效的警告等级 0 到 4 范围内：<br />**/ W0**禁止显示所有警告。 这相当于 **/w**。<br />**/ W1**显示等级 1 （严重） 警告。 **/ W1**是命令行编译器中的默认设置。<br />**/ W2**显示等级 1 和等级 2 （明显） 警告。<br />**/ W3**显示级别 1、 2 级和等级 3 （生产质量） 警告。 **/ W3**是在 IDE 中的默认设置。<br />**/ W4**显示级别 1，级别 2 和等级 3 警告以及在所有级别 4 （信息性） 的警告，默认情况下不会关闭。 我们建议使用此选项可以提供类似于 lint 的警告。 对于新项目，它可能是最好使用 **/w4**在所有编译; 这将确保尽可能少的可能的硬查找代码缺陷。|
|**/Wall**|显示所有情况下显示的警告 **/w4**和其他警告的 **/w4**不包括 — 例如，默认情况下处于关闭状态的警告。 有关详细信息，请参阅[编译器警告，是 Off By Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。|
|**/Wv**\[**:**_version_]|显示仅在编译器版本中引入的警告*版本*及更早版本。 禁止显示代码中的新警告时迁移到较新版本的编译器，并修复它们保持您现有的生成过程，您可以使用此选项。 可选参数*版本*采用形式*nn*[。*mm*[。*和*]] 其中*nn*是主要版本号*mm*是可选的次要版本编号和*和*是可选的生成数编译器。 例如，使用 */Wv:17*若要显示在 Visual Studio 2012 （即，任何版本 17 的主要版本号的编译器） 或更早版本，引入的警告，但取消 Visual Studio 2013 （主要版本中引入的警告18） 及更高版本。 默认情况下 **/Wv**使用取消当前的编译器版本号，并不将任何警告。 有关哪些警告所抑制的编译器版本的信息，请参阅[由编译器版本的编译器警告](../../error-messages/compiler-warnings/compiler-warnings-by-compiler-version.md)。|
|**/WX**|将所有编译器警告视为错误。 对于新项目，它可能是最好使用 **/WX**在所有编译; 中对所有警告进行都解析可确保最少的可能的硬查找代码缺陷。<br /><br /> 链接器还有 **/WX**选项。 有关详细信息，请参阅 [/WX（将链接器警告视为错误）](../../build/reference/wx-treat-linker-warnings-as-errors.md)。|
|**/w1**_nnnn_<br /><br /> **/w2**_nnnn_<br /><br /> **/w3**_nnnn_<br /><br /> **/ w4**_nnnn_|为指定的警告数量设置警告等级_nnnn_。 这样可以设置特定的警告级别时更改该警告的编译器行为。 可以使用这些选项与其他警告选项结合使用，以强制执行的警告，而不是默认的 Visual Studio 提供自己的编码标准。<br /><br /> 例如， **/w34326**使 C4326 生成为级别 3 警告而不是 1 级。 如果在编译时通过使用两 **/w34326**选项和 **/W2**选项时，警告 C4326 不生成。|
|**/wd**_nnnn_|禁止显示由指定的编译器警告_nnnn_。<br /><br /> 例如， **/wd4326**禁止显示编译器警告 C4326。|
|**/we**_nnnn_|将指定的编译器警告_nnnn_为错误。<br /><br /> 例如， **/we4326**导致警告 C4326 被视为编译器错误编号。|
|**/wo**_nnnn_|编译器警告，它指定的报表_nnnn_仅一次。<br /><br /> 例如， **/wo4326**会导致警告 C4326 报告仅一次，第一次它遇到由编译器。|

如果您使用的任何警告选项时使用创建预编译标头[/Yc](../../build/reference/yc-create-precompiled-header-file.md)选项，任何使用使用预编译标头[/Yu](../../build/reference/yu-use-precompiled-header-file.md)选项将使这些相同的警告选项生效电子邮件了。 您可以重写预编译标头中使用命令行上的另一个警告选项设置的警告选项。

可以使用[#pragma 警告](../../preprocessor/warning.md)指令来控制级别的警告，它在编译时报告在特定源文件中。

在源代码中的警告杂注指令不受 **/w**选项。

[生成错误文档](../../error-messages/compiler-errors-1/c-cpp-build-errors.md)描述警告和警告级别，并指示为何某些语句可能按你期望的那样不编译。

### <a name="to-set-the-compiler-options-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 若要设置 **/W0**， **/W1**， **/W2**， **/W3**， **/w4**， **/wall**m **/Wv**， **/WX**或 **/WX-** 选项中，选择**配置属性** > **C /C + +** > **常规**属性页。

   - 若要设置 **/W0**， **/W1**， **/W2**， **/W3**， **/w4**，或 **/wall**选项，修改**警告等级**属性。

   - 若要设置 **/WX**或 **/WX-** 选项，修改**将警告视为错误**属性。

   - 若要设置的版本 **/Wv**选项，请输入中的编译器版本号**警告版本**属性。

1. 若要设置 **/wd**或 **/we**选项中，选择**配置属性** > **C/c + +**  >  **高级**属性页。

   - 若要设置 **/wd**选项，选中**禁用特定警告**属性下拉列表控件，然后选择**编辑**。 在编辑框中**禁用特定警告**对话框中，输入警告编号。 若要输入多个警告，分隔各个值之间用分号 (**;**)。 例如，若要禁用 C4001 和 C4010，输入**4001; 4010**。 选择**确定**以保存所做的更改并返回到**属性页**对话框。

   - 若要设置 **/we**选项，选择**特定警告视为错误**属性下拉列表控件，然后选择**编辑**。 在编辑框中**特定警告视为错误**对话框中，输入警告编号。 若要输入多个警告，分隔各个值之间用分号 (**;**)。 例如，若要将 C4001 和 C4010 视为错误，请输入**4001; 4010**。 选择**确定**以保存所做的更改并返回到**属性页**对话框。

1. 若要设置 **/wo**选项，选中**配置属性** > **C/c + +** > **命令行**属性页。 输入中的编译器选项**其他选项**框。

1. 选择**确定**以保存所做的更改。

### <a name="to-set-the-compiler-option-programmatically"></a>以编程方式设置编译器选项

- 请参阅<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WarningLevel%2A>、<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WarnAsError%2A>、<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DisableSpecificWarnings%2A>和<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)

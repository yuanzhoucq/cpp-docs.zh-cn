---
title: "-w，-W0，-W1、-W2，-W3、-W4，-w1，-w2，-w3，-w4，-Wall、-wd，-我们-wo，-西弗吉尼亚州，-WX （警告级别） |Microsoft 文档"
ms.custom: 
ms.date: 01/31/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ee6ac53bd92873279c08dc7458114612d00ff791
ms.sourcegitcommit: a5a69d2dc3513261e9e28320e4e067aaf40d2ef2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/21/2018
---
# <a name="w-w0-w1-w2-w3-w4-w1-w2-w3-w4-wall-wd-we-wo-wv-wx-warning-level"></a>/w、 /w0 取消显示、 /W1、 /W2、 /W3、 /W4、 /w1、 /w2、 /w3、 /w4，/Wall、 /wd，/ 我们 /wo，/Wv，/WX （警告级别）

指定编译器如何为给定编译生成警告。

## <a name="syntax"></a>语法

> **/w**  
> **/W0**  
> **/W1**  
> **/W2**  
> **/W3**  
> **/W4**  
> **/Wall**  
> **/Wv**\[**:**_version_]  
> **/WX**  
> **/w1**_warning_  
> **/w2**_warning_  
> **/w3**_warning_  
> **/w4**_warning_  
> **/wd**_warning_  
> **/we**_warning_  
> **/wo**_warning_  

## <a name="remarks"></a>备注

警告选项指定的编译器警告记录到显示和整个编译警告行为。

下表中描述了警告选项和相关的自变量：

|选项|描述|
------------|-----------------|
|**/w**|禁止显示所有的编译器警告。|
|**/W0**<br /><br /> **/W1**<br /><br /> **/W2**<br /><br /> **/W3**<br /><br /> **/W4**|指定要由编译器生成的警告级别。 有效的警告等级范围在 0 到 4:<br />**/ W0**禁止显示所有警告。 这相当于**/w**。<br />**/W1**显示级别 1 （严重） 的警告。 **/W1**是命令行编译器中的默认设置。<br />**/ W2**显示级别 1 和等级 2 （重要） 的警告。<br />**/ W3**显示级别 1、 级别 2 和等级 3 （生产质量） 警告。 **/ W3**是在 IDE 中的默认设置。<br />**/W4**显示级别 1，级别 2，以及级别 3 警告，以及所有级别 4 （信息） 的警告，默认情况下关闭不状态。 我们建议使用此选项以提供链接形式的警告。 对于新项目，它可能是最好使用**/W4**在所有编译; 中，这将确保最大程度地减少可能的硬查找代码缺陷。|
|**/Wall**|显示所有警告显示**/W4**和所有其他警告， **/W4**不包括-例如，默认情况下处于关闭状态的警告。 有关详细信息，请参阅[编译器警告，将关闭默认](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。|
|**/Wv**\[**:**_version_]|显示仅在编译器版本中引入的警告*版本*及更早版本。 若要禁止显示代码中的新警告，当你迁移到较新版本的编译器，和若要修复它们时保持现有的生成过程，你可以使用此选项。 可选参数*版本*采用的形式 *nn* [。*mm*[。*和*]] 其中 *nn* 是主要的版本号， *mm*是可选的次要版本数和*和*是编译器的可选内部版本号。 例如，使用*/Wv:17*显示警告引入在 Visual Studio 2012 （即，任何 17 的主要版本号的编译器的版本） 或更早版本，但禁止显示在 Visual Studio 2013 （主版本中引入的警告18） 及更高版本。 默认情况下， **/Wv**使用当前的编译器版本号，并不会出现警告将被抑制。 有关哪些警告所抑制的编译器版本的信息，请参阅[按编译器版本的编译器警告](../../error-messages/compiler-warnings/compiler-warnings-by-compiler-version.md)。|
|**/WX**|将所有编译器警告视为错误。 对于新项目，它可能是最好使用**/WX**在所有编译; 解决所有警告确保最大程度地减少可能的硬查找代码缺陷。<br /><br /> 链接器还有**/WX**选项。 有关详细信息，请参阅 [/WX（将链接器警告视为错误）](../../build/reference/wx-treat-linker-warnings-as-errors.md)。|
|**/w1**_nnnn_<br /><br /> **/w2**_nnnn_<br /><br /> **/w3**_nnnn_<br /><br /> **/w4**_nnnn_|为指定的警告数设置的警告级别 _nnnn_ 。 这允许您设置特定的警告级别时更改该警告的编译器行为。 可以使用这些选项与其他警告选项结合使用，以强制执行自己的编码的警告，而不是默认的 Visual Studio 提供的标准。<br /><br /> 例如， **/w34326**使 C4326 生成为级别 3 警告而不是第 1 级。 如果通过同时使用编译**/w34326**选项和**/W2**选项，警告 C4326 不生成。|
|**/wd**_nnnn_|禁止显示由指定的编译器警告 _nnnn_ 。<br /><br /> 例如， **/wd4326**禁止显示编译器警告 C4326。|
|**/we**_nnnn_|将指定的编译器警告 _nnnn_ 视为错误。<br /><br /> 例如， **/we4326**导致 C4326 由编译器视为错误的警告编号。|
|**/wo**_nnnn_|编译器警告指定的报表 _nnnn_ 仅一次。<br /><br /> 例如， **/wo4326**警告 C4326 报告仅一次的原因，第一次它遇到的编译器。|

如果通过使用创建预编译标头时，会使用的任何警告选项[/Yc](../../build/reference/yc-create-precompiled-header-file.md)选项，任何使用使用预编译标头[/Yu](../../build/reference/yu-use-precompiled-header-file.md)选项将导致这些相同的警告选项生效试。 你可以重写预编译标头中设置通过使用命令行上的另一个警告选项的警告选项。

你可以使用[#pragma 警告](../../preprocessor/warning.md)指令来控制的警告级别在编译时报告在特定源文件中。

在源代码中的警告杂注指令不会受到**/w**选项。

[生成错误文档](../../error-messages/compiler-errors-1/c-cpp-build-errors.md)描述警告和警告级别，并指明为何某些语句可能不会编译按你期望的那样。

### <a name="to-set-the-compiler-options-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 若要设置**/w0 取消显示**， **/W1**， **/W2**， **/W3**， **/W4**， **/wall**m**/Wv**， **/WX**或**/WX-**选项中，选择**配置属性** > **C /C + +** > **常规**属性页。

   - 若要设置**/w0 取消显示**， **/W1**， **/W2**， **/W3**， **/W4**，或**/wall**选项，修改**警告级别**属性。

   - 若要设置**/WX**或**/WX-**的选项，将修改**将警告视为错误**属性。

   - 若要设置的版本**/Wv**选项，请输入中的编译器版本号**警告版本**属性。

1. 若要设置**/wd**或**/we**选项中，选择**配置属性** > **C/c + +**  >  **高级**属性页。

   - 若要设置**/wd**选项中，选择**禁用特定警告**属性下拉列表控件中，然后选择**编辑**。 中的编辑框中**禁用特定警告**对话框中，输入警告编号。 若要输入多个警告，分隔各个值之间用分号 (**;**)。 例如，若要禁用 C4001 和 C4010，输入**4001; 4010**。 选择**确定**以保存所做的更改并返回到**属性页**对话框。

   - 若要设置**/we**选项，选择**将特定的警告视为错误**属性下拉列表控件中，然后选择**编辑**。 中的编辑框中**将特定的警告视为错误**对话框中，输入警告编号。 若要输入多个警告，分隔各个值之间用分号 (**;**)。 例如，若要将 C4001 和 C4010 视为错误，请输入**4001; 4010**。 选择**确定**以保存所做的更改并返回到**属性页**对话框。

1. 若要设置**/wo**选项中，选择**配置属性** > **C/c + +** > **命令行**属性页。 输入中的编译器选项**其他选项**框。

1. 选择**确定**以保存所做的更改。

### <a name="to-set-the-compiler-option-programmatically"></a>以编程方式设置编译器选项

- 请参阅<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WarningLevel%2A>、<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WarnAsError%2A>、<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DisableSpecificWarnings%2A>和<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[编译器选项](../../build/reference/compiler-options.md)  
[设置编译器选项](../../build/reference/setting-compiler-options.md)  

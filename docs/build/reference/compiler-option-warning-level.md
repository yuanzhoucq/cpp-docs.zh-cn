---
title: "-w，-W0，-W1、-W2，-W3、-W4，-w1，-w2，-w3，-w4，-Wall、-wd，-我们-wo，-西弗吉尼亚州，-WX （警告级别） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
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
dev_langs: C++
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
ms.assetid: d6bc7bf5-c754-4879-909c-8e3a67e2629f
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5504c3d726feda499fb4b63f68d7784291308694
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="w-w0-w1-w2-w3-w4-w1-w2-w3-w4-wall-wd-we-wo-wv-wx-warning-level"></a>/w、 /w0 取消显示、 /W1、 /W2、 /W3、 /W4、 /w1、 /w2、 /w3、 /w4，/Wall、 /wd，/ 我们 /wo，/Wv，/WX （警告级别）
指定编译器如何为给定编译生成警告。  
  
## <a name="syntax"></a>语法  
  
```  
/w  
/W0  
/W1  
/W2  
/W3  
/W4  
/Wall  
/Wv[<version>]  
/WX  
/w1<warning>   
/w2<warning>   
/w3<warning>   
/w4<warning>   
/wd<warning>   
/we<warning>   
/wo<warning>  
```  
  
## <a name="remarks"></a>备注  
 警告选项指定的编译器警告记录到显示和整个编译警告行为。  
  
 下表中描述了警告选项和相关的自变量：  
  
|选项|描述|  
|------------|-----------------|  
|**/w**|禁止显示所有的编译器警告。|  
|**/W0**<br /><br /> **/W1**<br /><br /> **/W2**<br /><br /> **/W3**<br /><br /> **/W4**|指定要由编译器生成的警告级别。 有效的警告等级范围在 0 到 4:<br /><br /> -   **/ W0**禁止显示所有警告。<br />-   **/W1**显示级别 1 （严重） 的警告。 **/W1**是默认设置。<br />-   **/ W2**显示级别 1 和等级 2 （重要） 的警告。<br />-   **/ W3**显示级别 1、 级别 2 和等级 3 （生产质量） 警告。<br />-   **/W4**显示级别 1，级别 2，以及级别 3 警告，以及所有级别 4 （信息） 的警告，默认情况下关闭不状态。 建议您仅使用此选项来提供链接形式的警告。 但是，对于新项目时，它可能最好使用**/W4**在所有编译; 中，这将确保最大程度地减少可能的硬查找代码缺陷。|  
|**/ 墙**|显示所有警告显示**/W4**和所有其他警告， **/W4**不包括-例如，默认情况下处于关闭状态的警告。 有关详细信息，请参阅[编译器警告，将关闭默认](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。|  
|**/Wv**`:version`|禁止显示警告比新的编译器版本中引入`version`。 你可以使用此选项，以确定是否有新的警告时使用较旧版本的编译器，没有收到警告编译的代码中并暂时取消你的生成过程从新的警告时修复它们。 可选参数`version`采用的形式`nn`[。`mm`[.`bbbbb`]] 其中`nn`是主要的版本号，`mm`是可选的次要版本数和`bbbbb`是可选的编译器的版本号。 例如，使用`/Wv:17.00.00000`来禁止显示警告引入 Visual c + + 2012年及更高版本。 默认情况下， **/Wv**使用当前的编译器版本号，并不会出现警告将被抑制。 有关哪些警告所抑制的编译器版本的信息，请参阅[按编译器版本的编译器警告](../..//error-messages/compiler-warnings/compiler-warnings-by-compiler-version.md)。|  
|**/WX**|将所有的编译器警告视为错误。 对于新项目，它可能是最好使用**/WX**在所有编译; 解决所有警告确保最大程度地减少可能的硬查找代码缺陷。<br /><br /> 链接器还有**/WX**选项。 有关详细信息，请参阅 [/WX（将链接器警告视为错误）](../../build/reference/wx-treat-linker-warnings-as-errors.md)。|  
|**/w1**`n`<br /><br /> **/w2**`n`<br /><br /> **/w3**`n`<br /><br /> **/w4**`n`|为指定的警告数设置的警告级别`n`。 这允许您设置特定的警告级别时更改该警告的编译器行为。 可以使用这些选项与其他警告选项结合使用，以强制执行自己的编码的警告，而不是默认的 Visual Studio 提供的标准。<br /><br /> 例如，`/w34326`使 C4326 生成为级别 3 警告而不是第 1 级。 如果通过同时使用编译`/w34326`选项和`/W2`选项，警告 C4326 不生成。|  
|**/wd**`n`|禁止显示由指定的编译器警告`n`。<br /><br /> 例如，`/wd4326`禁止显示编译器警告 C4326。|  
|**/we**`n`|将指定的编译器警告`n`视为错误。<br /><br /> 例如，`/we4326`导致 C4326 由编译器视为错误的警告编号。|  
|**/wo**`n`|编译器警告指定的报表`n`仅一次。<br /><br /> 例如，`/wo4326`警告 C4326 报告仅一次的原因，第一次它遇到的编译器。|  
  
 如果通过使用创建预编译标头时，会使用的任何警告选项[/Yc](../../build/reference/yc-create-precompiled-header-file.md)选项，任何使用使用预编译标头[/Yu](../../build/reference/yu-use-precompiled-header-file.md)选项将导致这些相同的警告选项生效试。 你可以重写预编译标头中设置通过使用命令行上的另一个警告选项的警告选项。  
  
 你可以使用[#pragma 警告](../../preprocessor/warning.md)指令来控制的警告级别在编译时报告在特定源文件中。  
  
 在源代码中的杂注警告指令不会受到**/w**选项。  
  
 [生成错误文档](../../error-messages/compiler-errors-1/c-cpp-build-errors.md)描述警告和警告级别，并指明为何某些语句可能不会编译按你期望的那样。  
  
### <a name="to-set-the-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置编译器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  选择**C/c + +**。  
  
3.  上**常规**属性页上，修改**警告级别**或**将警告视为错误**属性。  
  
4.  上**高级**属性页上，修改**禁用特定警告**属性。  
  
5.  剩余的选项，在**命令行**属性页上，键入中的编译器选项**其他选项**框。  
  
### <a name="to-set-the-compiler-option-programmatically"></a>以编程方式设置编译器选项  
  
-   请参阅<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WarningLevel%2A>、<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WarnAsError%2A>、<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DisableSpecificWarnings%2A>和<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## <a name="see-also"></a>另请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)
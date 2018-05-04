---
title: -Yd （将调试信息放在对象文件中） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /yd
dev_langs:
- C++
helpviewer_keywords:
- /Yd compiler option [C++]
- -Yd compiler option [C++]
- debugging [C++], debug information files
- Yd compiler option [C++]
ms.assetid: c5a699fe-65ce-461e-964c-7f5eb2a8320a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 39b03b0faf975caba8c5a287c88afcdf53f7a71f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="yd-place-debug-information-in-object-file"></a>/Yd（将调试信息放在对象文件中）
从的预编译标头 (.pch) 文件一起使用时创建完成调试在所有对象文件的信息的进度进行[/Yc](../../build/reference/yc-create-precompiled-header-file.md)和[/Z7](../../build/reference/z7-zi-zi-debug-information-format.md)选项。 已否决。  
  
## <a name="syntax"></a>语法  
  
```  
/Yd  
```  
  
## <a name="remarks"></a>备注  
 **/Yd**已弃用;[!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)]现在支持多个对象写入单个.pdb 文件，使用 **/Zi**相反。 不推荐使用的编译器选项的列表，请参阅**已弃用并删除的编译器选项**中[按类别列出的编译器选项](../../build/reference/compiler-options-listed-by-category.md)。  
  
 除非你需要将分发库包含调试信息，请使用[/Zi](../../build/reference/z7-zi-zi-debug-information-format.md)选项而非 **/Z7**和 **/Yd**。  
  
 将完整的调试信息存储在每个.obj 文件是仅需分发包含调试信息的库。 它将减慢编译并需要大量的磁盘空间。 当 **/Yc**和 **/Z7**使用不带 **/Yd**，编译器将创建从.pch 文件的第一个.obj 文件中存储常见的调试信息。 编译器不会插入到.obj 文件，随后从.pch 文件; 创建此信息它将插入的信息的交叉引用。 无论多少.obj 文件中使用.pch 文件，只有一个.obj 文件包含常见的调试信息。  
  
 虽然此默认行为会更快地生成时间和降低磁盘空间要求，当它并不需要少量更改需要重新生成包含常见的调试信息的.obj 文件。 在这种情况下，编译器必须重新生成包含对原始的.obj 文件的交叉引用的所有.obj 文件。 此外，如果不同的项目中使用常见的.pch 文件，依赖于对单个.obj 文件的交叉引用是困难。  
  
 预编译标头的详细信息，请参阅：  
  
-   [/Y（预编译标头）](../../build/reference/y-precompiled-headers.md)  
  
-   [创建预编译标头文件](../../build/reference/creating-precompiled-header-files.md)  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击 **“C/C++”** 文件夹。  
  
3.  点击“命令行”  属性页。  
  
4.  在 **“附加选项”** 框中键入编译器选项。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## <a name="examples"></a>示例  
 假设你有两个基本文件，F.cpp 和 G.cpp，每个包含这些 **#include**语句：  
  
```  
#include "windows.h"  
#include "etc.h"  
```  
  
 以下命令将创建预编译标头文件 ETC.pch 和对象文件 F.obj:  
  
```  
CL /YcETC.H /Z7 F.CPP  
```  
  
 对象文件 F.obj 包括类型和 WINDOWS.h 和 ETC.h 的符号信息 （以及它们包括任何其他标头文件）。 现在你可以使用预编译标头 ETC.pch 编译源文件 G.cpp:  
  
```  
CL /YuETC.H /Z7 G.CPP  
```  
  
 对象文件 G.obj 不包括调试信息的预编译标头，但只引用 F.obj 文件中的信息。 请注意，你必须与 F.obj 文件链接。  
  
 如果你预编译标头不用编译 **/Z7**，你仍然可以在更高版本使用的编译中使用它 **/Z7**。 但是，调试信息放在当前的对象文件中，并且函数和预编译标头中定义的类型的本地符号均不可用于调试器。  
  
## <a name="see-also"></a>请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)
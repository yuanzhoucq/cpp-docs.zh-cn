---
title: -Yc （创建预编译标头文件） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.UsePrecompiledHeader
- /yc
- VC.Project.VCCLWCECompilerTool.PrecompiledHeaderThrough
- VC.Project.VCCLWCECompilerTool.UsePrecompiledHeader
- VC.Project.VCCLCompilerTool.PrecompiledHeaderThrough
dev_langs:
- C++
helpviewer_keywords:
- precompiled header files, creating
- PCH files, creating
- .pch files, creating
- -Yc compiler option [C++]
- /Yc compiler option [C++]
- Yc compiler option [C++]
ms.assetid: 47c2e555-b4f5-46e6-906e-ab5cf21f0678
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 865b5e0fa7039a0b60f524c2f13a367569757d92
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="yc-create-precompiled-header-file"></a>/Yc（创建预编译标头文件）
指示编译器创建表示在某个特定点的编译状态的预编译标头 (.pch) 文件。  
  
## <a name="syntax"></a>语法  
  
> __/Yc__
> __/Yc__*filename*  
  
  
## <a name="arguments"></a>自变量  
*filename*  
 指定的标头 (.h) 文件。 当使用此参数时，编译器将编译所有代码，包括.h 文件。  
  
## <a name="remarks"></a>备注  
 当**/Yc**指定不带参数，则编译器将编译所有代码，直至末尾的基的源文件，或中的基文件的点到其中[hdrstop](../../preprocessor/hdrstop.md)指令时发生。 生成的.pch 文件作为基本源文件具有相同的基名称，除非您指定不同的文件名称使用**hdrstop**杂注或**/Fp**选项。  
  
 预编译的代码替换为与指定的文件的基名称创建名称保存在文件**/Yc**选项且扩展名为.pch。 你还可以使用[/Fp （名称。Pch 文件）](../../build/reference/fp-name-dot-pch-file.md)选项以指定预编译标头文件的名称。  
  
 如果你使用__/Yc__*filename*，编译器将编译所有代码，随后用于为指定的文件包括[/Yu （使用预编译标头文件）](../../build/reference/yu-use-precompiled-header-file.md)选项。  
  
 如果选项__/Yc__*filename*和__/Yu__*filename*出现在相同的命令行和两个引用，或暗示的相同的文件名称，__/Yc__*filename*优先。 此功能简化了生成文件的写入。  
  
 预编译标头的详细信息，请参阅：  
  
-   [/Y （预编译标头）](../../build/reference/y-precompiled-headers.md)  
  
-   [创建预编译标头文件](../../build/reference/creating-precompiled-header-files.md)  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  选择的.cpp 文件。 .Cpp 文件必须 #include 包含预编译标头信息的.h 文件。 项目的**/Yc**设置可以在文件级别被覆盖。  
  
2.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
3.  打开**配置属性**， **C/c + +**，**预编译标头**属性页。  
  
4.  修改**预编译标头**属性。  
  
5.  若要设置文件名，修改**预编译标头文件**属性。
  
### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PrecompiledHeaderThrough%2A>和<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UsePrecompiledHeader%2A>。  
  
## <a name="example"></a>示例  
 考虑下列代码：  
  
```cpp  
// prog.cpp
// compile with: cl /c /Ycmyapp.h prog.cpp
#include <afxwin.h>   // Include header for class library  
#include "resource.h" // Include resource definitions  
#include "myapp.h"    // Include information specific to this app  
// ...  
```  
  
当使用命令编译此代码`CL /YcMYAPP.H PROG.CPP`、 编译器将保存的所有预处理步骤为 AFXWIN.h，RESOURCE.h，以及在预编译标头文件中的 MYAPP.h 调用 MYAPP.pch。  
  
## <a name="see-also"></a>请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)[创建预编译标头文件](../../build/reference/creating-precompiled-header-files.md)
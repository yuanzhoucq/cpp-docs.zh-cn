---
title: -Yu （使用预编译标头文件） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /yu
dev_langs:
- C++
helpviewer_keywords:
- Yu compiler option [C++]
- /Yu compiler option [C++]
- -Yu compiler option [C++]
- PCH files, use existing
- .pch files, use existing
- precompiled header files, use existing
ms.assetid: 24f1bd0e-b624-4296-a17e-d4b53e374e1f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d115017e843e7f03455e1eef2b384b3475a1b798
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378712"
---
# <a name="yu-use-precompiled-header-file"></a>/Yu（使用预编译标头文件）
指示编译器使用当前的编译中的现有预编译标头 (.pch) 文件。  
  
## <a name="syntax"></a>语法  
  
```  
/Yu[filename]  
```  
  
## <a name="arguments"></a>自变量  
 *filename*  
 标头文件，它包括在源文件使用的名称 **#include**预处理器指令。  
  
## <a name="remarks"></a>备注  
 该包含文件的名称必须是相同 **/Yc**选项创建预编译标头和任何后续 **/Yu** ，该值指示使用预编译标头的选项。  
  
 有关 **/Yc**，`filename`指定的点的预编译会停止; 编译器预编译所有代码，但`filename`并将其命名生成预编译的头使用的包含文件和扩展的基名称为.pch。  
  
 .Pch 文件必须已经创建使用 **/Yc**。  
  
 编译器将在作为预编译的.h 文件之前发生的所有代码。 它将跳到刚刚场外 **#include**与.h 文件中，关联的指令使用.pch 文件中包含的代码并进行编译之后的所有代码`filename`。  
  
 在命令行中，不允许有空格之间 **/Yu**和`filename`。  
  
 当指定 **/Yu**选项但不带文件名称，源程序必须包含[#pragma hdrstop](../../preprocessor/hdrstop.md)指定预编译标头，.pch 文件的文件名称的杂注。 在这种情况下，编译器将使用预编译标头 （.pch 文件） 由名为[/Fp （名称。Pch 文件）](../../build/reference/fp-name-dot-pch-file.md)。 编译器将跳到该杂注的位置，从指定的杂注，预编译标头文件将还原的已编译的状态并进行编译杂注后面的代码。 如果 **#pragma hdrstop**未指定文件名，编译器将查找具有派生自的基名称的扩展名为.pch 的源文件的名称的文件。 你还可以使用 **/Fp**选项以指定不同的.pch 文件。  
  
 如果指定 **/Yu**选项但不带文件名称，并且无法指定**hdrstop**杂注时，将生成错误消息和编译不成功。  
  
 如果 **/Yc** `filename`和 **/Yu** `filename`选项出现在相同的命令行上，并且引用相同的文件名， **/Yc** `filename`采用优先级，最多预编译所有代码和包括的命名的文件。 此功能简化了生成文件的写入。  
  
 由于.pch 文件包含有关计算机环境的信息以及有关程序的内存地址信息，你应仅使用被创建时所在的计算机上的 pch 文件。  
  
 预编译标头的详细信息，请参阅：  
  
-   [/Y（预编译标头）](../../build/reference/y-precompiled-headers.md)  
  
-   [创建预编译标头文件](../../build/reference/creating-precompiled-header-files.md)  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  指定[/Yc （创建预编译标头文件）](../../build/reference/yc-create-precompiled-header-file.md)项目中的.cpp 文件。  
  
2.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
3.  单击 **“C/C++”** 文件夹。  
  
4.  单击**预编译标头**属性页。  
  
5.  修改**通过文件创建/使用 PCH**属性或**创建/使用预编译标头**属性。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PrecompiledHeaderThrough%2A>和<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UsePrecompiledHeader%2A>。  
  
## <a name="examples"></a>示例  
 如果以下代码：  
  
```  
#include <afxwin.h>   // Include header for class library  
#include "resource.h" // Include resource definitions  
#include "myapp.h"    // Include information specific to this app  
...  
```  
  
 使用命令行编译`CL /YuMYAPP.H PROG.CPP`，编译器不会处理三个保存在预处理所有三个文件 （和它们可能包含任何文件） 中所涉及的时间从而 include 语句，但 myapp.pch，使用预编译代码。  
  
 你可以使用[/Fp （名称。Pch 文件）](../../build/reference/fp-name-dot-pch-file.md)选项与 **/Yu**选项以指定.pch 文件的名称，如果名称不同于到两个文件名称参数 **/Yc**或源文件，如下所示的基名称以下：  
  
```  
CL /YuMYAPP.H /FpMYPCH.pch PROG.CPP  
```  
  
 此命令指定一个名为 MYPCH.pch 的预编译标头文件。 编译器使用其内容以还原的所有标头文件达 myapp.h 预编译的状态。 由编译器进行编译的代码在 MYAPP.h 之后**包括**语句。  
  
## <a name="see-also"></a>请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)
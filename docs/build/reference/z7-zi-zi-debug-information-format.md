---
title: "-Z7，-Zi，-ZI （调试信息格式） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.DebugInformationFormat
- /zi
- /z7
- VC.Project.VCCLWCECompilerTool.DebugInformationFormat
dev_langs: C++
helpviewer_keywords:
- C7 compatible compiler option [C++]
- -Zl compiler option [C++]
- Debug Information Format compiler option
- ZI compiler option
- -Zi compiler option [C++]
- /ZI compiler option [C++]
- Z7 compiler option [C++]
- debugging [C++], debug information files
- Zi compiler option [C++]
- none compiler option [C++]
- /Zi compiler option [C++]
- program database compiler option [C++]
- full symbolic debugging information
- /Z7 compiler option [C++]
- line numbers only compiler option [C++]
- cl.exe compiler, debugging options
- -Z7 compiler option [C++]
ms.assetid: ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 782420e674d6101f49e2b361c888a8f4b0b4c1ec
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="z7-zi-zi-debug-information-format"></a>/Z7、/Zi、/ZI（调试信息格式）
选择为程序创建的调试信息的类型，并选择是将此信息保存在对象(.obj)文件中，还是保存在程序数据库(PDB)中。  
  
## <a name="syntax"></a>语法  
  
```  
/Z{7|i|I}  
```  
  
## <a name="remarks"></a>备注  
 下表描述了这些选项。  
  
 无  
 不生成任何调试信息，因此编译较快。  
  
 **/Z7**  
 生成包含用于调试器的完整符号调试信息的 .obj 文件。 符号化调试信息包含变量的名称和类型以及函数和行号。 不生成任何 .pdb 文件。  
  
 对于第三方库的分发服务器，不生成 .pdb 文件是一个优点。 但是，在链接阶段和调试期间，用于预编译标头的 .obj 文件是必需的。 如果仅在.pch 对象文件中键入信息 （和任何代码），您还需要使用编译[/Yl （为调试库插入 PCH 引用）](../../build/reference/yl-inject-pch-reference-for-debug-library.md)。  
  
 **/Zi**  
 生成一个程序数据库(PDB)，其中包含供调试器使用的类型信息和符号化调试信息。 符号化调试信息包含变量的名称和类型以及函数和行号。  
  
 **/Zi**不会影响优化。 但是， **/Zi**未表示**/调试**; 请参阅[/DEBUG （生成调试信息）](../../build/reference/debug-generate-debug-info.md)有关详细信息。  
  
 类型信息放置在 .pdb 文件而不是 .obj 文件中。  
  
 你可以使用[/Gm （启用最小重新生成）](../../build/reference/gm-enable-minimal-rebuild.md)与**/Zi**，而**/Gm**编译时不可用**/Z7**。  
  
 使用编译时**/Zi**和**/clr**、<xref:System.Diagnostics.DebuggableAttribute>属性将不会放置在程序集元数据中; 你必须指定它在源代码中，如果你希望。 该特性可影响应用程序的运行时性能。 有关如何产生 Debuggable 特性会影响性能和如何修改对性能的影响的详细信息，请参阅[简化映像到调试](/dotnet/framework/debug-trace-profile/making-an-image-easier-to-debug)。  
  
 **/ZI**  
 采用支持“编辑并继续”功能的格式生成程序数据库(如上所述)。 如果想使用“编辑并继续”调试，则必须使用此选项。 因为大多数优化不使用编辑并继续兼容，所以使用**/ZI**禁用任何`#pragma optimize`在代码中的语句。  
  
 **/ZI**导致[/Gy （启用函数级链接）](../../build/reference/gy-enable-function-level-linking.md)和[/FC （完整路径的源代码文件中诊断）](../../build/reference/fc-full-path-of-source-code-file-in-diagnostics.md)用于你编译。  
  
 **/ZI**与不兼容[/clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
> [!NOTE]
>  **/ZI**选项仅适用于面向 x86 和 x64 处理器的编译器此编译器选项不是面向 ARM 处理器的编译器中可用。  
  
 编译器命名的程序数据库*项目*.pdb。 如果不使用项目文件进行编译，编译器将创建一个名为 VC 数据库*x*0.pdb。 其中*x*是主要版本的[!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)]中使用。 编译器将 PDB 的名称嵌入每个使用此选项创建的 .obj 文件中，从而使调试器了解符号和行号信息的位置。 当使用此选项时，.obj 文件将较小，因为调试信息存储在 .pdb 文件中而不是 .obj 文件中。  
  
 如果从使用此选项编译的对象创建库，则在将库链接到程序时，关联 .pdb 文件必须可用。 因此，如果分发此库，就必须分发 PDB。  
  
 若要创建不使用.pdb 文件包含调试信息的库，你必须选择编译器的 C 7.0 兼容 (**/Z7**) 选项。 如果使用预编译标头选项，则预编译标头和其他源代码的调试信息都放在 PDB 中。 **/Yd**时指定了程序数据库选项，将忽略选项。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击 **“C/C++”** 文件夹。  
  
3.  单击**常规**属性页。  
  
4.  修改**调试信息格式**属性。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项  
  
-   请参阅<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DebugInformationFormat%2A>。  
  
## <a name="see-also"></a>另请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)
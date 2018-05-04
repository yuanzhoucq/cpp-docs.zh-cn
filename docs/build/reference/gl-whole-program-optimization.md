---
title: -GL （全程序优化） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /gl
- VC.Project.VCCLWCECompilerTool.WholeProgramOptimization
dev_langs:
- C++
helpviewer_keywords:
- /GL compiler option [C++]
- whole program optimizations and C++ compiler
- -GL compiler option [C++]
- GL compiler option [C++]
ms.assetid: 09d51e2d-9728-4bd0-b5dc-3b8284aca1d1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ce972b6e7254ad7454f8e8799283588f0fdd5270
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="gl-whole-program-optimization"></a>/GL（全程序优化）
启用全程序优化。  
  
## <a name="syntax"></a>语法  
  
```  
/GL[-]  
```  
  
## <a name="remarks"></a>备注  
 全程序优化使编译器能够在程序中的所有模块上执行优化的信息。 但不进行全程序优化，对执行优化每个模块 （编译单位）。  
  
 全程序优化默认处于关闭状态，并且必须显式启用。 但是，还有可能显式禁用它与 **/gl-隐式**。  
  
 提供有关的所有模块的信息，编译器可以：  
  
-   优化跨函数边界使用寄存器。  
  
-   执行操作更好地跟踪对全局数据，允许加载和存储的数减少的修改。  
  
-   更好地表现的跟踪可能项集的修改通过指针取消引用，减少加载和存储的数字。  
  
-   即使在另一个模块中定义函数模块中函数进行内联。  
  
 .obj 文件生成 **/GL**将不能对作为此类链接器实用程序[EDITBIN](../../build/reference/editbin-reference.md)和[DUMPBIN](../../build/reference/dumpbin-reference.md)。  
  
 如果编译您的程序与 **/GL**和[/c](../../build/reference/c-compile-without-linking.md)，应使用 /LTCG 链接器选项来创建输出文件。  
  
 [/ZI](../../build/reference/z7-zi-zi-debug-information-format.md)不能与使用 **/GL**  
  
 使用生成的文件格式 **/GL**当前版本中可能无法读取后续版本的 Visual c + +。 不应装运组成.obj 文件与生成的.lib 文件 **/GL**除非您愿意为提供的所有版本的 Visual c + + 的.lib 文件副本希望你使用，现在和将来的用户。  
  
 .obj 文件生成 **/GL** ，预编译标头文件不应该用于生成的.lib 文件，除非将生成在同一计算机上链接的.lib 文件 **/GL** .obj 文件。 在链接时，将需要从.obj 文件的预编译的头文件的信息。  
  
 有关可用优化和全程序优化的限制的详细信息，请参阅[/LTCG](../../build/reference/ltcg-link-time-code-generation.md)。  **/GL**还使配置文件引导式的优化可用; 请参阅 /LTCG。  在编译的优化，并且如果你希望从按配置优化订购的函数按配置文件时，你必须使用进行编译[/Gy](../../build/reference/gy-enable-function-level-linking.md)或意味着 /Gy 编译器选项。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项  
  
1.  请参阅[/LTCG （链接时间代码生成）](../../build/reference/ltcg-link-time-code-generation.md)有关如何指定 **/GL**在开发环境中。  
  
### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项  
  
1.  请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WholeProgramOptimization%2A>。  
  
## <a name="see-also"></a>请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)
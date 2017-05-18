---
title: "错误 C1083 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1083
dev_langs:
- C++
helpviewer_keywords:
- C1083
ms.assetid: 97e52df3-e79c-4f85-8f1e-bbd1057d55e7
caps.latest.revision: 23
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: bb94e24657d16b2a3eda3a770c2b6ae734c6006f
ms.openlocfilehash: bbc5e1f78ca1ea15e65fdd76b7ecd2ea0e195b00
ms.contentlocale: zh-cn
ms.lasthandoff: 04/12/2017

---
# <a name="fatal-error-c1083"></a>错误 C1083
无法打开 filetype 文件:“file”: message  
  
 编译器在找不到文件时会生成 C1083 错误。 下面是编译器生成此错误的常见原因。  
  
 **指定的文件名称不正确**  
  
 文件名可能键入有误。 例如，  
  
```cpp  
#include <algorithms.h>  
```  
  
 可能找不到你想要的文件。 没有的 c + + 标准库头文件名为 algorithms 没有.h 文件扩展名。 通过此 `include` 指令找不到该文件。 若要修复此问题，请验证输入的文件名是否正确。  
  
 某些 C 运行库标头位于标准包含目录的子目录中。 例如，若要包含 sys\types.h，则必须将 sys 子目录名称包含在包含指令中的：  
  
 `#include <sys\types.h>`  
  
 **在编译器搜索路径中未包括的文件**  
  
 此编译器无法使用 `include` 或 `import` 指令指示的搜索规则找到该文件。 例如，使用引号括起的头文件名  
  
 `#include "myincludefile.h"`  
  
 告知编译器先在包含源文件的相同目录中查找该文件，然后在生成环境指定的其他位置查找。 如果引号包含绝对路径，则编译器仅在该位置查找文件。 如果引号包含相对路径，则编译器在相对于源目录的目录中查找文件。 如果名称使用尖括号括起，  
  
 `#include <stdio.h>`  
  
 编译器遵循生成环境中，定义的搜索路径**/I**编译器选项， **/X**编译器选项和**包括**环境变量。 有关详细信息，包括有关使用查找的文件的搜索顺序的特定详细信息，请参阅[#include 指令 （C/c + +）](../../preprocessor/hash-include-directive-c-cpp.md)和[#import 指令](../../preprocessor/hash-import-directive-cpp.md)。  
  
 甚至当标头文件列出在**解决方案资源管理器**作为项目的一部分，这些文件仅由编译器时发现它们通过引用`include`或`import`指令并且位于目录搜索路径。 不同种类的生成可能会使用不同搜索路径。 **/X**编译器选项可以用于从包含文件搜索路径中排除目录。 这样不同的生成就可以使用具有相同名称、但保存在不同目录中的不同包含文件。 这是使用预处理器命令进行的条件编译的替代方法。 有关详细信息**/X**编译器选项，请参阅[/X （忽略标准包括路径）](../../build/reference/x-ignore-standard-include-paths.md)。  
  
 在命令行中调用编译器时，通常会使用环境变量来指定搜索路径。 如果通过描述的搜索路径**包括**环境变量设置不正确，则会生成 C1083 错误。 有关如何使用环境变量的详细信息，请参阅[如何︰ 在生成中使用环境变量](/visualstudio/msbuild/how-to-use-environment-variables-in-a-build)。  
  
 若要修复此问题，请更改编译器用于搜索包含或导入的文件的路径。 新项目使用默认搜索路径。 您可能必须修改路径才能为项目添加目录。 如果在命令行上进行编译，设置**包括**环境变量或**/I**编译器选项来指定文件的路径。 若要在 Visual Studio 中设置包含目录路径，请打开项目的**属性页**对话框框中，展开**配置属性**和**VC + + 目录**，然后编辑**包含目录**值。 有关 Visual Studio 中的编译器搜索的每个用户和每个项目目录的详细信息，请参阅[VC + + 目录属性页](../../ide/vcpp-directories-property-page.md)。 有关详细信息**/I**编译器选项，请参阅[/I （附加包含目录）](../../build/reference/i-additional-include-directories.md)。  
  
 **是包含了错误版本的文件名称**  
  
 C1083 错误还可能指示包含了错误版本的文件。 例如，某个生成可能包含错误版本的文件，该文件的 `include` 指令针对不是用于该生成的头文件。 当找不到头文件时，编译器会生成 C1083 错误。 此问题的解决方法是使用正确的文件，而不是向生成添加头文件或目录。  
  
 **不是尚未预编译预编译标头**  
  
 当项目配置为使用预编译标头时，必须创建相关 .pch 文件，以便可以编译使用头内容的文件。 例如，会在项目目录中为新 MFC 项目自动创建 stdafx.cpp 文件。 先编译该文件以创建预编译的头文件。 （在典型生成过程设计中，这是自动完成的。）有关详细信息，请参阅[创建预编译标头文件](../../build/reference/creating-precompiled-header-files.md)。  
  
 **其他原因**  
  
-   该文件使用托管的代码，但是编译器选项**/clr**未指定。 有关详细信息，请参阅 [/clr（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
-   对文件进行编译使用不同**/ 分析**比使用预编译头编译器选项设置。 (当预编译一个项目的标头时，全都应使用相同**/ 分析**设置。)有关详细信息，请参阅 [/analyze（代码分析）](../../build/reference/analyze-code-analysis.md)。  
  
-   文件、目录或磁盘为只读。  
  
-   未授予文件或目录的访问权限。  
  
-   文件句柄不足。 关闭一些应用程序，然后重新编译。 这种情况一般不常见。 但是，在物理内存有限的计算机上生成大型项目时，可能会发生这种情况。  
  
 下面的示例生成 C1083 错误。  
  
```  
// C1083.cpp  
// compile with: /c  
#include "test.h"   // C1083 test.h does not exist  
#include "stdio.h"   // OK  
```  
  
 有关如何生成 C/c + + 项目，在 IDE 中或命令行上的信息和有关设置环境变量的信息，请参阅[生成 C/c + + 程序](../../build/building-c-cpp-programs.md)。
 
 ## <a name="see-also"></a>另请参阅
 [MSBuild 属性](/visualstudio/msbuild/msbuild-properties)

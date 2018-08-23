---
title: -LN （创建 MSIL 模块） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /LN
dev_langs:
- C++
helpviewer_keywords:
- -LN compiler option [C++]
- /LN compiler option [C++]
ms.assetid: 4f38f4f4-3176-4caf-8200-5c7585dc1ed3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1ca6d1933b684cc574bc4e0107b9f3f30364c908
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42609457"
---
# <a name="ln-create-msil-module"></a>/LN（创建 MSIL 模块）
指定不应将程序集清单插入输出文件中。  
  
## <a name="syntax"></a>语法  
  
```  
/LN  
```  
  
## <a name="remarks"></a>备注  
 默认情况下 **/LN**不起作用 （程序集清单插入到输出文件中）。  
  
 当 **/LN**使用，则之一[/clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)还必须使用选项。  
  
 在清单中不具有程序集元数据的托管的程序称为模块。 如果使用编译[/c （编译而无需链接）](../../build/reference/c-compile-without-linking.md)并 **/LN**，指定[/NOASSEMBLY （创建 MSIL 模块）](../../build/reference/noassembly-create-a-msil-module.md)中来创建输出文件的链接器阶段。  
  
 您可能想要创建模块，如果你想要采用的基于组件的方法来生成程序集。  也就是说，可以创作类型，并将其编译到模块。  然后，您可以从一个或多个模块生成程序集。  从模块创建程序集的详细信息，请参阅[用作链接器输入的.netmodule 文件](../../build/reference/netmodule-files-as-linker-input.md)或[Al.exe （程序集链接器）](/dotnet/framework/tools/al-exe-assembly-linker)。  
  
 模块的默认文件扩展名为 .netmodule。  
  
 在 Visual c + + 在 Visual c + + 2005年之前的版本中，模块通过创建 **/clr:noAssembly**。  
  
 Visual C++ 链接器接受 .netmodule 文件作为输入，链接器生成的输出文件将是与输入到链接器的任何 .netmodule 没有运行时依赖关系的程序集或 .netmodule。  有关详细信息，请参阅 [用作链接器输入的 .netmodule 文件](../../build/reference/netmodule-files-as-linker-input.md)。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
-   指定[/NOASSEMBLY （创建 MSIL 模块）](../../build/reference/noassembly-create-a-msil-module.md)中来创建输出文件的链接器阶段。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项  
  
-   不能以编程方式更改此编译器选项。  
  
## <a name="see-also"></a>请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)
---
title: /LN（创建 MSIL 模块）
ms.date: 11/04/2016
f1_keywords:
- /LN
helpviewer_keywords:
- -LN compiler option [C++]
- /LN compiler option [C++]
ms.assetid: 4f38f4f4-3176-4caf-8200-5c7585dc1ed3
ms.openlocfilehash: d8253dacbfa57f84a3eee05ffa0f8f9879f6b009
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536924"
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

- 指定[/NOASSEMBLY （创建 MSIL 模块）](../../build/reference/noassembly-create-a-msil-module.md)中来创建输出文件的链接器阶段。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 不能以编程方式更改此编译器选项。

## <a name="see-also"></a>请参阅

[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)
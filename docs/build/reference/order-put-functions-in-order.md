---
title: 顺序 （按顺序放置函数） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.FunctionOrder
- /order
dev_langs:
- C++
helpviewer_keywords:
- ORDER linker option
- -ORDER linker option
- LINK tool [C++], program optimizing
- /ORDER linker option
- LINK tool [C++], swap tuning
- paging, optimizing
ms.assetid: ecf5eb3e-e404-4e86-9a91-4e5ec157261a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: de9b0fb629a1bf984929ec170f05e25e740e9cd5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378478"
---
# <a name="order-put-functions-in-order"></a>/ORDER（按顺序放置函数）

指定单独打包 (COMDAT) 函数的链接顺序。

## <a name="syntax"></a>语法

>/ 排序: @*filename*

### <a name="parameters"></a>参数

*filename*  
指定 COMDAT 函数的链接顺序的文本文件。

## <a name="remarks"></a>备注

**/Order**编译器选项允许你通过将一个函数调用的函数以及组合优化程序的分页行为。 你还可以分组频繁调用的函数在一起。 这些技巧，称为*交换优化*或*分页优化*，增加在需要时并不需要从磁盘分页时调用的函数是在内存中的概率。

当你将你的源代码编译到的对象文件时，可以告诉编译器将每个函数放入其自己的部分，调用*COMDAT*，通过使用[/Gy （启用函数级链接）](../../build/reference/gy-enable-function-level-linking.md)编译器选项。 **/Order**链接器选项通知链接器将 Comdat 放置到可执行映像中所指定的顺序。

若要指定的 COMDAT 顺序，创建*响应文件*，按名称，每行一个，在你想要放置链接器的顺序列出每个 COMDAT 的文本文件。 将此文件作为名称传递给*filename*参数 **/order**选项。 对于 c + + 函数，COMDAT 的名称是函数名称的修饰的形式。 使用 C 函数的未修饰的名称`main`，并为 c + + 函数声明为`extern "C"`。 函数名称和修饰的名称区分大小写。 修饰名的详细信息，请参阅[修饰名](../../build/reference/decorated-names.md)。 

若要查找你 Comdat 的修饰的名，使用[DUMPBIN](../../build/reference/dumpbin-reference.md)工具的[/符号](../../build/reference/symbols.md)对象文件上的选项。 链接器会自动将添加前下划线 (\_) 到函数名称在响应中的文件，除非名称开头用问号 （？） 或 at 符号 (@)。 例如，如果源文件，example.cpp，包含函数`int cpp_func(int)`，`extern "C" int c_func(int)`和`int main(void)`，该命令`DUMPBIN /SYMBOLS example.obj`列出这些修饰的名：

```Output
...
088 00000000 SECT1A notype ()    External     | ?cpp_func@@YAHH@Z (int __cdecl cpp_func(int))
089 00000000 SECT22 notype ()    External     | _c_func
08A 00000000 SECT24 notype ()    External     | _main
...
```

在这种情况下，指定的名称作为`?cpp_func@@YAHH@Z`， `c_func`，和`main`响应文件中。

如果多个 **/order**选项会显示在链接器选项，指定的最后一个生效。

**/Order**选项禁用增量链接。 你可能会看到链接器警告[LNK4075](../../error-messages/tool-errors/linker-tools-warning-lnk4075.md)时指定此选项，如果启用了增量链接，或如果已指定[/ZI (增量 PDB)](../../build/reference/z7-zi-zi-debug-information-format.md)编译器选项。 若要抑制此警告，可以使用[/incremental: no](../../build/reference/incremental-link-incrementally.md)链接器选项，若要关闭增量链接，并使用[/Zi (生成 PDB)](../../build/reference/z7-zi-zi-debug-information-format.md)编译器选项以生成 PDB，而增量链接。

> [!NOTE]
> 链接无法排序静态函数，因为静态函数名称不是公共符号名称。 当 **/order**指定，则链接器警告[LNK4037](../../error-messages/tool-errors/linker-tools-warning-lnk4037.md)生成为静态或找不到顺序响应文件中的每个符号。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。  

1. 下**配置属性**，打开**链接器**，然后选择**优化**属性页。

1. 修改**函数顺序**属性以包含响应文件的名称。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.FunctionOrder%2A>。

## <a name="see-also"></a>请参阅

[设置链接器选项](../../build/reference/setting-linker-options.md)  
[链接器选项](../../build/reference/linker-options.md)
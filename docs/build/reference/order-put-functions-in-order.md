---
title: /ORDER（按顺序放置函数）
ms.date: 09/05/2018
f1_keywords:
- VC.Project.VCLinkerTool.FunctionOrder
- /order
helpviewer_keywords:
- ORDER linker option
- -ORDER linker option
- LINK tool [C++], program optimizing
- /ORDER linker option
- LINK tool [C++], swap tuning
- paging, optimizing
ms.assetid: ecf5eb3e-e404-4e86-9a91-4e5ec157261a
ms.openlocfilehash: 5429876d9bfae7d8b317d52d69f0b21c720b002a
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57418069"
---
# <a name="order-put-functions-in-order"></a>/ORDER（按顺序放置函数）

指定单独打包 (COMDAT) 函数的链接顺序。

## <a name="syntax"></a>语法

> **/ORDER:\@**<em>文件名</em>

### <a name="parameters"></a>参数

*filename*<br/>
指定 COMDAT 函数的链接顺序的文本文件。

## <a name="remarks"></a>备注

**/O**编译器选项，可通过将一个函数调用的函数以及组合优化程序的分页行为。 也可以一起分组频繁调用的函数。 这些技术，称为*交换优化*或*分页优化*，增加需要和不需要从磁盘中分页时被调用的函数是在内存中的概率。

在你的源代码编译对象文件，可以指示编译器将放入其自己的部分，名为每个函数*COMDAT*，通过使用[/Gy （启用函数级链接）](../../build/reference/gy-enable-function-level-linking.md)编译器选项。 **/O**链接器选项通知链接器将 comdat 放置到可执行映像中所指定的顺序。

若要指定 COMDAT 顺序，请创建*响应文件*，按名称，每行，你希望它们由链接器放置的顺序列出每个 COMDAT 的文本文件。 将为此文件的名称传递*文件名*的参数 **/O**选项。 对于 c + + 函数的 COMDAT 名称是函数名称的修饰的形式。 使用 C 函数的未修饰的名`main`，并为 c + + 函数声明为`extern "C"`。 函数名称和修饰的名是区分大小写。 修饰名的详细信息，请参阅[修饰名](../../build/reference/decorated-names.md)。

若要查找你的 Comdat 的修饰的名，请使用[DUMPBIN](../../build/reference/dumpbin-reference.md)工具的[/ 符号](../../build/reference/symbols.md)上的对象文件的选项。 链接器会自动将前面添加下划线 (**\_**) 函数名称在响应中的文件的名称开头问号除非 (**？**) 或 at 符号 ( **\@**). 例如，如果源文件，example.cpp，包含的函数`int cpp_func(int)`，`extern "C" int c_func(int)`并`int main(void)`，该命令`DUMPBIN /SYMBOLS example.obj`列出了这些修饰的名：

```Output
...
088 00000000 SECT1A notype ()    External     | ?cpp_func@@YAHH@Z (int __cdecl cpp_func(int))
089 00000000 SECT22 notype ()    External     | _c_func
08A 00000000 SECT24 notype ()    External     | _main
...
```

在这种情况下，指定作为名称`?cpp_func@@YAHH@Z`， `c_func`，和`main`响应文件中。

如果多个 **/O**选项将出现在链接器选项，指定的最后一个生效。

**/O**选项禁用增量链接。 你可能会看到链接器警告[LNK4075](../../error-messages/tool-errors/linker-tools-warning-lnk4075.md)时指定此选项，如果启用了增量链接，或如果已指定[/ZI (增量 PDB)](../../build/reference/z7-zi-zi-debug-information-format.md)编译器选项。 若要提示此警告，可以使用[/incremental: no](../../build/reference/incremental-link-incrementally.md)链接器选项将关闭增量链接，并使用[/Zi (生成 PDB)](../../build/reference/z7-zi-zi-debug-information-format.md)编译器选项来生成 PDB，而增量链接。

> [!NOTE]
> 链接不能进行排序的静态函数，因为静态函数名称不是公共符号名称。 当 **/O**指定，则链接器警告[LNK4037](../../error-messages/tool-errors/linker-tools-warning-lnk4037.md)生成为静态或找不到订单响应文件中每个符号。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。

1. 选择**配置属性** > **链接器** > **优化**属性页。

1. 修改**函数顺序**属性以包含响应文件的名称。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.FunctionOrder%2A>。

## <a name="see-also"></a>请参阅

[设置链接器选项](../../build/reference/setting-linker-options.md)<br/>
[链接器选项](../../build/reference/linker-options.md)

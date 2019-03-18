---
title: /TLBOUT（命名 .TLB 文件）
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.TypeLibraryFile
- /tlbout
helpviewer_keywords:
- tlb files, renaming
- TLBOUT linker option
- /TLBOUT linker option
- .tlb files, renaming
- -TLBOUT linker option
ms.assetid: 0df6d078-2e48-46c9-a1a5-02674d85dce8
ms.openlocfilehash: 4e04514933a521bbf9d927fa6b47bacb87896353
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822257"
---
# <a name="tlbout-name-tlb-file"></a>/TLBOUT（命名 .TLB 文件）

```
/TLBOUT:[path\]filename
```

## <a name="arguments"></a>自变量

*path*<br/>
应在其中创建.tlb 文件的绝对或相对路径规范。

*filename*<br/>
指定由 MIDL 编译器创建的.tlb 文件的名称。 假定没有文件扩展名;指定*文件名*.tlb 如果想要具有.tlb 扩展名。

## <a name="remarks"></a>备注

/TLBOUT 选项指定的名称和.tlb 文件的扩展名。

当链接包含的项目时，MSVC 链接器将调用 MIDL 编译器[模块](../../windows/module-cpp.md)属性。

如果未指定 /TLBOUT，.tlb 文件会从其名称[/IDLOUT](idlout-name-midl-output-files.md) *filename*。 如果未指定 /IDLOUT，则将 vc70.tlb 调用.tlb 文件。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[Visual Studio 中的设置 c + + 编译器和生成属性](../working-with-project-properties.md)。

1. 单击**链接器**文件夹。

1. 单击**嵌入的 IDL**属性页。

1. 修改**类型库**属性。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

1. 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TypeLibraryFile%2A>。

## <a name="see-also"></a>请参阅

[MSVC 链接器引用](linking.md)<br/>
[MSVC 链接器选项](linker-options.md)<br/>
[/IGNOREIDL（不将属性处理到 MIDL 中）](ignoreidl-don-t-process-attributes-into-midl.md)<br/>
[/MIDL（指定 MIDL 命令行选项）](midl-specify-midl-command-line-options.md)<br/>
[生成特性化程序](../../windows/building-an-attributed-program.md)

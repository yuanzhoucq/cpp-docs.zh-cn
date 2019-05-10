---
title: /MIDL（指定 MIDL 命令行选项）
ms.date: 09/05/2018
f1_keywords:
- /midl
- VC.Project.VCLinkerTool.MidlCommandFile
helpviewer_keywords:
- -MIDL linker option
- MIDL
- /MIDL linker option
- MIDL linker option
- MIDL, command line options
ms.assetid: 22dc259e-b34c-4ed3-a380-4beb734482c1
ms.openlocfilehash: 584958ac51bdc491ad1bdd16117ecaad6e000ec7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62321067"
---
# <a name="midl-specify-midl-command-line-options"></a>/MIDL（指定 MIDL 命令行选项）

指定 MIDL 命令行选项的响应文件

## <a name="syntax"></a>语法

> **/MIDL:\@**<em>file</em>

## <a name="arguments"></a>自变量

文件<br/>
包含文件的名称[MIDL 命令行选项](/windows/desktop/Midl/general-midl-command-line-syntax)。

## <a name="remarks"></a>备注

必须给定的 IDL 文件转换为 TLB 文件的所有选项*文件*;不能链接器的命令行上指定 MIDL 命令行选项。 如果未指定 /MIDL，MIDL 编译器将调用使用 IDL 文件名称和任何其他选项。

该文件应包含每行一个 MIDL 命令行选项。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置C++Visual Studio 中的编译器和生成属性](../working-with-project-properties.md)。

1. 选择**配置属性** > **链接器** > **嵌入的 IDL**属性页。

1. 修改**MIDL 命令**属性。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MidlCommandFile%2A>。

## <a name="see-also"></a>请参阅

[MSVC 链接器参考](linking.md)<br/>
[MSVC 链接器选项](linker-options.md)<br/>
[/IDLOUT（命名 MIDL 输出文件）](idlout-name-midl-output-files.md)<br/>
[/IGNOREIDL（不将属性处理到 MIDL 中）](ignoreidl-don-t-process-attributes-into-midl.md)<br/>
[/TLBOUT（命名 .TLB 文件）](tlbout-name-dot-tlb-file.md)<br/>
[生成特性化程序](../../windows/building-an-attributed-program.md)

---
title: / USEPROFILE （使用 PGO 数据与 LTCG） |Microsoft 文档
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
f1_keywords:
- USEPROFILE
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b12c2e63d5e65d2528f77852d9466d4161d7cc6a
ms.sourcegitcommit: ee7d74683af7631441c8c7f65ef5ceceaee4a5ee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
---
# <a name="useprofile-run-pgo-in-thread-safe-mode"></a>/ USEPROFILE (在线程安全模式下的运行 PGO)

此链接器选项一起使用[/LTCG (链接时间代码生成](ltcg-link-time-code-generation.md)通知链接器使用按配置优化 (PGO) 定型数据生成。

## <a name="syntax"></a>语法

> **/USEPROFILE**[**:**{**AGGRESSIVE**|**PGD=**_filename_}]

### <a name="arguments"></a>自变量

**AGGRESSIVE**<br/>
此可选参数指定应在优化的代码生成期间使用的主动速度优化。

**PGD**=*filename*<br/>
指定 .pgd 文件的基文件名。 默认情况下，链接器使用带.pgd 扩展名的基的可执行文件名称。

## <a name="remarks"></a>备注

**/USEPROFILE**链接器选项一起使用**/LTCG**生成或更新基于 PGO 培训数据优化的版本。 它是已弃用的等效项**/LTCG:PGUPDATE**和**/ltcg: pgoptimize**选项。

可选**主动**参数禁用大小相关试探法来尝试针对速度进行优化。 这可能会导致大大增加你可执行文件的大小和可能增加所生成的速度的优化功能。 你应配置文件，并比较使用和不使用的结果**主动**。 此参数必须指定显式;默认情况下不启用它。

**PGD**参数指定要使用中的相同的定型数据.pgd 文件的可选名称[/GENPROFILE 或 /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)。 它是已弃用的等效项**/PGD**切换。 默认情况下，或如果没有*filename*指定，如使用可执行文件具有相同的基名称的.pgd 文件。

**/USEPROFILE**链接器选项是 Visual Studio 2015 中的新增功能。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。

1. 选择**配置属性** > **链接器** > **优化**属性页。

1. 在**链接时间代码生成**属性，选择**使用链接时间代码生成 (/ LTCG)**。

1. 选择**配置属性** > **链接器** > **命令行**属性页。

1. 输入**/USEPROFILE**选项和可选参数插入**其他选项**框。 选择**确定**以保存所做的更改。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[/GENPROFILE 和 /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)<br/>
[/LTCG](ltcg-link-time-code-generation.md)<br/>
[按配置文件优化](../../build/reference/profile-guided-optimizations.md)<br/>
[用于按配置文件优化的环境变量](../../build/reference/environment-variables-for-profile-guided-optimizations.md)<br/>

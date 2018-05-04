---
title: /PGD （为按配置优化中指定数据库） |Microsoft 文档
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.ProfileGuidedDatabase
dev_langs:
- C++
helpviewer_keywords:
- -PGD linker option
- /PGD linker option
ms.assetid: 9f312498-493b-461f-886f-92652257e443
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7685f99137a1b599a5f9020fac9e3cae4ba3bc3c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="pgd-specify-database-for-profile-guided-optimizations"></a>/PGD（为按配置文件优化指定数据库）

**/PGD 选项已弃用。** 从 Visual Studio 2015，开始喜欢[/GENPROFILE 或 /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)改为链接器选项。 此选项用于指定使用按配置优化进程的.pgd 文件的名称。

## <a name="syntax"></a>语法

> **/PGD:**_filename_

## <a name="argument"></a>参数

*filename*<br/>
指定用于保存有关正在运行的程序的信息的.pgd 文件的名称。

## <a name="remarks"></a>备注

当使用不推荐使用[/ltcg: pginstrument](../../build/reference/ltcg-link-time-code-generation.md)选项，请使用 **/PGD**来指定非默认名称或使用.pgd 文件的位置。 如果不指定 **/PGD**，.pgd 文件基名称是相同的输出文件 （.exe 或.dll） 基名称和从中调用该链接的同一目录中创建。

当使用不推荐使用 **/ltcg: pgoptimize**选项，请使用 **/PGD**选项以指定要用于创建优化的映像的.pgd 文件的名称。 *Filename*自变量应匹配*filename*指定给 **/ltcg: pginstrument**。

有关详细信息，请参阅[按配置优化](../../build/reference/profile-guided-optimizations.md)。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。

1. 选择**配置属性** > **链接器** > **优化**属性页。

1. 修改**按配置优化数据库**属性。 选择**确定**以保存所做的更改。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

1. 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ProfileGuidedDatabase%2A>。

## <a name="see-also"></a>请参阅

[设置链接器选项](../../build/reference/setting-linker-options.md)<br/>
[链接器选项](../../build/reference/linker-options.md)<br/>

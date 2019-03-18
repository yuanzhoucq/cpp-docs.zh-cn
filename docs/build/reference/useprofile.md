---
title: /USEPROFILE （与 LTCG 使用 PGO 数据）
ms.date: 03/14/2018
f1_keywords:
- USEPROFILE
ms.openlocfilehash: 7bc0033ae5ef512cbd2e2063c5cb9bd9b061c180
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57816524"
---
# <a name="useprofile-run-pgo-in-thread-safe-mode"></a>/USEPROFILE (在线程安全模式下运行 PGO)

此链接器选项一起使用[/LTCG (链接时间代码生成](ltcg-link-time-code-generation.md)通知链接器使用按配置优化 (PGO) 训练数据生成。

## <a name="syntax"></a>语法

> **/USEPROFILE**[**:**{**AGGRESSIVE**|**PGD=**_filename_}]

### <a name="arguments"></a>自变量

**AGGRESSIVE**<br/>
此可选参数指定在优化的代码生成过程中，应使用主动速度优化。

**PGD**=*filename*<br/>
指定 .pgd 文件的基文件名。 默认情况下，链接器使用带.pgd 扩展名基可执行文件名称。

## <a name="remarks"></a>备注

**/USEPROFILE**连同使用链接器选项 **/LTCG**生成或更新优化的生成基于 PGO 训练数据。 它是已弃用的等效 **/LTCG:PGUPDATE**并 **/ltcg: pgoptimize**选项。

可选**过激**参数禁用大小相关试探法来尝试优化速度。 这可能会导致优化，显著增大到可执行文件，并可能会增加所生成的速度。 您应配置文件，并比较使用和不使用的结果**过激**。 必须显式; 指定此参数默认情况下未启用它。

**PGD**参数指定要使用中的相同的定型数据.pgd 文件的可选名称[/GENPROFILE 或 /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)。 它是已弃用的等效 **/PGD**切换。 默认情况下，或如果没有*文件名*指定，则具有相同的基名称，如使用可执行文件的.pgd 文件。

**/USEPROFILE**链接器选项是 Visual Studio 2015 中的新增功能。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[Visual Studio 中的设置 c + + 编译器和生成属性](../working-with-project-properties.md)。

1. 选择**配置属性** > **链接器** > **优化**属性页。

1. 在中**链接时间代码生成**属性中，选择**使用链接时间代码生成 (/ LTCG)**。

1. 选择**配置属性** > **链接器** > **命令行**属性页。

1. 输入 **/USEPROFILE**选项和可选参数置于**其他选项**框。 选择“确定”以保存更改。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[/GENPROFILE 和 /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)<br/>
[/LTCG](ltcg-link-time-code-generation.md)<br/>
[按配置文件优化](../profile-guided-optimizations.md)<br/>
[用于按配置文件优化的环境变量](../environment-variables-for-profile-guided-optimizations.md)<br/>

---
title: /GENPROFILE, /FASTGENPROFILE（生成经分析检测的生成）
ms.date: 03/14/2018
f1_keywords:
- GENPROFILE
- FASTGENPROFILE
- /GENPROFILE
- /FASTGENPROFILE
helpviewer_keywords:
- GENPROFILE
- FASTGENPROFILE
ms.assetid: deff5ce7-46f5-448a-b9cd-a7a83a6864c6
ms.openlocfilehash: cf6327b175344f1e2914792eb47a4838e544ea24
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57813872"
---
# <a name="genprofile-fastgenprofile-generate-profiling-instrumented-build"></a>/GENPROFILE, /FASTGENPROFILE（生成经分析检测的生成）

通过链接器指定 .pgd 文件的生成，以支持按配置优化 (PGO)。 **/GENPROFILE**并 **/FASTGENPROFILE**使用不同的默认参数。 使用 **/GENPROFILE**若要在分析期间精度优先速度和内存使用情况。 使用 **/FASTGENPROFILE**倾向于精度的较小的内存使用情况和速度。

## <a name="syntax"></a>语法

> **/GENPROFILE**[**:**{[**COUNTER32**|**COUNTER64**] | [**EXACT**|**NOEXACT**] |**MEMMAX =**_#_|**MEMMIN =**_#_| [**路径**|**NOPATH** ] | [**TRACKEH** |**NOTRACKEH** ] |**PGD =**_文件名_}]<br/>
> **/ FASTGENPROFILE**[**:**{[**COUNTER32**|**COUNTER64**] | [**EXACT**|**NOEXACT**] |**MEMMAX =**_#_|**MEMMIN =**_#_| [**路径**|**NOPATH** ] | [**TRACKEH** |**NOTRACKEH** ] |**PGD =**_文件名_}]

### <a name="arguments"></a>自变量

可能会为指定以下参数的任何 **/GENPROFILE**或 **/FASTGENPROFILE**。 此处列出的参数由竖线分隔 (**|**) 字符是互相排斥。 使用逗号 (**，**) 字符以分隔选项。

**COUNTER32** &#124; **COUNTER64**<br/>
使用**COUNTER32**若要指定使用 32 位探针计数器，并**COUNTER64**若要指定 64 位探针计数器。 当指定 **/GENPROFILE**，默认值是**COUNTER64**。 当指定 **/FASTGENPROFILE**，默认值是**COUNTER32**。

**EXACT** &#124; **NOEXACT**<br/>
使用**EXACT**来指定用于探测的线程安全互锁的增量。 **NOEXACT**指定用于探测的未受保护的增量操作。 默认值是**NOEXACT**。

**MEMMAX**=*值*， **MEMMIN**=*值*<br/>
使用**MEMMAX**并**MEMMIN**在内存中指定定型数据的最大和最小预留大小。 该值为要保留的内存量（以字节为单位）。 默认情况下，这些值由内部启发式确定。

**PATH**  &#124; **NOPATH** <br/>
使用**路径**指定一组单独的函数的每个唯一路径的 PGO 计数器。 使用**NOPATH**以指定只有一组计数器为每个函数。 当指定 **/GENPROFILE**，默认值是**路径**。 当指定 **/FASTGENPROFILE**，默认值是**NOPATH** 。

**TRACKEH** &AMP;#124; **NOTRACKEH** <br/>
指定是否使用额外计数器以便在训练期间引发异常时保持准确计数。 使用**TRACKEH**指定额外计数器以进行确切计数。 使用**NOTRACKEH**若要指定单个计数器的代码，不使用异常处理或不会遇到在训练方案中的异常。  当指定 **/GENPROFILE**，默认值是**TRACKEH** 。 当指定 **/FASTGENPROFILE**，默认值是**NOTRACKEH** 。

**PGD**=*filename*<br/>
指定 .pgd 文件的基文件名。 默认情况下，链接器使用带 .pgd 扩展名的基本可执行映像文件名。

## <a name="remarks"></a>备注

**/GENPROFILE**并 **/FASTGENPROFILE**选项告知链接器生成的配置文件按配置优化 (PGO) 支持应用程序训练所需的分析检测文件。 这些选项是 Visual Studio 2015 中的新增功能。 更喜欢对不推荐使用这些选项 **/ltcg: pginstrument**， **/PGD**并 **/POGOSAFEMODE**选项和**PogoSafeMode**， **VCPROFILE_ALLOC_SCALE**并**VCPROFILE_PATH**环境变量。 将应用程序训练生成的分析信息用作输入，以在生成期间执行目标全程序优化。 你可以设置其他选项来控制各种性能分析功能，以调整应用训练和生成期间的性能。 指定的默认选项 **/GENPROFILE**提供最准确的结果，尤其是对于大型的复杂多线程应用。 **/FASTGENPROFILE**选项降低内存占用量和更快的性能，代价是牺牲准确性的培训，在使用不同的默认值。

通过使用生成后运行所检测的应用时捕获分析信息 **/GENPROFILE**的 **/FASTGENPROFILE**。 指定时捕获此信息[/USEPROFILE](useprofile.md)链接器选项以执行分析步骤，然后用于指导优化的生成步骤。 有关如何训练您的应用程序的详细信息和所收集的数据的详细信息，请参阅[按配置文件优化](../profile-guided-optimizations.md)。

此外必须指定 **/LTCG**时指定 **/GENPROFILE**或 **/FASTGENPROFILE**。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[Visual Studio 中的设置 c + + 编译器和生成属性](../working-with-project-properties.md)。

1. 选择**配置属性** > **链接器** > **命令行**属性页。

1. 输入 **/GENPROFILE**或 **/FASTGENPROFILE**选项和参数置于**其他选项**框。 选择“确定”以保存更改。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[MSVC 链接器引用](linking.md)<br/>
[MSVC 链接器选项](linker-options.md)<br/>
[/LTCG（链接时间代码生成）](ltcg-link-time-code-generation.md)<br/>

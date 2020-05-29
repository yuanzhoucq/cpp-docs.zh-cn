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
ms.openlocfilehash: 19ddf56d92cc2d8fbbfaf635c8e1602443e35b5b
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825779"
---
# <a name="genprofile-fastgenprofile-generate-profiling-instrumented-build"></a>/GENPROFILE, /FASTGENPROFILE（生成经分析检测的生成）

通过链接器指定 .pgd 文件的生成，以支持按配置优化 (PGO)。 **/GENPROFILE**和 **/FASTGENPROFILE**使用不同的默认参数。 在分析期间，使用 **/GENPROFILE**来优选速度和内存使用情况。 使用 **/FASTGENPROFILE**可以更快地使用较小的内存和速度。

## <a name="syntax"></a>语法

> **/GENPROFILE**[**：**{[**COUNTER32**|**COUNTER64**] | [**精确**|**NOEXACT**] |**MEMMAX =**_#_|**MEMMIN =**_#_|[**路径**|**NOPATH** ] |[**TRACKEH** |**NOTRACKEH** ] |**PGD =**_filename_}] \
> **/FASTGENPROFILE**[**：**{[**COUNTER32**|**COUNTER64**] | [**精确**|**NOEXACT**] |**MEMMAX =**_#_|**MEMMIN =**_#_|[**路径**|**NOPATH** ] |[**TRACKEH** |**NOTRACKEH** ] |**PGD =**_filename_}]

### <a name="arguments"></a>参数

以下任何参数均可指定给 **/GENPROFILE**或 **/FASTGENPROFILE**。 此处用竖线（**|**）字符分隔的参数是互斥的。 使用逗号（**，**）字符分隔选项。

**COUNTER32** &#124; **COUNTER64**<br/>
使用**COUNTER32**指定32位探测计数器的用法，并使用**COUNTER64**指定64位探测计数器。 指定 **/GENPROFILE**时，默认值为**COUNTER64**。 指定 **/FASTGENPROFILE**时，默认值为**COUNTER32**。

**精确**&#124; **NOEXACT**<br/>
使用**EXACT**指定探测器的线程安全互锁增量。 **NOEXACT**指定探测器的未受保护增量操作。 默认值为**NOEXACT**。

**MEMMAX**=*value*， **MEMMIN**=*值*<br/>
使用**MEMMAX**和**MEMMIN**指定内存中训练数据的最大和最小预留大小。 该值为要保留的内存量（以字节为单位）。 默认情况下，这些值由内部启发式确定。

**路径**&#124; **NOPATH** <br/>
使用**PATH**为函数的每个唯一路径指定一组单独的 PGO 计数器。 使用**NOPATH**为每个函数仅指定一组计数器。 指定 **/GENPROFILE**时，默认为**PATH** 。 指定 **/FASTGENPROFILE**时，默认值为**NOPATH** 。

**TRACKEH** &#124; **NOTRACKEH** <br/>
指定是否使用额外计数器以便在训练期间引发异常时保持准确计数。 使用**TRACKEH**为准确计数指定额外的计数器。 使用**NOTRACKEH**为不使用异常处理或在定型方案中不会遇到异常的代码指定单个计数器。  指定 **/GENPROFILE**时，默认值为**TRACKEH** 。 指定 **/FASTGENPROFILE**时，默认值为**NOTRACKEH** 。

**PGD**=*文件名*<br/>
指定 .pgd 文件的基文件名。 默认情况下，链接器使用带 .pgd 扩展名的基本可执行映像文件名。

## <a name="remarks"></a>备注

**/GENPROFILE**和 **/FASTGENPROFILE**选项告知链接器生成支持按配置文件优化（PGO）的应用程序训练所需的分析检测文件。 这些选项是 Visual Studio 2015 中的新增选项。 首选这些选项到弃用的 **/ltcg： PGINSTRUMENT**、 **/PGD**和 **/POGOSAFEMODE**选项以及**POGOSAFEMODE**、 **VCPROFILE_ALLOC_SCALE**和**VCPROFILE_PATH**环境变量。 将应用程序训练生成的分析信息用作输入，以在生成期间执行目标全程序优化。 你可以设置其他选项来控制各种性能分析功能，以调整应用训练和生成期间的性能。 **/GENPROFILE**指定的默认选项提供最准确的结果，尤其是对于大型的复杂多线程应用。 在定型期间， **/FASTGENPROFILE**选项使用不同的默认值来实现更低的内存占用量和更快的性能。

使用 **/FASTGENPROFILE**的 **/GENPROFILE**进行生成后，当你运行已检测应用时，将捕获分析信息。 当你指定[/USEPROFILE](useprofile.md)链接器选项来执行分析步骤，然后使用该选项来引导优化生成步骤时，将捕获此信息。 若要详细了解如何培训您的应用程序和有关所收集数据的详细信息，请参阅[按配置文件优化](../profile-guided-optimizations.md)。

指定 **/GENPROFILE**或 **/FASTGENPROFILE**时，还必须指定 **/ltcg** 。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页” **** 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择 "**配置属性** > **链接器** > **命令行**" 属性页。

1. 在 "**附加选项**" 框中输入 **/GENPROFILE**或 **/FASTGENPROFILE**选项和参数。 选择“确定”以保存更改****。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A> 。

## <a name="see-also"></a>另请参阅

[MSVC 链接器参考](linking.md)<br/>
[MSVC 链接器选项](linker-options.md)<br/>
[/LTCG （链接时间代码生成）](ltcg-link-time-code-generation.md)<br/>

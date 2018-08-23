---
title: /GENPROFILE，/FASTGENPROFILE （生成经分析检测的生成） |Microsoft 文档
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- GENPROFILE
- FASTGENPROFILE
- /GENPROFILE
- /FASTGENPROFILE
helpviewer_keywords:
- GENPROFILE
- FASTGENPROFILE
ms.assetid: deff5ce7-46f5-448a-b9cd-a7a83a6864c6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 05d7961ff46661b8f6df2768591932699c3965d4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379297"
---
# <a name="genprofile-fastgenprofile-generate-profiling-instrumented-build"></a>/GENPROFILE, /FASTGENPROFILE（生成经分析检测的生成）

通过链接器指定 .pgd 文件的生成，以支持按配置优化 (PGO)。 **/GENPROFILE**和 **/FASTGENPROFILE**使用不同的默认参数。 使用 **/GENPROFILE**来分析过程优先通过速度和内存使用情况的精度。 使用 **/FASTGENPROFILE**来优先于精度的较小的内存使用情况和速度。

## <a name="syntax"></a>语法

> **/GENPROFILE**[**:**{[**COUNTER32**|**COUNTER64**] | [**EXACT**|**NOEXACT**] |**MEMMAX =**_#_|**MEMMIN =**_#_| [**路径**|**NOPATH** ] | [**TRACKEH** |**NOTRACKEH** ] |**PGD =**_filename_}]<br/>
> **/ FASTGENPROFILE**[**:**{[**COUNTER32**|**COUNTER64**] | [**EXACT**|**NOEXACT**] |**MEMMAX =**_#_|**MEMMIN =**_#_| [**路径**|**NOPATH** ] | [**TRACKEH** |**NOTRACKEH** ] |**PGD =**_filename_}]

### <a name="arguments"></a>自变量

以下自变量的任何可能指定给 **/GENPROFILE**或 **/FASTGENPROFILE**。 此处列出的参数隔开管道 (**|**) 字符是互相排斥。 使用逗号 (**，**) 字符，用于分隔选项。

**COUNTER32** &AMP;#124; **COUNTER64**<br/>
使用**COUNTER32**来指定的 32 位探针计数器，用法和**COUNTER64**若要指定 64 位探针计数器。 当指定 **/GENPROFILE**，默认值是**COUNTER64**。 当指定 **/FASTGENPROFILE**，默认值是**COUNTER32**。

**确切** &AMP;#124; **NOEXACT**<br/>
使用**EXACT**指定为探针的线程安全互锁的增量。 **NOEXACT**指定探测的未受保护的增量操作。 默认值是**NOEXACT**。

**MEMMAX**=*值*， **MEMMIN**=*值*<br/>
使用**MEMMAX**和**MEMMIN**指定内存中的定型数据的最大和最小预留大小。 该值为要保留的内存量（以字节为单位）。 默认情况下，这些值由内部启发式确定。

**路径**&AMP;#124; **NOPATH**  <br/>
使用**路径**以指定一组单独的 PGO 计数器的每个唯一路径的函数。 使用**NOPATH**指定只有一个组的每个函数的计数器。 当指定 **/GENPROFILE**，默认值是**路径**。 当指定 **/FASTGENPROFILE**，默认值是**NOPATH** 。

**TRACKEH** &AMP;#124; **NOTRACKEH**  <br/>
指定是否使用额外计数器以便在训练期间引发异常时保持准确计数。 使用**TRACKEH**指定额外计数器以进行确切计数。 使用**NOTRACKEH**若要指定单个计数器的代码，不使用异常处理或，不会遇到培训方案中的异常。  当指定 **/GENPROFILE**，默认值是**TRACKEH** 。 当指定 **/FASTGENPROFILE**，默认值是**NOTRACKEH** 。

**PGD**=*filename*<br/>
指定 .pgd 文件的基文件名。 默认情况下，链接器使用带 .pgd 扩展名的基本可执行映像文件名。

## <a name="remarks"></a>备注

**/GENPROFILE**和 **/FASTGENPROFILE**选项告知链接器生成支持按配置优化 (PGO) 的应用程序训练所需的分析检测文件。 这些选项是 Visual Studio 2015 中的新增功能。 希望为不推荐使用这些选项 **/ltcg: pginstrument**， **/PGD**和 **/POGOSAFEMODE**选项和**PogoSafeMode**， **VCPROFILE_ALLOC_SCALE**和**VCPROFILE_PATH**环境变量。 将应用程序训练生成的分析信息用作输入，以在生成期间执行目标全程序优化。 你可以设置其他选项来控制各种性能分析功能，以调整应用训练和生成期间的性能。 通过指定的默认选项 **/GENPROFILE**提供最准确的结果，尤其是对于大型、 复杂的多线程应用。 **/FASTGENPROFILE**选项使用不同的默认值较低的内存占用量和在培训，代价是牺牲准确性期间更快的性能。

通过使用生成后运行所检测的应用时捕获分析信息 **/GENPROFILE**的 **/FASTGENPROFILE**。 在你指定此信息时会捕获[/USEPROFILE](useprofile.md)链接器选项以执行分析步骤，然后使用指导优化的生成步骤。 有关如何训练您的应用程序的详细信息和收集的数据的详细信息，请参阅[按配置优化](profile-guided-optimizations.md)。

你还必须指定 **/LTCG**时指定 **/GENPROFILE**或 **/FASTGENPROFILE**。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。

1. 选择**配置属性** > **链接器** > **命令行**属性页。

1. 输入 **/GENPROFILE**或 **/FASTGENPROFILE**选项和参数插入**其他选项**框。 选择**确定**以保存所做的更改。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[设置链接器选项](../../build/reference/setting-linker-options.md)<br/>
[链接器选项](../../build/reference/linker-options.md)<br/>
[/LTCG（链接时间代码生成）](../../build/reference/ltcg-link-time-code-generation.md)<br/>

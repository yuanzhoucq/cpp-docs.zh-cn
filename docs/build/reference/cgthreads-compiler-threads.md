---
title: /CGTHREADS（编译器线程）
ms.date: 11/04/2016
helpviewer_keywords:
- /CGTHREADS linker option
- -CGTHREADS linker option
- CGTHREADS linker option
ms.assetid: 4b52cfdb-3702-470b-9580-fabeb1417488
ms.openlocfilehash: e2e1a51dcff46601034ed18292e9c4dcf4bd7d5c
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57413935"
---
# <a name="cgthreads-compiler-threads"></a>/CGTHREADS（编译器线程）

设置 cl.exe 线程数以在指定链接时代码生成后用于优化和代码生成。

## <a name="syntax"></a>语法

```
/CGTHREADS:[1-8]
```

## <a name="arguments"></a>自变量

*number*<br/>
可供 cl.exe 使用的最大线程数，范围在 1 到 8 之间。

## <a name="remarks"></a>备注

**/CGTHREADS**选项指定线程 cl.exe 使用的最大数目并行优化和代码生成阶段的编译时链接时间代码生成 ([/LTCG](../../build/reference/ltcg-link-time-code-generation.md)) 是指定。 默认情况下，cl.exe 使用四个线程，如同 **/CGTHREADS:4**指定。 如果有更多处理器内核可用，则较大的 `number` 值可以缩短生成时间。

可为生成指定多个级别的并行。 Msbuild.exe 开关 **/maxcpucount**指定可以并行运行的 MSBuild 进程数。 [/MP （使用多个进程生成）](../../build/reference/mp-build-with-multiple-processes.md)编译器标志指定同时编译源文件的 cl.exe 进程数。 [/Cgthreads](../../build/reference/cgthreads-code-generation-threads.md)编译器选项指定由每个 cl.exe 进程使用的线程数。 由于处理器只能同时运行与处理器内核数量相同的线程数，因此同时为所有这些选项指定较大的值将不起作用，而且还会起反作用。 有关如何并行生成项目的详细信息，请参阅[并行生成多个项目](/visualstudio/msbuild/building-multiple-projects-in-parallel-with-msbuild)。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 选择**配置属性**，**链接器**文件夹。

1. 选择**命令行**属性页。

1. 修改**其他选项**属性以包含 **/CGTHREADS:**`number`，其中`number`是从 1 到 8，一个值，然后选择**确定**。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[链接器选项](../../build/reference/linker-options.md)<br/>
[设置链接器选项](../../build/reference/setting-linker-options.md)

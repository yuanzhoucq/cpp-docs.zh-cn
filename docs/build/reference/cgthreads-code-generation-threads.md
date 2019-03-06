---
title: /cgthreads（代码生成线程）
ms.date: 11/04/2016
f1_keywords:
- /cgthreads
helpviewer_keywords:
- /cgthreads compiler option (C++)
- -cgthreads compiler option (C++)
- cgthreads compiler option (C++)
- cgthreads
ms.assetid: 64bc768c-6caa-4baf-9dea-7cfa1ffb01c2
ms.openlocfilehash: 6c3d3b51691247ddef5614cae113ffa9ded576e9
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57425232"
---
# <a name="cgthreads-code-generation-threads"></a>/cgthreads（代码生成线程）

设置 cl.exe 线程数以用于优化和代码生成。

## <a name="syntax"></a>语法

```
/cgthreads[1-8]
```

## <a name="arguments"></a>自变量

*number*<br/>
可供 cl.exe 使用的最大线程数，范围在 1 到 8 之间。

## <a name="remarks"></a>备注

**/Cgthreads**选项指定 cl.exe 线程的最大数目以并行方式使用进行优化和代码编译生成阶段。 请注意，可以是之间没有空格 **/cgthreads**和`number`参数。 默认情况下，cl.exe 使用四个线程，如同 **/cgthreads4**指定。 如果有更多处理器内核可用，则较大的 `number` 值可以缩短生成时间。 它与结合使用时，此选项会尤其有用[/GL （全程序优化）](../../build/reference/gl-whole-program-optimization.md)。

可为生成指定多个级别的并行。 Msbuild.exe 开关 **/maxcpucount**指定可以并行运行的 MSBuild 进程数。 [/MP （使用多个进程生成）](../../build/reference/mp-build-with-multiple-processes.md)编译器标志指定同时编译源文件的 cl.exe 进程数。 **/Cgthreads**选项指定由每个 cl.exe 进程使用的线程数。 由于处理器只能同时运行与处理器内核数量相同的线程数，因此同时为所有这些选项指定较大的值将不起作用，而且还会起反作用。 有关如何并行生成项目的详细信息，请参阅[并行生成多个项目](/visualstudio/msbuild/building-multiple-projects-in-parallel-with-msbuild)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 选择**配置属性**， **C/c + +** 文件夹。

1. 选择**命令行**属性页。

1. 修改**其他选项**属性以包含 **/cgthreads**`N`，其中`N`是一个介于 1 到 8，，然后选择**确定**。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)

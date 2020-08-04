---
title: /cgthreads（代码生成线程）
ms.date: 07/31/2020
f1_keywords:
- /cgthreads
helpviewer_keywords:
- /cgthreads compiler option (C++)
- -cgthreads compiler option (C++)
- cgthreads compiler option (C++)
- cgthreads
ms.assetid: 64bc768c-6caa-4baf-9dea-7cfa1ffb01c2
ms.openlocfilehash: 319a42ab68f02df6019ff283f1039ef3d561c4a0
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/03/2020
ms.locfileid: "87520870"
---
# <a name="cgthreads-code-generation-threads"></a>`/cgthreads`（代码生成线程）

设置 cl.exe 线程数以用于优化和代码生成。

## <a name="syntax"></a>语法

> **`/cgthreads1`**\
> **`/cgthreads2`**\
> **`/cgthreads3`**\
> **`/cgthreads4`**\
> **`/cgthreads5`**\
> **`/cgthreads6`**\
> **`/cgthreads7`**\
> **`/cgthreads8`**

## <a name="arguments"></a>参数

**`cgthreadsN`**\
要使用的 cl.exe 的最大线程数，其中*N*是介于1到8之间的数字。

## <a name="remarks"></a>备注

**`cgthreads`** 选项指定 cl.exe 并行使用的最大线程数，用于编译的优化和代码生成阶段。 请注意 **`cgthreads`** ，和*number*参数之间不能有空格。 默认情况下，cl.exe 使用四个线程，就像指定的情况一样 **`/cgthreads4`** 。 如果有更多的处理器核心可用，则*较大的*值可以缩短生成时间。 当结合[ `/GL` （全程序优化）](gl-whole-program-optimization.md)时，此选项特别有用。

可为生成指定多个级别的并行。 msbuild.exe 开关 **`/maxcpucount`** 指定可并行运行的 MSBuild 进程数。 " [ `/MP` （包含多个进程的生成）](mp-build-with-multiple-processes.md) " 编译器标志指定同时编译源文件的 cl.exe 进程数。 **`cgthreads`** 选项指定每个 cl.exe 进程使用的线程数。 处理器只能与处理器核心同时运行多个线程。 同时为所有这些选项指定较大的值并不是很有用，可以是适得其反。 有关如何并行生成项目的详细信息，请参阅[并行生成多个项目](/visualstudio/msbuild/building-multiple-projects-in-parallel-with-msbuild)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择 "**配置属性**" "  >  **c/c + +**  >  **命令行**" 属性页。

1. 修改 "**附加选项**" 属性以包含 **`cgthreadsN`** ，其中 *`N`* 是介于1到8之间的值，然后选择 **"确定"**。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)

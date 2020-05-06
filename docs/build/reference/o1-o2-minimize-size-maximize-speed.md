---
title: /O1、/O2（最小化大小、最大化速度）
ms.date: 09/25/2017
f1_keywords:
- /o2
- /o1
helpviewer_keywords:
- maximize speed compiler option [C++]
- minimize size compiler option [C++]
- -O2 compiler option [C++]
- fast code
- small code
- O2 compiler option [C++]
- /O2 compiler option [C++]
- -O1 compiler option [C++]
- O1 compiler option [C++]
- /O1 compiler option [C++]
ms.assetid: 2d1423f5-53d9-44da-8908-b33a351656c2
ms.openlocfilehash: 3daf5dd5f9912194fd5d8aaeb4c7a312be142b69
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825335"
---
# <a name="o1-o2-minimize-size-maximize-speed"></a>/O1、/O2（最小化大小、最大化速度）

选择一组会影响生成的代码的大小和速度的预定义选项。

## <a name="syntax"></a>语法

> O1
> /O2

## <a name="remarks"></a>备注

使用 **/O1**和 **/O2**编译器选项，可以一次设置多个特定的优化选项。 在大多数情况下， **/O1**选项设置创建最小代码的各个优化选项。 在大多数情况下， **/O2**选项设置创建最快代码的选项。 **/O2**选项是发布版本的默认选项。 下表显示了 **/O1**和 **/O2**设置的特定选项：

|选项|等效于|
|------------|-------------------|
|**/O1** （最小化大小）|[/Og](og-global-optimizations.md) [/Os](os-ot-favor-small-code-favor-fast-code.md) [/oy](oy-frame-pointer-omission.md) [/Ob2](ob-inline-function-expansion.md) [/gf](gf-eliminate-duplicate-strings.md) [/gy](gy-enable-function-level-linking.md)|
|**/O2** （最大化速度）|[/Og](og-global-optimizations.md) [/Oi](oi-generate-intrinsic-functions.md) [/ot](os-ot-favor-small-code-favor-fast-code.md) [/oy](oy-frame-pointer-omission.md) [/Ob2](ob-inline-function-expansion.md) [/gf](gf-eliminate-duplicate-strings.md) [/gy](gy-enable-function-level-linking.md)|

**/O1**和 **/O2**是互斥的。

> [!NOTE]
> **x86 特定**\
> 这些选项意味着使用框架指针省略（[/oy](oy-frame-pointer-omission.md)）选项。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页” **** 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 在 "**配置属性**" 下，打开 " **c/c + +** "，然后选择 "**优化**" 属性页。

1. 修改 "**优化**" 属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A> 。

## <a name="see-also"></a>另请参阅

[/O 选项（优化代码）](o-options-optimize-code.md)<br/>
[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)<br/>
[/EH （异常处理模型）](eh-exception-handling-model.md)

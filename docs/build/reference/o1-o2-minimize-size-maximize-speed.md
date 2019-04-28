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
ms.openlocfilehash: d33fe6bceae09267fd3f79ffe3dc26864e87c764
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320352"
---
# <a name="o1-o2-minimize-size-maximize-speed"></a>/O1、/O2（最小化大小、最大化速度）

选择一组预定义的影响大小的选项和生成代码的速度。

## <a name="syntax"></a>语法

> /O1 /O2

## <a name="remarks"></a>备注

**/O1**并 **/o2**编译器选项都同时设置多个特定的优化选项的快速方法。 **/O1**选项设置在大多数情况下创建的最小代码的各个优化选项。 **/O2**选项设置在大多数情况下创建最快的代码的选项。 **/O2**选项是发布版本的默认值。 此表显示了通过设置的特定选项 **/o1**并 **/o2**:

|选项|等效于|
|------------|-------------------|
|**/ O1** （最小大小）|[/Og](og-global-optimizations.md) [/Os](os-ot-favor-small-code-favor-fast-code.md) [/Oy](oy-frame-pointer-omission.md) [/Ob2](ob-inline-function-expansion.md) [/GF](gf-eliminate-duplicate-strings.md) [/Gy](gy-enable-function-level-linking.md)|
|**/ O2** （最大化速度）|[/Og](og-global-optimizations.md) [/Oi](oi-generate-intrinsic-functions.md) [/Ot](os-ot-favor-small-code-favor-fast-code.md) [/Oy](oy-frame-pointer-omission.md) [/Ob2](ob-inline-function-expansion.md) [/GF](gf-eliminate-duplicate-strings.md) [/Gy](gy-enable-function-level-linking.md)|

**/ O1**并 **/o2**互相排斥。

> [!NOTE]
> **x86 特定**这些选项意味着使用帧指针省略 ([/Oy](oy-frame-pointer-omission.md)) 选项。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置C++Visual Studio 中的编译器和生成属性](../working-with-project-properties.md)。

1. 下**配置属性**，打开**C /C++**  ，然后选择**优化**属性页。

1. 修改**优化**属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>。

## <a name="see-also"></a>请参阅

[/O 选项（优化代码）](o-options-optimize-code.md)<br/>
[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)<br/>
[/EH（异常处理模型）](eh-exception-handling-model.md)

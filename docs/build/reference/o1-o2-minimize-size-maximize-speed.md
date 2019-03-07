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
ms.openlocfilehash: 8074d4308974673c18dffb45ae580d43f3a377b3
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57415535"
---
# <a name="o1-o2-minimize-size-maximize-speed"></a>/O1、/O2（最小化大小、最大化速度）

选择一组预定义的影响大小的选项和生成代码的速度。

## <a name="syntax"></a>语法

> /O1 /O2

## <a name="remarks"></a>备注

**/O1**并 **/o2**编译器选项都同时设置多个特定的优化选项的快速方法。 **/O1**选项设置在大多数情况下创建的最小代码的各个优化选项。 **/O2**选项设置在大多数情况下创建最快的代码的选项。 **/O2**选项是发布版本的默认值。 此表显示了通过设置的特定选项 **/o1**并 **/o2**:

|选项|等效于|
|------------|-------------------|
|**/ O1** （最小大小）|[/Og](../../build/reference/og-global-optimizations.md) [/Os](../../build/reference/os-ot-favor-small-code-favor-fast-code.md) [/Oy](../../build/reference/oy-frame-pointer-omission.md) [/Ob2](../../build/reference/ob-inline-function-expansion.md) [/GF](../../build/reference/gf-eliminate-duplicate-strings.md) [/Gy](../../build/reference/gy-enable-function-level-linking.md)|
|**/ O2** （最大化速度）|[/Og](../../build/reference/og-global-optimizations.md) [/Oi](../../build/reference/oi-generate-intrinsic-functions.md) [/Ot](../../build/reference/os-ot-favor-small-code-favor-fast-code.md) [/Oy](../../build/reference/oy-frame-pointer-omission.md) [/Ob2](../../build/reference/ob-inline-function-expansion.md) [/GF](../../build/reference/gf-eliminate-duplicate-strings.md) [/Gy](../../build/reference/gy-enable-function-level-linking.md)|

**/ O1**并 **/o2**互相排斥。

> [!NOTE]
> **x86 特定**这些选项意味着使用帧指针省略 ([/Oy](../../build/reference/oy-frame-pointer-omission.md)) 选项。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 下**配置属性**，打开**C/c + +** ，然后选择**优化**属性页。

1. 修改**优化**属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>。

## <a name="see-also"></a>请参阅

[/O 选项（优化代码）](../../build/reference/o-options-optimize-code.md)<br/>
[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)<br/>
[/EH（异常处理模型）](../../build/reference/eh-exception-handling-model.md)

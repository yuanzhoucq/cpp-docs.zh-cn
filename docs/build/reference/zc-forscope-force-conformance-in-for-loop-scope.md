---
title: /Zc:forScope（强制 for 循环范围中的一致性）
ms.date: 03/06/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.ForceConformanceInForLoopScope
- VC.Project.VCCLWCECompilerTool.ForceConformanceInForLoopScope
- /zc:forScope
helpviewer_keywords:
- /Zc compiler options [C++]
- -Zc compiler options [C++]
- Conformance compiler options
- Zc compiler options [C++]
ms.assetid: 3031f02d-3b14-4ad0-869e-22b0110c3aed
ms.openlocfilehash: b1173ad609a1b2c95d6cf118f4e2d5defeec5b9c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234336"
---
# <a name="zcforscope-force-conformance-in-for-loop-scope"></a>/Zc:forScope（强制 for 循环范围中的一致性）

用于针对具有 Microsoft 扩展 ( [/Ze](../../cpp/for-statement-cpp.md) ) 的[for](za-ze-disable-language-extensions.md)循环实现标准 C++ 行为。

## <a name="syntax"></a>语法

> **/Zc： forScope**[ **-** ]

## <a name="remarks"></a>备注

标准行为是使 **`for`** 循环的初始值设定项在循环之后超出范围 **`for`** 。 在 **/zc： forScope**和[/ze](za-ze-disable-language-extensions.md)下， **`for`** 循环的初始值设定项保持在范围内，直到局部范围结束。

默认情况下， **/zc： forScope**选项处于启用状态。 如果指定了[/permissive-](permissive-standards-conformance.md)选项，则 **/zc： forScope**不受影响。

**/Zc:forScope-** 选项已弃用，并将从未来版本中删除。 使用 **/Zc:forScope-** 将生成弃用警告 D9035。

以下代码在 **/Ze** （而不是 **/Za**）下进行编译：

```cpp
// zc_forScope.cpp
// compile by using: cl /Zc:forScope- /Za zc_forScope.cpp
// C2065, D9035 expected
int main() {
    // Compile by using cl /Zc:forScope- zc_forScope.cpp
    // to compile this non-standard code as-is.
    // Uncomment the following line to resolve C2065 for /Za.
    // int i;
    for (int i = 0; i < 1; i++)
        ;
    i = 20;   // i has already gone out of scope under /Za
}
```

使用 **/Zc:forScope-** 时，如果变量由于在上一范围内所作的声明而处在范围内，则将生成警告 C4288（默认关闭）。 为了说明这点，请删除示例代码中用于声明 `//` 的 `int i`字符。

可通过使用 **conform** 杂注修改 [/Zc:forScope](../../preprocessor/conform.md) 的运行时行为。

如果在包含现有 .pch 文件的项目中使用 **/Zc:forScope-** ，则将生成警告、忽略 **/Zc:forScope-** ，并使用现有 .pch 文件继续进行编译。 如果希望生成新的 .pch 文件，请使用[/yc （创建预编译标头文件）](yc-create-precompiled-header-file.md)。

有关 Visual C++ 中一致性问题的详细信息，请参阅 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择 "**配置属性**" "  >  **c/c + +**  >  **语言**" 属性页。

1. 修改 **“强制 For 循环范围中的一致性”** 属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ForceConformanceInForLoopScope%2A>。

## <a name="see-also"></a>另请参阅

[/Zc（一致性）](zc-conformance.md)<br/>
[/Za、/Ze （禁用语言扩展）](za-ze-disable-language-extensions.md)<br/>

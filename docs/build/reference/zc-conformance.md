---
title: /Zc（一致性）
ms.date: 03/06/2018
helpviewer_keywords:
- /Zc compiler options [C++]
- -Zc compiler options [C++]
- Conformance compiler options
- Zc compiler options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
ms.openlocfilehash: 6d6d3b7736fd1775372a3b2093c53e177db5099e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234349"
---
# <a name="zc-conformance"></a>`/Zc`度

您可以使用 **`/Zc`** 编译器选项来指定标准或特定于 Microsoft 的编译器行为。

## <a name="syntax"></a>语法

> **`/Zc:`**_选项_{，_选项_}

## <a name="remarks"></a>备注

当 Visual Studio 实现了与标准不兼容的 C 或 c + + 扩展时，可以使用 **`/Zc`** 一致性选项来指定标准相容或特定于 Microsoft 的行为。 对于某些选项，Microsoft 特定的行为是默认行为，以防止对现有代码进行大规模的重大更改。 在其他情况下，默认值为标准行为，在安全性、性能或兼容性方面的改进超出了重大更改的成本。 在较新版本的 Visual Studio 中，每种一致性选项的默认设置可能会发生变化。 有关每种一致性选项的详细信息，请参阅主题。 [`/permissive-`](permissive-standards-conformance.md)编译器选项将默认情况下不设置的一致性选项设置为一致的设置。

这些是 **`/Zc`** 编译器选项：

| 选项 | 行为 |
|--|--|
| [`/Zc:alignedNew`](zc-alignednew.md) | 启用 c + + 17 过度对齐动态分配（默认情况下在 c + + 17 中启用）。 |
| [`/Zc:auto`](zc-auto-deduce-variable-type.md) | 为（默认情况下为）强制实施新的标准 c + + 含义 **`auto`** 。 |
| [`/Zc__cplusplus`](zc-cplusplus.md) | 使 `__cplusplus` 宏能够报告支持的标准（默认为关闭）。 |
| [`/Zc:externConstexpr`](zc-externconstexpr.md) | 启用变量的外部链接 **`constexpr`** （默认为关闭）。 |
| [`/Zc:forScope`](zc-forscope-force-conformance-in-for-loop-scope.md) | 强制实施标准 c + + **`for`** 范围规则（默认为启用）。 |
| [`/ZcimplicitNoexcept`](zc-implicitnoexcept-implicit-exception-specifiers.md) | 启用 **`noexcept`** 对所需函数的隐式（默认为启用）。 |
| [`/Zc:inline`](zc-inline-remove-unreferenced-comdat.md) | 删除未引用的函数或数据（如果它是 COMDAT 或仅具有内部链接）（默认为关闭）。 |
| [`/Zc:noexceptTypes`](zc-noexcepttypes.md) | 强制执行 c + + 17 **`noexcept`** 规则（在 c + + 17 或更高版本中默认启用）。 |
| [`/Zc:referenceBinding`](zc-referencebinding-enforce-reference-binding-rules.md) | UDT 临时项不会绑定到非常量左值引用（默认为关闭）。 |
| [`/Zc:rvalueCast`](zc-rvaluecast-enforce-type-conversion-rules.md) | 强制实施标准 c + + 显式类型转换规则（默认关闭）。 |
| [`/Zc:sizedDealloc`](zc-sizeddealloc-enable-global-sized-dealloc-functions.md) | 启用 c + + 14 全局大小释放函数（默认为启用）。 |
| [`/Zc:strictStrings`](zc-strictstrings-disable-string-literal-type-conversion.md) | 禁用字符串到 `char*` 或 `wchar_t*` 转换（默认为关闭）。 |
| [`/Zc:ternary`](zc-ternary.md) | 强制执行有关操作数类型的条件运算符规则（默认关闭）。 |
| [`/Zc:threadSafeInit`](zc-threadsafeinit-thread-safe-local-static-initialization.md) | 启用线程安全的本地静态初始化（默认为启用）。 |
| [`/Zc:throwingNew`](zc-throwingnew-assume-operator-new-throws.md) | 假设 **`operator new`** 失败时引发（默认关闭）。 |
| [`/Zc:trigraphs`](zc-trigraphs-trigraphs-substitution.md) | 启用 trigraphs （已过时，默认情况下为关闭）。 |
| [`/Zc:twoPhase`](zc-twophase.md) | 使用不一致的模板分析行为（默认情况下符合）。 |
| [`/Zc:wchar_t`](zc-wchar-t-wchar-t-is-native-type.md) | **`wchar_t`** 是本机类型，不是 typedef （默认情况下启用）。 |

有关 Visual C++ 中一致性问题的详细信息，请参阅 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。

## <a name="see-also"></a>另请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)

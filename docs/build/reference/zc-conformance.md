---
title: /Zc（一致性）
ms.date: 03/06/2018
helpviewer_keywords:
- /Zc compiler options [C++]
- -Zc compiler options [C++]
- Conformance compiler options
- Zc compiler options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
ms.openlocfilehash: 4422524deab2a749c96d5e967bc3223d0c9c9873
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438666"
---
# <a name="zc-conformance"></a>/Zc（一致性）

可以使用 **/zc**编译器选项来指定标准或特定于 Microsoft 的编译器行为。

## <a name="syntax"></a>语法

> **/Zc：** _选项_{，_选项_}

## <a name="remarks"></a>备注

当 Visual Studio 实现 C 的扩展或C++与标准不兼容时，可以使用 `/Zc` 一致性选项来指定符合标准的或特定于 Microsoft 的行为。 对于某些选项，Microsoft 特定的行为是默认行为，以防止对现有代码进行大规模的重大更改。 在其他情况下，默认值为标准行为，在安全性、性能或兼容性方面的改进超出了重大更改的成本。 在较新版本的 Visual Studio 中，每种一致性选项的默认设置可能会发生变化。 有关每种一致性选项的详细信息，请参阅主题。 [/Permissive-](permissive-standards-conformance.md)编译器选项隐式设置默认情况下未设置为符合性设置的一致性选项。

下面是 `/Zc` 编译器选项：

|选项|行为|
|---|---|
|[alignedNew\[-\]](zc-alignednew.md)|启用 c + + 17 过度对齐动态分配（默认情况下在 c + + 17 中启用）。|
|[自动\[-\]](zc-auto-deduce-variable-type.md)|为 `auto` 强制实施C++新的标准含义（默认为启用）。|
|[__cplusplus\[-\]](zc-cplusplus.md)|启用 **__cplusplus**宏，以报告支持的标准（默认为关闭）。|
|[externConstexpr\[-\]](zc-externconstexpr.md)|为 `constexpr` 变量启用外部链接（默认为关闭）。|
|[forScope\[-\]](zc-forscope-force-conformance-in-for-loop-scope.md)|强制标准C++ `for` 范围规则（默认为启用）。|
|[implicitNoexcept\[-\]](zc-implicitnoexcept-implicit-exception-specifiers.md)|启用对所需函数的隐式 `noexcept` （默认为启用）。|
|[内联\[-\]](zc-inline-remove-unreferenced-comdat.md)|删除未引用的函数或数据（如果它是 COMDAT 或仅具有内部链接）（默认为关闭）。|
|[noexceptTypes\[-\]](zc-noexcepttypes.md)|强制执行 c + + 17 noexcept 规则（在 c + + 17 或更高版本中默认启用）。|
|[referenceBinding\[-\]](zc-referencebinding-enforce-reference-binding-rules.md)|UDT 临时项不会绑定到非常量左值引用（默认为关闭）。|
|[rvalueCast\[-\]](zc-rvaluecast-enforce-type-conversion-rules.md)|强制标准C++显式类型转换规则（默认关闭）。|
|[sizedDealloc\[-\]](zc-sizeddealloc-enable-global-sized-dealloc-functions.md)|启用 c + + 14 全局大小释放函数（默认为启用）。|
|[strictStrings\[-\]](zc-strictstrings-disable-string-literal-type-conversion.md)|禁用要 `char*` 或 `wchar_t*` 转换的字符串文本（默认为关闭）。|
|[三元\[-\]](zc-ternary.md)|强制执行有关操作数类型的条件运算符规则（默认关闭）。|
|[threadSafeInit\[-\]](zc-threadsafeinit-thread-safe-local-static-initialization.md)|启用线程安全的本地静态初始化（默认为启用）。|
|[throwingNew\[-\]](zc-throwingnew-assume-operator-new-throws.md)|假定 `operator new` 在失败时引发（默认关闭）。|
|[trigraphs\[-\]](zc-trigraphs-trigraphs-substitution.md)|启用 trigraphs （已过时，默认情况下为关闭）。|
|[twoPhase](zc-twophase.md)|使用不一致的模板分析行为（默认情况下符合）。|
|[wchar_t\[-\]](zc-wchar-t-wchar-t-is-native-type.md)|`wchar_t` 是本机类型，不是 typedef （默认启用）。|

有关 Visual C++ 中一致性问题的详细信息，请参阅 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。

## <a name="see-also"></a>另请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)

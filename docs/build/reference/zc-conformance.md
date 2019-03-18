---
title: /Zc（一致性）
ms.date: 03/06/2018
f1_keywords:
- /zc
helpviewer_keywords:
- /Zc compiler options [C++]
- -Zc compiler options [C++]
- Conformance compiler options
- Zc compiler options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
ms.openlocfilehash: e24dd53f9c805f57ce974a81a4963434f1868095
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57821204"
---
# <a name="zc-conformance"></a>/Zc（一致性）

可以使用 **/Zc**编译器选项来指定标准或特定于 Microsoft 的编译器行为。

## <a name="syntax"></a>语法

> **/ Zc:**_选项_{，_选项_}

## <a name="remarks"></a>备注

当 Visual Studio 已实现对 C 或 c + + 不符合标准的扩展时，可以使用`/Zc`一致性选项以指定符合标准的或特定于 Microsoft 的行为。 对于一些选项，特定于 Microsoft 的行为是默认值，以防止对现有代码的大规模重大更改。 在其他情况下，默认值为标准的行为，其中中安全、 性能或兼容性的改进带来的重大更改的成本。 较新版本的 Visual Studio 可能会改变每个符合性选项的默认设置。 有关每个符合性选项的详细信息，请参阅特定选项的主题。 [触发-](permissive-standards-conformance.md)编译器选项隐式设置为其符合的设置的默认情况下不设置的符合性选项。

这些是`/Zc`编译器选项：

|选项|行为|
|---|---|
|[alignedNew\[-\]](zc-alignednew.md)|启用 C + + 17 过度对齐动态分配 （在默认情况下在 C + + 17）。|
|[auto\[-\]](zc-auto-deduce-variable-type.md)|强制实施的新的标准 c + + 含义`auto`(在默认情况下)。|
|[__cplusplus\[-\]](zc-cplusplus.md)|启用 **__cplusplus**宏来报告的受支持的标准 （默认情况下关闭）。|
|[externConstexpr\[-\]](zc-externconstexpr.md)|启用外部链接的`constexpr`变量 （默认情况下关闭）。|
|[forScope\[-\]](zc-forscope-force-conformance-in-for-loop-scope.md)|强制执行标准 c + +`for`范围规则 (在默认情况下)。|
|[implicitNoexcept\[-\]](zc-implicitnoexcept-implicit-exception-specifiers.md)|启用隐式`noexcept`上所需的功能 (在默认情况下)。|
|[inline\[-\]](zc-inline-remove-unreferenced-comdat.md)|如果它为 COMDAT 或具有内部链接只能删除未引用的函数或数据 （默认情况下关闭）。|
|[noexceptTypes\[-\]](zc-noexcepttypes.md)|强制执行 C + + 17 noexcept 规则 (在默认情况下，在 C + + 17 或更高版本)。|
|[referenceBinding\[-\]](zc-referencebinding-enforce-reference-binding-rules.md)|UDT 临时不会绑定到的非常量左值引用 （默认情况下关闭）。|
|[rvalueCast\[-\]](zc-rvaluecast-enforce-type-conversion-rules.md)|强制实施标准 c + + 显式类型转换规则 （默认情况下关闭）。|
|[sizedDealloc\[-\]](zc-sizeddealloc-enable-global-sized-dealloc-functions.md)|启用 C + + 14 个全局大小的释放函数 (在默认情况下)。|
|[strictStrings\[-\]](zc-strictstrings-disable-string-literal-type-conversion.md)|禁用字符串文本`char*`或`wchar_t*`转换 （默认情况下关闭）。|
|[ternary\[-\]](zc-ternary.md)|强制实施条件运算符的操作数类型上的规则 （默认情况下关闭）。|
|[threadSafeInit\[-\]](zc-threadsafeinit-thread-safe-local-static-initialization.md)|启用线程安全的本地静态初始化 (在默认情况下)。|
|[throwingNew\[-\]](zc-throwingnew-assume-operator-new-throws.md)|假定`operator new`失败时引发 （默认情况下关闭）。|
|[trigraphs\[-\]](zc-trigraphs-trigraphs-substitution.md)|启用三元祖 （已过时，关闭默认情况下）。|
|[twoPhase-](zc-twophase.md)|使用不符合要求模板分析 （默认情况下一致性） 的行为。|
|[wchar_t\[-\]](zc-wchar-t-wchar-t-is-native-type.md)|`wchar_t` 是本机类型，不是 typedef (在默认情况下)。|

有关 Visual C++ 中一致性问题的详细信息，请参阅 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。

## <a name="see-also"></a>请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)

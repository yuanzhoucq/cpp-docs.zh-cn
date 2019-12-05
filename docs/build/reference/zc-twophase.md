---
title: /Zc:twoPhase-（禁用两阶段名称查找）
description: 说明如何在指定/permissive-时，/Zc： twoPhase-禁用两阶段名称查找。
ms.date: 12/03/2019
f1_keywords:
- twoPhase
- /Zc:twoPhase
- VC.Project.VCCLCompilerTool.EnforceTypeConversionRules
helpviewer_keywords:
- twoPhase
- disable two-phase name lookup
- /Zc:twoPhase
ms.openlocfilehash: a2ede9f0875bf718d63361201cf8923666078f7a
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74856951"
---
# <a name="zctwophase--disable-two-phase-name-lookup"></a>/Zc:twoPhase-（禁用两阶段名称查找）

" **/Zc： twoPhase** " 选项在 " **/permissive-** " 下，通知编译器使用原始的、不一致的 Microsoft C++编译器行为来分析和实例化类模板和函数模板。

## <a name="syntax"></a>语法

> **/Zc:twoPhase-**

## <a name="remarks"></a>备注

Visual Studio 2017 版本15.3 及更高版本：在[/Permissive-](permissive-standards-conformance.md)下，编译器将使用两阶段名称查找来查找模板名称。 如果还指定 **/zc： twoPhase-** ，则编译器会恢复为其以前的不一致类模板和函数模板名称解析和替换行为。 如果未指定 **/permissive-** ，则默认情况下不一致的行为。

版本10.0.15063.0 （创意者更新或 RS2）及更早版本中的 Windows SDK 头文件在一致性模式下不起作用。 **/Zc： twoPhase-** 当你使用 **/permissive-** 时，需要编译这些 SDK 版本的代码。 从版本10.0.15254.0 （秋季创意者更新或 RS3）开始的 Windows SDK 版本在一致性模式下正常工作。 它们不需要 **/zc： twoPhase** 。

使用 **/zc： twoPhase-** 如果你的代码要求正确编译旧行为。 请考虑更新代码以符合标准。

### <a name="compiler-behavior-under-zctwophase-"></a>/Zc 下的编译器行为： twoPhase-

默认情况下，或者在 Visual Studio 2017 版本15.3 及更高版本中同时指定 **/permissive-** 和 **/zc： twoPhase**时，编译器将使用此行为：

- 它仅分析模板声明、类头和基类列表。 模板正文被捕获为令牌流。 不会分析函数体、初始值设定项、默认参数或 noexcept 参数。 类模板在暂定类型上是伪实例化的，用于验证类模板中的声明是否正确。 请考虑此类模板：

   ```cpp
   template <typename T> class Derived : public Base<T> { ... }
   ```

   模板声明、`template <typename T>`、类头 `class Derived`和基类列表 `public Base<T>` 进行了分析，但会将模板正文捕获为令牌流。

- 分析函数模板时，编译器仅分析函数签名。 永远不会分析函数体。 相反，它被捕获为令牌流。

因此，如果模板正文具有语法错误，但该模板永远无法实例化，则编译器不会诊断错误。

此行为的另一个效果是重载解决方案。 由于在实例化的位置扩展令牌流的方式，出现非标准行为。 在模板声明中看不到的符号在实例化时可能可见。 这意味着它们可以参与重载决策。 你可能会发现模板更改行为的方式取决于模板定义中不可见的代码，而不是标准。

例如，考虑此代码：

```cpp
// zctwophase.cpp
// To test options, compile by using
// cl /EHsc /nologo /W4 zctwophase.cpp
// cl /EHsc /nologo /W4 /permissive- zctwophase.cpp
// cl /EHsc /nologo /W4 /permissive- /Zc:twoPhase- zctwophase.cpp

#include <cstdio>

void func(long) { std::puts("Standard two-phase") ;}

template<typename T> void g(T x)
{
    func(0);
}

void func(int) { std::puts("Microsoft one-phase"); }

int main()
{
    g(6174);
}
```

下面是在将默认模式、一致性模式和一致性模式与 **/zc： twoPhase**选项一起使用时的输出：

```cmd
C:\Temp>cl /EHsc /nologo /W4 zctwophase.cpp && zctwophase
zctwophase.cpp
Microsoft one-phase

C:\Temp>cl /EHsc /nologo /W4 /permissive- zctwophase.cpp && zctwophase
zctwophase.cpp
Standard two-phase

C:\Temp>cl /EHsc /nologo /W4 /permissive- /Zc:twoPhase- zctwophase.cpp && zctwophase
zctwophase.cpp
Microsoft one-phase
```

当在 **/permissive-** 下的一致性模式下进行编译时，此程序将打印 "`Standard two-phase`"，因为当编译器到达模板时，`func` 的第二个重载不可见。 如果添加 **/zc： twoPhase**，程序将打印 "`Microsoft one-phase`"。 输出与未指定 **/permissive-** 时相同。

*依赖名称*是依赖于模板参数的名称。 在 **/zc： twoPhase-** 下，这些名称还具有不同的查找行为。 在一致性模式下，依赖名称不会绑定到模板的定义点。 相反，编译器会在实例化模板时对其进行查找。 对于具有依赖函数名称的函数调用，该名称将绑定到模板定义中的调用站点上可见的函数。 自变量相关查找的其他重载将添加到模板定义的点，并在模板实例化的点添加。

两阶段查找包括两个部分：模板定义期间查找非依赖项名称，以及在模板实例化期间查找依赖名称。 在 **/zc： twoPhase**下，编译器不会独立于未限定的查找执行参数相关查找。 也就是说，它不执行两阶段查找，因此重载决策的结果可能不同。

以下是另一示例：

```cpp
// zctwophase1.cpp
// To test options, compile by using
// cl /EHsc /W4 zctwophase1.cpp
// cl /EHsc /W4 /permissive- zctwophase1.cpp
// cl /EHsc /W4 /permissive- /Zc:twoPhase- zctwophase1.cpp

#include <cstdio>

void func(long) { std::puts("func(long)"); }

template <typename T> void tfunc(T t) {
    func(t);
}

void func(int) { std::puts("func(int)"); }

namespace NS {
    struct S {};
    void func(S) { std::puts("NS::func(NS::S)"); }
}

int main() {
    tfunc(1729);
    NS::S s;
    tfunc(s);
}
```

如果在不 **/permissive-** 的情况下进行编译，则将打印以下代码：

```Output
func(int)
NS::func(NS::S)
```

当用 **/permissive-** 编译但没有 **/zc： twoPhase**时，此代码将打印：

```Output
func(long)
NS::func(NS::S)
```

在用 **/permissive-** 和 **/zc： twoPhase**编译时，此代码将打印：

```Output
func(int)
NS::func(NS::S)
```

在 **/permissive-** 下的一致性模式下，调用 `tfunc(1729)` 解析 `void func(long)` 重载。 它不会解析 `void func(int)` 重载，如 **/zc： twoPhase-** 。 这是因为非限定的 `func(int)` 是在模板定义之后声明的，不能通过依赖于参数的查找找到。 但 `void func(S)` 参与参数依赖的查找，因此它将添加到调用 `tfunc(s)`的重载集，即使它是在模板函数之后声明的。

### <a name="update-your-code-for-two-phase-conformance"></a>更新代码以实现两阶段一致性

旧版本的编译器不需要关键字 `template` 和 `typename` 在C++标准需要它们的地方。 某些位置需要这些关键字，以消除编译器在查找的第一个阶段时应如何分析依赖名称。 例如：

`T::Foo<a || b>(c);`

一致性编译器会将 `Foo` 分析为 `T`范围内的变量，这意味着此代码是一个逻辑或表达式，其 `T::foo < a` 为左操作数，而 `b > (c)` 作为右操作数。 如果希望将 `Foo` 用作函数模板，则必须通过添加 `template` 关键字来指示它是模板：

`T::template Foo<a || b>(c);`

在 Visual Studio 2017 版本15.3 及更高版本中，当指定 **/permissive-** 和 **/zc： twoPhase**时，编译器将允许此代码，而不包含 `template` 关键字。 它将代码解释为带有 `a || b`的参数的函数模板调用，因为它仅以有限的方式分析模板。 在第一阶段中，根本不分析上述代码。 在第二阶段中，有足够的上下文可告诉 `T::Foo` 是模板而不是变量，因此编译器不会强制使用关键字。

此行为还可通过以下方式查看：在函数模板正文、初始值设定项、默认参数和 noexcept 参数中的名称之前消除关键字 `typename`。 例如：

```cpp
template<typename T>
typename T::TYPE func(typename T::TYPE*)
{
    /* typename */ T::TYPE i;
}
```

如果不在函数体中使用关键字 `typename`，则此代码将在 **/Permissive-/zc： twoPhase**下进行编译，但不会在 **/permissive-** 单独使用。 需要 `typename` 关键字来指示 `TYPE` 依赖于。 由于不在 **/zc： twoPhase-** 下分析正文，因此编译器不需要关键字。 在 **/permissive-** 一致性模式下，没有 `typename` 关键字的代码会生成错误。 若要将代码迁移到 Visual Studio 2017 版本15.3 和更高版本中的符合性，请在缺少 `typename` 关键字时将其插入。

同样，请看下面的代码示例：

```cpp
template<typename T>
typename T::template X<T>::TYPE func(typename T::TYPE)
{
    typename T::/* template */ X<T>::TYPE i;
}
```

在 **/Permissive-/zc： twoPhase**下，在较旧的编译器中，编译器仅要求第2行 `template` 关键字。 在一致性模式下，编译器现在还要求第4行中的 `template` 关键字，以指示 `T::X<T>` 为模板。 查找缺少此关键字的代码，并提供它以使你的代码符合标准。

有关一致性问题的详细信息，请参阅[ C++ Visual Studio 中的一致性改进](../../overview/cpp-conformance-improvements.md)和[非标准行为](../../cpp/nonstandard-behavior.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页” 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择“配置属性” > “C/C++” > “命令行”属性页。

1. 修改 "**附加选项**" 属性以包含 **/zc： twoPhase** ，然后选择 **"确定"** 。

## <a name="see-also"></a>另请参阅

[/Zc（一致性）](zc-conformance.md)

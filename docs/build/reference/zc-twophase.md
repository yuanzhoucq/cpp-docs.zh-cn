---
title: '/Zc: twophase-（禁用两阶段名称查找）'
ms.date: 03/06/2018
f1_keywords:
- twoPhase
- /Zc:twoPhase
- VC.Project.VCCLCompilerTool.EnforceTypeConversionRules
helpviewer_keywords:
- twoPhase
- disable two-phase name lookup
- /Zc:twoPhase
ms.openlocfilehash: b9e94f131448cb9be6c31962ecd19607ceb1b708
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58776032"
---
# <a name="zctwophase--disable-two-phase-name-lookup"></a>/Zc: twophase-（禁用两阶段名称查找）

当 **/zc: twophase-** 指定选项，编译器分析并不符合要求是相同版本的 Visual Studio，Visual Studio 2017 版本 15.3 中实例化类模板和函数模板。

## <a name="syntax"></a>语法

> **/Zc:twoPhase-**

## <a name="remarks"></a>备注

在 Visual Studio 2017 版本 15.3 及更高版本，默认情况下，编译器将使用两阶段名称查找有关模板的名称解析。 如果 **/zc: twophase-** 指定，则编译器将恢复为其以前不符合要求类模板和函数模板名称解析和替换的行为。

**/Zc: twophase-** 默认情况下未设置选项以启用不符合要求的行为。 [触发-](permissive-standards-conformance.md)选项隐式设置的符合标准的两阶段查找编译器行为，但它可以通过重写 **/zc: twophase-**。

在符合性模式下，在版本 10.0.15063.0 （创意者更新或 Redstone 2） 和更早版本的 Windows SDK 标头文件执行操作无法正常工作。 必须使用 **/zc: twophase-** 若要使用 Visual Studio 2017 版本 15.3 及更高版本时进行编译代码对这些 SDK 版本。 从版本 10.0.15254.0 （Redstone 3 或 Fall Creators Update） 开始的 Windows SDK 版本在符合性模式下正常工作，并且不需要 **/zc: twophase-** 选项。

使用 **/zc: twophase-** 如果代码需要的正确编译的旧行为。 强烈建议考虑更新您的代码以符合标准。

### <a name="compiler-behavior-under-zctwophase-"></a>/Zc: twophase-下的编译器行为

在 Visual Studio 2017 版本 15.3 中之前, 的编译器的版本以及何时 **/zc: twophase-** 指定，则编译器将使用此行为：

- 它将解析仅模板声明、 类 head 和基的类列表。 在模板正文被捕获为标记流。 没有函数体、 初始值设定项、 默认自变量或 noexcept 参数进行分析。 类模板是伪实例化暂定类型上要验证的类模板中的声明正确。 请考虑此类模板：

   ```cpp
   template <typename T> class Derived : public Base<T> { ... }
   ```

   模板声明中， `template <typename T`>，类头`class Derived`，和基类列表`public Base<T>`进行解析，但在模板正文被捕获为标记流。

- 当解析函数模板，编译器将分析仅在函数签名。 永远不会分析函数体。 相反，它被捕获为标记流。

因此，如果在模板正文有语法错误，并且永远不会实例化该模板，永远不会诊断错误。

此行为的另一个问题是重载解决方法。 由于在实例化的站点扩展标记流的方式，未在模板声明中可见的符号可能会在实例化时可见，并参与重载决策。 这可能会导致根据是不可见的模板已定义时，与标准的代码更改行为的模板。

例如，考虑此代码：

```cpp
#include <cstdio>

void func(void*) { std::puts("The call resolves to void*") ;}

template<typename T> void g(T x)
{
    func(0);
}

void func(int) { std::puts("The call resolves to int"); }

int main()
{
    g(3.14);
}
```

在编译时 **/zc: twophase-**，此程序将打印"调用解析为 int"。 在符合性模式下下**触发-**，此程序将"调用解析为 void *"，因为第二个重载的`func`当编译器遇到该模板不可见。

*依赖项名称*，依赖于模板参数的名称具有也是在不同的查找行为 **/zc: twophase-**。 在符合性模式下，依赖名称未在模板的定义绑定。 相反，这些名称查找模板实例化时。 对于具有依赖的函数名称的函数调用，绑定到组的可见在模板的定义中，按上述方式进行调用的函数的名称。 在模板定义的点和实例化模板时的点添加从参数相关的查找其他重载。 两阶段查找这两个阶段是在针对依赖名称时的模板实例化的模板定义和查找时的非依赖名称的查询。 下 **/zc: twophase-**，编译器不会执行依赖于自变量查找单独从普通的非限定查找 （即，它不会执行两阶段查找），因此重载决策的结果可能不同。

下面是另一个示例：

```cpp
// zctwophase1.cpp
// Compile by using
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

当编译不含 **/zc: twophase-**，这将打印

```Output
func(long)
NS::func(NS::S)
```

编译时使用 **/zc: twophase-**，这将打印

```Output
func(int)
NS::func(NS::S)
```

在符合性模式下**触发-**，在调用`tfunc(1729)`解析为`void func(long)`重载，不`void func(int)`下重载 **/zc: twophase-**，因为非限定`func(int)`模板的定义之后声明和通过参数相关的查找找不到。 但是`void func(S)`参与参数相关的查找，因此将其添加到调用设置的重载`tfunc(s)`即使模板函数之后声明。

### <a name="update-your-code-for-two-phase-conformance"></a>更新你的代码为两阶段的一致性

较旧版本的编译器不需要关键字`template`和`typename`无处不在 c + + 标准要求它们。 在某些位置中需要这些关键字消除歧义编译器在查找的第一阶段期间分析依赖名称的方式。 例如：

`T::Foo<a || b>(c);`

符合编译器分析`Foo`中的作用域的变量`T`，这意味着此代码是一个逻辑-或带有表达式`T::foo < a`作为左操作数和`b > (c)`为右操作数。 如果您希望使用`Foo`作为函数模板，您必须指示这是一个模板，通过添加`template`关键字：

`T::template Foo<a || b>(c);`

在 Visual Studio 2017 版本 15.3 中之前, 的版本以及何时 **/zc: twophase-** 指定，编译器允许此代码而无需`template`关键字并将其解释为具有的自变量的函数模板调用`a || b`，因为它会分析模板以非常有限的方式。 上面的代码不是在所有分析在第一个阶段。 第二个阶段，没有足够的上下文来进行分辨`T::Foo`是模板而不是变量，因此编译器不强制使用的关键字。

此行为也可以查看通过消除关键字`typename`之前中函数模板正文、 初始值设定项、 默认自变量和 noexcept 自变量的名称。 例如：

```cpp
template<typename T>
typename T::TYPE func(typename T::TYPE*)
{
    /* typename */ T::TYPE i;
}
```

如果不使用关键字`typename`在函数正文中，此代码编译下 **/zc: twophase-**，但不是下**触发-**。 `typename`指示所需的关键字`TYPE`依赖。 因为在不分析正文 **/zc: twophase-**，编译器不需要关键字。 在中**触发-** 符合性模式下，代码而无需`typename`关键字会生成错误。 若要将代码迁移到 Visual Studio 2017 版本 15.3 和更高版本，插入`typename`是缺少的关键字。

同样，请考虑此代码示例：

```cpp
template<typename T>
typename T::template X<T>::TYPE func(typename T::TYPE)
{
    typename T::/* template */ X<T>::TYPE i;
}
```

下 **/zc: twophase-** ，并且在较旧编译器中，编译器只需要`template`第 2 行的关键字。 默认情况下，并在符合性模式下，编译器现在还要求`template`第 4，指示行的关键字`T::X<T>`是一个模板。 查找缺少此关键字的代码并将其以使符合标准代码提供。

有关符合性问题的详细信息，请参阅[c + + 在 Visual Studio 中的符合性改进](../../overview/cpp-conformance-improvements-2017.md)并[非标准行为](../../cpp/nonstandard-behavior.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[Visual Studio 中的设置 c + + 编译器和生成属性](../working-with-project-properties.md)。

1. 选择**配置属性** > **C/c + +** > **命令行**属性页。

1. 修改**其他选项**属性以包含 **/zc: twophase-** ，然后选择**确定**。

## <a name="see-also"></a>请参阅

[/Zc（一致性）](zc-conformance.md)<br/>

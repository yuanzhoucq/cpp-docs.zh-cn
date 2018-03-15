---
title: "/Zc:twoPhase-（禁用两阶段的名称查找） |Microsoft 文档"
ms.custom: 
ms.date: 03/06/2018
ms.technology:
- cpp-tools
ms.topic: article
f1_keywords:
- twoPhase
- /Zc:twoPhase
- VC.Project.VCCLCompilerTool.EnforceTypeConversionRules
dev_langs:
- C++
helpviewer_keywords:
- twoPhase
- disable two-phase name lookup
- /Zc:twoPhase
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4582a5532d9fd410224ee4174ca3973bfe539656
ms.sourcegitcommit: eeb2b5ad8d3d22514a7b9bd7d756511b69ae0ccf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2018
---
# <a name="zctwophase--disable-two-phase-name-lookup"></a>/Zc:twoPhase-（禁用两阶段的名称查找）

当**/Zc:twoPhase-**指定选项，编译器分析，并在与 Visual Studio 2017 版本 15.3 之前的 Visual Studio 的版本相同的不符合要求方式中实例化类模板和函数模板。 

## <a name="syntax"></a>语法

> **/Zc:twoPhase-**

## <a name="remarks"></a>备注

在 Visual Studio 2017 版本 15.3 及更高版本，默认情况下，编译器会使用两阶段的名称查找模板名称解析。 如果**/Zc:twoPhase-**指定，则编译器将还原到其以前不符合要求类模板和函数模板名称解析和替换的行为。

**/Zc:twoPhase-**默认情况下不设置选项以使不符合要求的行为。 [/ 宽松-](permissive-standards-conformance.md)选项隐式设置的符合标准的两阶段查找编译器行为，但它可以通过重写**/Zc:twoPhase-**。

版本 10.0.15063.0 （创建者更新或 Redstone 2） 和早期版本中的 Windows SDK 标头文件在标准的模式下不正常运行。 必须使用**/Zc:twoPhase-**来编译这些 SDK 版本的代码，当你使用 Visual Studio 2017 版本 15.3 和更高版本。 从版本 10.0.15254.0 （Redstone 3 或回退创建者更新） 开始的 Windows sdk 的版本一致性方式会正常工作，并且不需要**/Zc:twoPhase-**选项。

使用**/Zc:twoPhase-**如果代码需要这一旧行为正确编译。 强烈建议考虑更新代码以符合标准。

### <a name="compiler-behavior-under-zctwophase-"></a>下 /Zc:twoPhase-编译器行为

在 Visual Studio 2017 版本 15.3 之前, 的编译器的版本以及何时**/Zc:twoPhase-**指定，则编译器将使用此行为：

- 分析仅模板声明、 类 head 和基的类列表。 模板正文被捕获为令牌流。 分析没有函数体、 初始值设定项、 默认自变量或 noexcept 自变量。 类模板是伪实例化的试探性的类型，可以验证类模板中的声明正确。 请考虑此类模板：

   ```cpp
   template <typename T> class Derived : public Base<T> { ... }
   ```

   模板声明中， `template <typename T`>，类头`class Derived`，和基类列表`public Base<T>`分析的但模板正文被捕获为令牌流。

- 在分析函数模板时，编译器将分析仅对函数签名。 永远不会分析函数体。 相反，它被捕获为令牌流。

因此，如果模板正文具有语法错误，该模板不会实例化，并将永远不会接受为诊断错误。

另一个影响此行为是重载解决方法。 由于在实例化的站点扩展令牌流的方法，未在模板声明中可见的符号可能在实例化可见并参与重载决策。 这可能会导致更改基于代码时不可见定义模板，与标准相反的行为的模板。

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

在编译时**/Zc:twoPhase-**，此程序将打印"调用将解析为 int"。 在下的一致性模式下**/ 宽松-**，此程序将打印"调用将解析为 void *"，因为第二个重载的`func`当编译器遇到模板不可见。

*依赖名称*，依赖于模板参数的名称具有查找行为，也是在下不同**/Zc:twoPhase-**。 在一致性模式下，不会在模板的定义绑定依赖名称。 相反，这些名称查找模板实例化时。 对于具有依赖的函数名称的函数调用，绑定到的一套可见在模板的定义中，按上面所述进行调用的函数的名称。 从依赖于自变量的查找的其他重载将添加到模板定义的点和其中的模板进行实例化的点。 两阶段查找两个阶段是在针对依赖名称时的模板实例化的模板定义和查找时为非依赖名称查找。 下**/Zc:twoPhase-**，编译器不会执行依赖于自变量的查找单独于普通的、 不合格的查找 （即，它不执行两阶段查找），因此重载决策的结果可能不同。

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

而无需在编译时**/Zc:twoPhase-**，这将打印

```Output
func(long)
NS::func(NS::S)
```

如果使用编译的**/Zc:twoPhase-**，这将打印

```Output
func(int)
NS::func(NS::S)
```

在下的一致性模式下**/ 宽松-**，调用`tfunc(1729)`解析为`void func(long)`超负荷运转，不`void func(int)`重载为在**/Zc:twoPhase-**，这是因为非限定`func(int)`后模板的定义声明并在通过依赖于自变量的查找找不到。 但是`void func(S)`参与依赖于自变量的查找，因此它添加到设置的调用的重载`tfunc(s)`即使模板函数之后声明。

### <a name="update-your-code-for-two-phase-conformance"></a>更新你的代码的两阶段一致性的工具

较旧版本的编译器不需要关键字`template`和`typename`无处不在 c + + 标准要求它们。 在某些位置中需要这些关键字消除歧义编译器查找的第一个阶段分析依赖名称的方式。 例如:

`T::Foo<a || b>(c);`

符合的编译器分析`Foo`作为的作用域中的变量`T`，这意味着此代码是逻辑的或带有表达式`T::foo < a`与左操作数和`b > (c)`与右操作数。 如果您想要使用`Foo`作为函数模板，您必须指示这是一个模板，通过添加`template`关键字：

`T::template Foo<a || b>(c);`

在 Visual Studio 2017 版本 15.3 之前, 的版本以及何时**/Zc:twoPhase-**指定，编译器允许此代码，而没有`template`关键字和将其解释为对具有的自变量的函数模板的调用`a || b`，因为它会分析方式非常有限的模板。 上面的代码不在所有分析在第一阶段。 在第二个阶段，没有足够的背景知识以告知`T::Foo`是模板，而不是变量，因此编译器不会强制使用的关键字。

通过消除关键字，也会看到此行为`typename`之前在函数模板正文、 初始值设定项、 默认自变量和 noexcept 自变量的名称。 例如:

```cpp
template<typename T>
typename T::TYPE func(typename T::TYPE*)
{
    /* typename */ T::TYPE i;
}
```

如果你不使用关键字`typename`在函数正文中，此代码将编译下**/Zc:twoPhase-**，但不是在**/ 宽松-**。 `typename`指示所需的关键字`TYPE`依赖。 因为正文不分析下**/Zc:twoPhase-**，编译器不需要关键字。 在**/ 宽松-**一致性模式时，代码，而没有`typename`关键字会产生错误。 若要将你的代码迁移到 Visual Studio 2017 版本 15.3 和场外，插入`typename`是缺少的关键字。

同样，请考虑此代码示例：

```cpp
template<typename T>
typename T::template X<T>::TYPE func(typename T::TYPE)
{
    typename T::/* template */ X<T>::TYPE i;
}
```

下**/Zc:twoPhase-** ，并且在较旧的编译器中，编译器只需要`template`上第 2 行的关键字。 默认情况下，而在标准的模式下，编译器现在还要求`template`上行 4，则指示关键字`T::X<T>`是一个模板。 查找缺少此关键字的代码并将其以使符合标准代码提供。

有关一致性问题的详细信息，请参阅[Visual Studio 中的 c + + 一致性改进](../../cpp-conformance-improvements-2017.md)和[非标准行为](../../cpp/nonstandard-behavior.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 选择**配置属性** > **C/c + +** > **命令行**属性页。

1. 修改**其他选项**属性以包含**/Zc:twoPhase-** ，然后选择**确定**。

## <a name="see-also"></a>请参阅

[/Zc（一致性）](../../build/reference/zc-conformance.md)<br/>

---
title: /Zc:throwingNew （假定运算符新的引发操作）
ms.date: 03/01/2018
f1_keywords:
- throwingNew
- /Zc:throwingNew
helpviewer_keywords:
- -Zc compiler options (C++)
- throwingNew
- Assume operator new Throws
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 20ff0101-9677-4d83-8c7b-8ec9ca49f04f
ms.openlocfilehash: 782cb55d30bfb11f55a0074a5c3245dd389323ed
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50561221"
---
# <a name="zcthrowingnew-assume-operator-new-throws"></a>/Zc:throwingNew （假定运算符新的引发操作）

当 **/Zc:throwingNew**指定选项，编译器优化对调用`operator new`跳过检查返回的 null 指针。 此选项告知编译器假定所有链接的实现`operator new`和自定义分配器符合 c + + 标准，并在分配失败时引发。 默认情况下，在 Visual Studio 中，编译器将保守地生成 null 检查 (**/Zc:throwingNew-**) 的这些调用，因为用户可以将链接的非引发实现`operator new`或编写自定义分配器例程返回 null 指针。

## <a name="syntax"></a>语法

> **/Zc:throwingNew**[**-**]

## <a name="remarks"></a>备注

因为 ISO C + + 98，标准已指定，默认值[运算符 new](../../standard-library/new-operators.md#op_new)引发`std::bad_alloc`时内存分配失败。 Visual Studio 6.0 到 Visual c + + 版本分配失败时返回 null 指针。 在 Visual Studio 2002 年开始`operator new`符合标准，并在失败时引发。 若要支持使用较旧的分配样式的代码，Visual Studio 提供的实现，可链接`operator new`中失败时返回一个 null 指针的 nothrownew.obj。 默认情况下，编译器还会生成防御性 null 检查，以防止这些较旧样式的分配器而即时故障导致失败。 **/Zc:throwingNew**选项告知编译器将忽略这些 null 检查，假定所有链接内存分配器符合标准。 这不适用于显式非引发`operator new`重载，它使用类型的其他参数来声明`std::nothrow_t`和具有显式`noexcept`规范。

从概念上讲，若要在可用存储中创建一个对象，编译器生成代码，以分配其内存，然后调用其构造函数来初始化内存。 因为 Visual c + + 编译器通常不能确定是否此代码将链接到不符合要求，非引发的分配器，默认情况下它还会生成 null 检查之前调用的构造函数。 这可以防止 null 指针取消引用在构造函数调用中，如果非引发分配失败。 在大多数情况下，这些检查都是不必要的因为默认`operator new`分配器引发而不是返回 null 指针。 检查还具有令人遗憾的副作用。 膨胀的代码大小，从而它们、 它们填满分支预测，和他们会禁止 devirtualization 或通过从已初始化的对象的 const 传播等其他有用的编译器优化。 仅对支持链接到的代码存在支票*nothrownew.obj*具有自定义不符合要求或`operator new`实现。 如果不使用非一致性`operator new`，我们建议你使用 **/Zc:throwingNew**来优化您的代码。

**/Zc:throwingNew**选项默认情况下处于关闭状态，不受[触发的](permissive-standards-conformance.md)选项。

如果使用链接时间代码生成 (LTCG) 进行编译，不需要指定 **/Zc:throwingNew**。 如果使用 LTCG 编译代码时，编译器可以检测到默认情况下，符合`operator new`使用实现。 如果是这样，编译器将省略 null 检查自动。 链接器寻找 **/ThrowingNew**标志是为了告知如果的实现`operator new`为一致性。 可以通过在你自定义的运算符的新实现的源中包含此指令指定此链接器标志：

```cpp
#pragma comment(linker, "/ThrowingNew")
```

有关 Visual C++ 中一致性问题的详细信息，请参阅 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。

## <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 从**配置**下拉列表菜单中，选择**所有配置**。

1. 选择**配置属性** > **C/c + +** > **命令行**属性页。

1. 修改**其他选项**属性以包含 **/Zc:throwingNew**或 **/Zc:throwingNew-** ，然后选择**确定**。

## <a name="see-also"></a>请参阅

[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)<br/>
[/Zc（一致性）](../../build/reference/zc-conformance.md)<br/>
[noexcept (C++)](../../cpp/noexcept-cpp.md)<br/>
[异常规范 (throw) (C++)](../../cpp/exception-specifications-throw-cpp.md)<br/>
[终止 （异常）](../../standard-library/exception-functions.md#terminate)<br/>

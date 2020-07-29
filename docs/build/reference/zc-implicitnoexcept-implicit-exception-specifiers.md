---
title: /Zc:implicitNoexcept（隐式异常说明符）
ms.date: 03/06/2018
f1_keywords:
- /Zc:implicitNoexcept
helpviewer_keywords:
- /Zc:implicitNoexcept
- Zc:implicitNoexcept
- -Zc:implicitNoexcept
ms.assetid: 71807652-6f9d-436b-899e-f52daa6f500b
ms.openlocfilehash: bb1a632ffe684ac0777d0089a2edfd514bf66d0b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223793"
---
# <a name="zcimplicitnoexcept-implicit-exception-specifiers"></a>/Zc:implicitNoexcept（隐式异常说明符）

指定 **/zc： implicitNoexcept**选项时，编译器会将隐式[noexcept](../../cpp/noexcept-cpp.md)异常说明符添加到编译器定义的特殊成员函数和用户定义的析构函数和释放函数。 默认情况下， **/zc： implicitNoexcept**已启用符合 ISO c + + 11 标准。 如果关闭此选项，则会 **`noexcept`** 对用户定义的析构函数和 dealloacators 以及编译器定义的特殊成员函数禁用隐式。

## <a name="syntax"></a>语法

> **/Zc： implicitNoexcept**[ **-** ]

## <a name="remarks"></a>备注

**/Zc： implicitNoexcept**告知编译器遵循 ISO c + + 11 标准的15.4 节。 它隐式向 **`noexcept`** 每个隐式声明或显式默认的特殊成员函数（默认构造函数、复制构造函数、移动构造函数、析构函数、复制赋值运算符或移动赋值运算符）以及每个用户定义的析构函数或释放器函数添加一个异常说明符。 用户定义的释放函数具有隐式 `noexcept(true)` 异常说明符。 对于用户定义的析构函数，隐式异常说明符为 `noexcept(true)`，除非包含的成员类或基类具有非 `noexcept(true)` 的析构函数。 对于编译器生成的特殊成员函数，如果此函数直接调用的任何函数实际上是 `noexcept(false)`，则隐式异常说明符为 `noexcept(false)`。 否则，隐式异常说明符为 `noexcept(true)`。

编译器不会为使用显式 **`noexcept`** 或 **`throw`** 说明符或特性声明的函数生成隐式异常说明符 `__declspec(nothrow)` 。

默认情况下， **/zc： implicitNoexcept**已启用。 [/Permissive-](permissive-standards-conformance.md)选项不影响 **/zc： implicitNoexcept**。

如果通过指定 **/zc： implicitNoexcept**禁用了选项，则编译器不会生成任何隐式异常说明符。 此行为与 Visual Studio 2013 相同，其中没有异常说明符的析构函数和释放函数可能具有 **`throw`** 语句。 默认情况下，在指定 **/zc： implicitNoexcept**时，如果 **`throw`** 在运行时遇到具有隐式说明符的函数， `noexcept(true)` 则会导致立即调用 `std::terminate` ，并且不保证异常处理程序的正常展开行为。 为了帮助识别这种情况，编译器将生成[编译器警告（等级1） C4297](../../error-messages/compiler-warnings/compiler-warning-level-1-c4297.md)。 如果 **`throw`** 是特意的，则建议将函数声明更改为具有显式说明符， `noexcept(false)` 而不是使用 **/zc： implicitNoexcept-**。

此示例演示当设置或禁用 **/zc： implicitNoexcept**选项时，不具有显式异常说明符的用户定义析构函数的行为方式。 若要在设置时显示行为，请使用进行编译 `cl /EHsc /W4 implicitNoexcept.cpp` 。 若要显示禁用时的行为，请使用进行编译 `cl /EHsc /W4 /Zc:implicitNoexcept- implicitNoexcept.cpp` 。

```cpp
// implicitNoexcept.cpp
// Compile by using: cl /EHsc /W4 implicitNoexcept.cpp
// Compile by using: cl /EHsc /W4 /Zc:implicitNoexcept- implicitNoexcept.cpp

#include <iostream>
#include <cstdlib>      // for std::exit, EXIT_FAILURE, EXIT_SUCCESS
#include <exception>    // for std::set_terminate

void my_terminate()
{
    std::cout << "Unexpected throw caused std::terminate" << std::endl;
    std::cout << "Exit returning EXIT_FAILURE" << std::endl;
    std::exit(EXIT_FAILURE);
}

struct A {
    // Explicit noexcept overrides implicit exception specification
    ~A() noexcept(false) {
        throw 1;
    }
};

struct B : public A {
    // Compiler-generated ~B() definition inherits noexcept(false)
    ~B() = default;
};

struct C {
    // By default, the compiler generates an implicit noexcept(true)
    // specifier for this user-defined destructor. To enable it to
    // throw an exception, use an explicit noexcept(false) specifier,
    // or compile by using /Zc:implicitNoexcept-
    ~C() {
        throw 1; // C4297, calls std::terminate() at run time
    }
};

struct D : public C {
    // This destructor gets the implicit specifier of its base.
    ~D() = default;
};

int main()
{
    std::set_terminate(my_terminate);

    try
    {
        {
            B b;
        }
    }
    catch (...)
    {
        // exception should reach here in all cases
        std::cout << "~B Exception caught" << std::endl;
    }
    try
    {
        {
            D d;
        }
    }
    catch (...)
    {
        // exception should not reach here if /Zc:implicitNoexcept
        std::cout << "~D Exception caught" << std::endl;
    }
    std::cout << "Exit returning EXIT_SUCCESS" << std::endl;
    return EXIT_SUCCESS;
}
```

当使用默认设置 **/zc： implicitNoexcept**进行编译时，该示例生成以下输出：

```Output
~B Exception caught
Unexpected throw caused std::terminate
Exit returning EXIT_FAILURE
```

当使用设置 **/zc： implicitNoexcept-** 编译时，该示例生成以下输出：

```Output
~B Exception caught
~D Exception caught
Exit returning EXIT_SUCCESS
```

有关 Visual C++ 中一致性问题的详细信息，请参阅 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择 "**配置属性**" "  >  **c/c + +**  >  **命令行**" 属性页。

1. 修改 "**附加选项**" 属性以包括 **/zc： implicitNoexcept**或 **/zc： ImplicitNoexcept** ，然后选择 **"确定"**。

## <a name="see-also"></a>另请参阅

[/Zc（一致性）](zc-conformance.md)<br/>
[noexcept](../../cpp/noexcept-cpp.md)<br/>
[异常规范（throw）](../../cpp/exception-specifications-throw-cpp.md)<br/>
[终止](../../standard-library/exception-functions.md#terminate)<br/>

---
title: '/Zc: implicitnoexcept （隐式异常说明符） |Microsoft 文档'
ms.custom: ''
ms.date: 03/06/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Zc:implicitNoexcept
dev_langs:
- C++
helpviewer_keywords:
- /Zc:implicitNoexcept
- Zc:implicitNoexcept
- -Zc:implicitNoexcept
ms.assetid: 71807652-6f9d-436b-899e-f52daa6f500b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7e420017056d6857a2809ce6eb85fe99b6f3866f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="zcimplicitnoexcept-implicit-exception-specifiers"></a>/Zc:implicitNoexcept（隐式异常说明符）

当 **/zc: implicitnoexcept**指定选项，编译器将添加一种隐式[noexcept](../../cpp/noexcept-cpp.md)异常说明符到编译器定义的特殊成员函数和用户定义的析构函数和释放。 默认情况下， **/zc: implicitnoexcept**启用以符合 ISO C + + 11 标准。 关闭此选项将对用户定义的析构函数和释放函数以及编译器定义的特殊成员函数禁用隐式 `noexcept`。

## <a name="syntax"></a>语法

> **/Zc:implicitNoexcept**[**-**]

## <a name="remarks"></a>备注

**/Zc: implicitnoexcept**告知编译器遵循 ISO C + + 11 标准的第 15.4 节。 它将隐式添加`noexcept`到每个隐式声明或显式设置的默认特殊成员函数异常说明符 — 默认构造函数中，复制构造函数、 移动构造函数、 析构函数、 复制赋值运算符或移动赋值运算符-和每个用户定义的析构函数或释放函数。 用户定义的释放函数具有隐式 `noexcept(true)` 异常说明符。 对于用户定义的析构函数，隐式异常说明符为 `noexcept(true)`，除非包含的成员类或基类具有非 `noexcept(true)` 的析构函数。 对于编译器生成的特殊成员函数，如果此函数直接调用的任何函数实际上是 `noexcept(false)`，则隐式异常说明符为 `noexcept(false)`。 否则，隐式异常说明符为 `noexcept(true)`。

编译器不会为通过使用显式 `noexcept` 或 `throw` 说明符或 `__declspec(nothrow)` 属性声明的函数生成隐式异常说明符。

默认情况下， **/zc: implicitnoexcept**已启用。 [/ 宽松-](permissive-standards-conformance.md)选项不影响 **/zc: implicitnoexcept**。

如果此选项已禁用通过指定 **/zc: implicitnoexcept-**，由编译器生成不隐式异常说明符。 此行为与 Visual Studio 2013 相同，其中不具有异常说明符的析构函数和释放函数可具有相同的 `throw` 语句。 默认情况下，以及何时 **/zc: implicitnoexcept**指定，如果`throw`语句遇到运行时在具有隐式函数`noexcept(true)`说明符，它会导致立即调用`std::terminate`，和不保证异常处理程序的正常展开行为。 为了帮助识别这种情况下，编译器将生成[编译器警告 （等级 1） C4297](../../error-messages/compiler-warnings/compiler-warning-level-1-c4297.md)。 如果`throw`是有意的我们建议你更改函数声明，以使用显式`noexcept(false)`而不是使用说明符 **/zc: implicitnoexcept-**。

此示例演示用户定义的析构函数，没有显式异常说明符的行为方式时 **/zc: implicitnoexcept**选项进行设置或禁用。 若要显示的行为设置时，通过使用`cl /EHsc /W4 implicitNoexcept.cpp`。 若要显示禁用时的行为，编译使用`cl /EHsc /W4 /Zc:implicitNoexcept- implicitNoexcept.cpp`。

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

通过使用默认设置在编译时 **/zc: implicitnoexcept**，该示例生成此输出：

```Output
~B Exception caught
Unexpected throw caused std::terminate
Exit returning EXIT_FAILURE
```

通过使用的设置在编译时 **/zc: implicitnoexcept-**，该示例生成此输出：

```Output
~B Exception caught
~D Exception caught
Exit returning EXIT_SUCCESS
```

有关 Visual C++ 中一致性问题的详细信息，请参阅 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 选择**配置属性** > **C/c + +** > **命令行**属性页。

1. 修改**其他选项**属性以包含 **/zc: implicitnoexcept**或 **/zc: implicitnoexcept-** ，然后选择**确定**。

## <a name="see-also"></a>请参阅

[/Zc（一致性）](../../build/reference/zc-conformance.md)<br/>
[noexcept](../../cpp/noexcept-cpp.md)<br/>
[异常规范 (throw)](../../cpp/exception-specifications-throw-cpp.md)<br/>
[terminate](../../standard-library/exception-functions.md#terminate)<br/>

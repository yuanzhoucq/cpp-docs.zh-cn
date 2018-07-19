---
title: '-Zc: noexceptTypes （C + + 17 noexcept 规则） |Microsoft 文档'
ms.date: 11/14/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Zc:noexceptTypes
dev_langs:
- C++
helpviewer_keywords:
- /Zc:noexceptTypes
- Zc:noexceptTypes
- -Zc:noexceptTypes
ms.assetid: 1cbf7e3c-0f82-4f91-84dd-612bcf26d2c6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 25ad2a662af2cda49e3e8dd8c769fa75dafee94b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379544"
---
# <a name="zcnoexcepttypes-c17-noexcept-rules"></a>/Zc:noexceptTypes （c + + 17 noexcept 规则）

C + + 17 标准使`throw()`的别名作为`noexcept`，删除`throw(<type list>)`和`throw(...)`，和允许某些类型包括`noexcept`。 在符合到 C + + 14 或更早版本的代码中，这会导致大量的源兼容性问题。 **/Zc:noexceptTypes**选项可以指定符合 C + + 17 标准也可以允许的 C + + 14 及更早版本行为，在 C + + 17 模式下编译代码时。

## <a name="syntax"></a>语法

> **/Zc:noexceptTypes**[-]

## <a name="remarks"></a>备注

当 **/Zc:noexceptTypes**指定选项，编译器符合 C + + 17 标准，并将[throw （)](../../cpp/exception-specifications-throw-cpp.md)的别名作为[noexcept](../../cpp/noexcept-cpp.md)，删除`throw(<type list>)`和`throw(...)`，和允许某些类型包括`noexcept`。 **/Zc:noexceptTypes**选项才可用[/std:c + + 17](std-specify-language-standard-version.md)或[/std:latest](std-specify-language-standard-version.md)已启用。 **/Zc:noexceptTypes**默认启用以符合 ISO C + + 17 标准。 [/ 宽松-](permissive-standards-conformance.md)选项不影响 **/Zc:noexceptTypes**。 关闭此选项通过指定 **/Zc:noexceptTypes-** 以恢复到 C + + 14 的行为`noexcept`时 **/std::C + + 17**或 **/std::latest**指定。

从 Visual Studio 2017 版本 15.5 开始，c + + 编译器诊断声明 C + + 17 模式中的多个不匹配的异常规范，或者当[/ 宽松-](permissive-standards-conformance.md)指定选项。

此示例演示如何使用异常说明符声明时行为 **/Zc:noexceptTypes**选项进行设置或禁用。 若要显示的行为设置时，通过使用`cl /EHsc /W4 noexceptTypes.cpp`。 若要显示禁用时的行为，编译使用`cl /EHsc /W4 /Zc:noexceptTypes- noexceptTypes.cpp`。

```cpp
// noexceptTypes.cpp
// Compile by using: cl /EHsc /W4 noexceptTypes.cpp
// Compile by using: cl /EHsc /W4 /Zc:noexceptTypes- noexceptTypes.cpp

void f() throw();    // equivalent to void f() noexcept;
void f() { }         // warning C5043
void g() throw(...); // warning C5040

struct A
{
    virtual void f() throw();
};

struct B : A
{
    virtual void f() { } // error C2694
};
```

通过使用默认设置在编译时 **/Zc:noexceptTypes**，该示例生成列出的警告。 若要更新你的代码，请改用以下：

```cpp
void f() noexcept;
void f() noexcept { }
void g() noexcept(false);

struct A
{
    virtual void f() noexcept;
};

struct B : A
{
    virtual void f() noexcept { }
};
```

有关 Visual C++ 中一致性问题的详细信息，请参阅 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 选择**配置属性** > **C/c + +** > **命令行**属性页。

1. 修改**其他选项**属性以包含 **/Zc:noexceptTypes**或 **/Zc:noexceptTypes-** ，然后选择**确定**。

## <a name="see-also"></a>请参阅

[/Zc（一致性）](../../build/reference/zc-conformance.md)  
[noexcept](../../cpp/noexcept-cpp.md)  
[异常规范 (throw)](../../cpp/exception-specifications-throw-cpp.md)  

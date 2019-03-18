---
title: /Zc:noexceptTypes （c + + 17 noexcept 规则）
ms.date: 11/14/2017
f1_keywords:
- /Zc:noexceptTypes
helpviewer_keywords:
- /Zc:noexceptTypes
- Zc:noexceptTypes
- -Zc:noexceptTypes
ms.assetid: 1cbf7e3c-0f82-4f91-84dd-612bcf26d2c6
ms.openlocfilehash: 28e06f54049d36262134b6be7eadb0e6e5349a45
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57812104"
---
# <a name="zcnoexcepttypes-c17-noexcept-rules"></a>/Zc:noexceptTypes （c + + 17 noexcept 规则）

C + + 17 标准使`throw()`的别名作为`noexcept`，删除`throw(<type list>)`并`throw(...)`，并允许某些类型，以便包括`noexcept`。 这会导致符合 c++14 或更早版本的代码中的一系列源兼容性问题。 **/Zc:noexceptTypes**选项可以指定针对 C + + 17 标准符合性，或在 C + + 17 模式下编译代码时允许 C + + 14 及更早版本的行为。

## <a name="syntax"></a>语法

> **/Zc:noexceptTypes**[-]

## <a name="remarks"></a>备注

当 **/Zc:noexceptTypes**指定选项，编译器符合 C + + 17 标准，并将[throw （)](../../cpp/exception-specifications-throw-cpp.md)作为别名[noexcept](../../cpp/noexcept-cpp.md)，删除`throw(<type list>)`并`throw(...)`，并允许某些类型，以便包括`noexcept`。 **/Zc:noexceptTypes**选项才可用[/std: c + + 17](std-specify-language-standard-version.md)或[/std:latest](std-specify-language-standard-version.md)已启用。 **/Zc:noexceptTypes**默认情况下启用符合 ISO C + + 17 标准。 [触发-](permissive-standards-conformance.md)选项不会影响 **/Zc:noexceptTypes**。 关闭此选项通过指定 **/Zc:noexceptTypes-** 若要还原到 C + + 14 的行为`noexcept`时 **/std::C + + 17**或 **/std::latest**指定。

从 Visual Studio 2017 版本 15.5 开始，c + + 编译器诊断 c++17 模式中的声明中的多个不匹配的异常规范，或者当[触发-](permissive-standards-conformance.md)指定选项。

此示例演示如何使用异常说明符声明时行为 **/Zc:noexceptTypes**设置或禁用选项。 若要显示的行为设置时，通过使用编译`cl /EHsc /W4 noexceptTypes.cpp`。 若要显示禁用时的行为，编译使用`cl /EHsc /W4 /Zc:noexceptTypes- noexceptTypes.cpp`。

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

使用默认设置在编译时 **/Zc:noexceptTypes**，该示例生成列出的警告。 若要更新你的代码，请改用以下：

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

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[Visual Studio 中的设置 c + + 编译器和生成属性](../working-with-project-properties.md)。

1. 选择**配置属性** > **C/c + +** > **命令行**属性页。

1. 修改**其他选项**属性以包含 **/Zc:noexceptTypes**或 **/Zc:noexceptTypes-** ，然后选择**确定**。

## <a name="see-also"></a>请参阅

[/Zc（一致性）](zc-conformance.md)<br/>
[noexcept](../../cpp/noexcept-cpp.md)<br/>
[异常规范 (throw)](../../cpp/exception-specifications-throw-cpp.md)

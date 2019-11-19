---
title: /Zc:noexceptTypes（C++17 noexcept 规则）
ms.date: 11/14/2017
f1_keywords:
- /Zc:noexceptTypes
helpviewer_keywords:
- /Zc:noexceptTypes
- Zc:noexceptTypes
- -Zc:noexceptTypes
ms.assetid: 1cbf7e3c-0f82-4f91-84dd-612bcf26d2c6
ms.openlocfilehash: 35bea7c2c629c615c60a6136f289b6b11926c054
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/05/2019
ms.locfileid: "73624868"
---
# <a name="zcnoexcepttypes-c17-noexcept-rules"></a>/Zc:noexceptTypes（C++17 noexcept 规则）

C + + 17 标准使 `throw()` `noexcept`的别名，删除 `throw(<type list>)` 和 `throw(...)`，并允许某些类型包含 `noexcept`。 此更改可能会导致与 c + + 14 或更早版本的代码中出现大量源兼容性问题。 **/Zc： noexceptTypes**选项指定与 c + + 17 标准的一致性。 **/Zc： noexceptTypes-** 在 c + + 17 模式下编译代码时，允许 c + + 14 及更早的行为。

## <a name="syntax"></a>语法

> **/Zc： noexceptTypes**[-]

## <a name="remarks"></a>备注

指定 **/zc： noexceptTypes**选项时，编译器将遵循 c + + 17 标准并将[throw （）](../../cpp/exception-specifications-throw-cpp.md)视为[noexcept](../../cpp/noexcept-cpp.md)的别名，删除 `throw(<type list>)` 和 `throw(...)`，并允许某些类型包含 `noexcept`。 只有在[/std： c + + 17](std-specify-language-standard-version.md)或[/std：](std-specify-language-standard-version.md) enabled 处于启用状态时， **/zc： noexceptTypes**选项才可用。 **/Zc：** 默认情况下启用 noexceptTypes 以符合 ISO c + + 17 标准。 [/Permissive-](permissive-standards-conformance.md)选项不影响 **/zc： noexceptTypes**。 通过指定 **/zc： noexceptTypes-** 在 **/std： c + + 17**或 **/std：最新**时，指定/Zc：-恢复为 c + + 14 的 `noexcept` 行为，关闭此选项。

从 Visual Studio 2017 版本15.5 开始， C++编译器会在 c + + 17 模式下或在你指定[/permissive-](permissive-standards-conformance.md)选项时诊断更多不匹配的异常规范。

此示例演示当设置或禁用 **/zc： noexceptTypes**选项时，具有异常说明符的声明的行为方式。 若要在设置时显示行为，请使用 `cl /EHsc /W4 noexceptTypes.cpp`进行编译。 若要显示禁用时的行为，请使用 `cl /EHsc /W4 /Zc:noexceptTypes- noexceptTypes.cpp`进行编译。

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

当使用默认设置 **/zc： noexceptTypes**进行编译时，该示例将生成列出的警告。 若要更新你的代码，请改用以下代码：

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

1. 打开项目的“属性页” 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择“配置属性” > “C/C++” > “命令行”属性页。

1. 修改 "**附加选项**" 属性以包括 **/zc： noexceptTypes**或 **/zc： NoexceptTypes** ，然后选择 **"确定"** 。

## <a name="see-also"></a>请参阅

[/Zc （一致性）](zc-conformance.md)\
[noexcept](../../cpp/noexcept-cpp.md)\
[异常规范（throw）](../../cpp/exception-specifications-throw-cpp.md)

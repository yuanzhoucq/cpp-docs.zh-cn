---
title: /Zc:noexceptTypes（C++17 noexcept 规则）
ms.date: 06/04/2020
f1_keywords:
- /Zc:noexceptTypes
helpviewer_keywords:
- /Zc:noexceptTypes
- Zc:noexceptTypes
- -Zc:noexceptTypes
ms.assetid: 1cbf7e3c-0f82-4f91-84dd-612bcf26d2c6
ms.openlocfilehash: 0f833209938ccc09cbc37235788b6f719d4d12d4
ms.sourcegitcommit: fe146adb3a02872538637196bb3c45aeeeaaf5c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84506866"
---
# <a name="zcnoexcepttypes-c17-noexcept-rules"></a>/Zc:noexceptTypes（C++17 noexcept 规则）

C + + 17 标准 `throw()` 为创建别名 `noexcept` ，删除 `throw(` *`type-list`* `)` 和 `throw(...)` ，并允许特定类型包括 `noexcept` 。 此更改可能会导致与 c + + 14 或更早版本的代码中出现大量源兼容性问题。 **`/Zc:noexceptTypes`** 选项指定与 c + + 17 标准的一致性。 **`/Zc:noexceptTypes-`** 在 c + + 17 模式下编译代码时，允许 c + + 14 及更早的行为。

## <a name="syntax"></a>语法

> **`/Zc:noexceptTypes`**\[**`-`**]

## <a name="remarks"></a>注解

如果 **`/Zc:noexceptTypes`** 指定了选项，则编译器将遵循 c + + 17 标准并将视为的 [**`throw()`**](../../cpp/exception-specifications-throw-cpp.md) 别名 [**`noexcept`**](../../cpp/noexcept-cpp.md) ，删除 `throw(` *`type-list`* `)` 和 `throw(...)` ，并允许某些类型包括 **`noexcept`** 。 **`/Zc:noexceptTypes`** 仅当启用了或时，选项才可用 [**`/std:c++17`**](std-specify-language-standard-version.md) [**`/std:c++latest`**](std-specify-language-standard-version.md) 。 **`/Zc:noexceptTypes`** 默认情况下，启用以符合 ISO c + + 17 标准。 此 [**`/permissive-`**](permissive-standards-conformance.md) 选项不会影响 **`/Zc:noexceptTypes`** 。 通过指定 **`/Zc:noexceptTypes-`** 以恢复到 **`noexcept`** 指定或时的 c + + 14 行为，可关闭此选项 **`/std:c++17`** **`/std:c++latest`** 。

从 Visual Studio 2017 版本15.5 开始，c + + 编译器将在 c + + 17 模式下的声明中诊断更不匹配的异常规范，或在指定选项时进行诊断 [**`/permissive-`**](permissive-standards-conformance.md) 。

此示例演示当设置或禁用该选项时，具有异常说明符的声明的行为方式 **`/Zc:noexceptTypes`** 。 若要在设置时显示行为，请使用进行编译 `cl /EHsc /W4 noexceptTypes.cpp` 。 若要显示禁用时的行为，请使用进行编译 `cl /EHsc /W4 /Zc:noexceptTypes- noexceptTypes.cpp` 。

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

当使用默认设置进行编译时 **`/Zc:noexceptTypes`** ，该示例将生成列出的警告。 若要更新你的代码，请改用以下代码：

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

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择 "**配置属性**" "  >  **c/c + +**  >  **命令行**" 属性页。

1. 修改 "**附加选项**" 属性以包含 *`/Zc:noexceptTypes`* 或 *`/Zc:noexceptTypes-`* ，然后选择 **"确定"**。

## <a name="see-also"></a>另请参阅

[**`/Zc`** 度](zc-conformance.md)\
[noexcept](../../cpp/noexcept-cpp.md)\
[异常规范 (throw)](../../cpp/exception-specifications-throw-cpp.md)

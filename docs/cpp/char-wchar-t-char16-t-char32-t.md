---
title: char、wchar_t、char16_t、char32_t
ms.date: 02/14/2018
ms.assetid: 6b33e9f5-455b-4e49-8f12-a150cbfe2e5b
ms.openlocfilehash: 6efbae1b8f6155410b823f1abef35c3dec90d458
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232334"
---
# <a name="char-wchar_t-char16_t-char32_t"></a>char、wchar_t、char16_t、char32_t

类型 **`char`** 、 **`wchar_t`** **`char16_t`** 和 **`char32_t`** 是内置类型，它们表示字母数字字符以及非字母数字的标志符号和非打印字符。

## <a name="syntax"></a>语法

```cpp
char     ch1{ 'a' };  // or { u8'a' }
wchar_t  ch2{ L'a' };
char16_t ch3{ u'a' };
char32_t ch4{ U'a' };
```

## <a name="remarks"></a>备注

**`char`** 类型为 C 和 c + + 中的原始字符类型。 类型 **`unsigned char`** 通常用于表示一个字节，该*字节*不是 c + + 中的内置类型。 **`char`** 类型可用于存储 ASCII 字符集中的字符或任意 ISO-8859 字符集，以及单个字节的多字节字符（例如，shift-jis 或 Unicode 字符集的 utf-8 编码）。 类型为的字符串 **`char`** 称为*窄*字符串，即使用于对多字节字符进行编码。 在 Microsoft 编译器中， **`char`** 是一个8位类型。

**`wchar_t`** 类型是实现定义的宽字符类型。 在 Microsoft 编译器中，它表示用于将 Unicode 编码为 UTF-16LE 的16位宽字符，Windows 操作系统上的本机字符类型。 通用 C 运行时（UCRT）库函数的宽字符版本使用 **`wchar_t`** 及其指针和数组类型作为参数和返回值，这与本机 WINDOWS API 的宽字符版本相同。

**`char16_t`** 和 **`char32_t`** 类型分别表示16位和32位宽字符。 以 UTF-16 编码的 unicode 可以存储在 **`char16_t`** 类型中，而编码为 utf-32 的 unicode 可以存储在 **`char32_t`** 类型中。 这些类型的字符串 **`wchar_t`** 都被称为*宽*字符串，但术语通常是专门引用类型为的字符串 **`wchar_t`** 。

在 c + + 标准库中， `basic_string` 类型专用于窄字符串和宽字符串。 当字符为类型、字符为类型、字符为类型时， `std::string` **`char`** `std::u16string` **`char16_t`** `std::u32string` **`char32_t`** 以及 `std::wstring` 当字符为类型 **`wchar_t`** 时，使用。 表示文本的其他类型，包括 `std::stringstream` 和 `std::cout` 的专用化的窄字符串和宽字符串。

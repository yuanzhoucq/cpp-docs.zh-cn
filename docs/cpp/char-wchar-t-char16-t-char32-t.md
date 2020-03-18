---
title: char、wchar_t、char16_t、char32_t
ms.date: 02/14/2018
ms.assetid: 6b33e9f5-455b-4e49-8f12-a150cbfe2e5b
ms.openlocfilehash: a518f24973aaddff59b97f104d9d912e4a2bedce
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447154"
---
# <a name="char-wchar_t-char16_t-char32_t"></a>char、wchar_t、char16_t、char32_t

类型**char**、 **wchar_t**、 **char16_t**和**char32_t**是表示字母数字字符以及非字母数字字符和非打印字符的内置类型。

## <a name="syntax"></a>语法

```cpp
char     ch1{ 'a' };  // or { u8'a' }
wchar_t  ch2{ L'a' };
char16_t ch3{ u'a' };
char32_t ch4{ U'a' };
```

## <a name="remarks"></a>备注

**Char**类型是 C 和C++中的原始字符类型。 类型**无符号字符**通常用于表示字节，该*字节*不是中C++的内置类型。 **Char**类型可用于存储 ASCII 字符集或任意 ISO-8859 字符集中的字符，以及多字节字符（如 shift-jis）或 Unicode 字符集的 utf-8 编码等各个字节的单个字节。 **Char**类型的字符串被称为*窄*字符串，即使用于编码多字节字符也是如此。 在 Microsoft 编译器中， **char**是一个8位类型。

**Wchar_t**类型是实现定义的宽字符类型。 在 Microsoft 编译器中，它表示用于将 Unicode 编码为 UTF-16LE 的16位宽字符，Windows 操作系统上的本机字符类型。 通用 C 运行时（UCRT）库函数的宽字符版本使用**wchar_t**及其指针和数组类型作为参数和返回值，就像使用本机 Windows API 的宽字符版本一样。

**Char16_t**和**char32_t**类型分别表示16位和32位宽字符。 以 UTF-16 编码的 unicode 可以存储在**char16_t**类型中，并且**Char32_t**可将 unicode 编码为32类型。 这些类型和**wchar_t**的字符串均称为*宽*字符串，但术语通常是专门引用**wchar_t**类型的字符串。

在C++标准库中，每个 `basic_string` 类型都专用于窄字符串和宽字符串。 当字符的类型为**char**时，使用 `std::string`，`std::u16string` 字符类型**char16_t**时，`std::u32string` 字符类型**char32_t**时使用，当字符类型 `std::wstring` 时，则使用**wchar_t。** 表示文本的其他类型，包括 `std::stringstream` 和 `std::cout` 专用于窄字符串和宽字符串。
---
title: '&lt;string_view&gt; typedef'
ms.date: 04/19/2019
f1_keywords:
- xstring/std::string_view
- xstring/std::u16string_view
- xstring/std::u32string_view
- xstring/std::wstring_view
ms.openlocfilehash: c3367afe1353ac70abb74a59658a255614ac8470
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459182"
---
# <a name="ltstring_viewgt-typedefs"></a>&lt;string_view&gt; typedef

||||
|-|-|-|
|[string_view](#string_view)|[u16string_view](#u16string_view)|[u32string_view](#u32string_view)|
|[wstring_view](#wstring_view)|

## <a name="string_view"></a> string_view

一种类型，该类型描述类模板与**char**类型的元素[basic_string_view](../standard-library/basic-string-view-class.md)的专用化。

```cpp
typedef basic_string_view<char, char_traits<char>> string_view;
```

### <a name="remarks"></a>备注

以下是等效声明：

```cpp
string_view str("Hello");

basic_string_view<char> str("Hello");
```

关于字符串构造函数的列表，请参阅 [basic_string:: basic_string](../standard-library/basic-string-class.md#basic_string)。

## <a name="u16string_view"></a> u16string_view

一种类型，该类型描述类模板与`char16_t`类型的元素 [basic_string_view](../standard-library/basic-string-view-class.md) 的专用化。

```cpp
typedef basic_string_view<char16_t, char_traits<char16_t>> u16string_view;
```

### <a name="remarks"></a>备注

关于字符串构造函数的列表，请参阅 [basic_string:: basic_string](../standard-library/basic-string-class.md#basic_string)。

## <a name="u32string_view"></a> u32string_view

一种类型，该类型描述类模板与`char32_t`类型的元素 [basic_string_view](../standard-library/basic-string-view-class.md) 的专用化。

```cpp
typedef basic_string_view<char32_t, char_traits<char32_t>> u32string_view;
```

### <a name="remarks"></a>备注

关于字符串构造函数的列表，请参阅 [basic_string:: basic_string](../standard-library/basic-string-class.md#basic_string)。

## <a name="wstring_view"></a>  wstring_view

一种类型，该类型描述类模板[basic_string_view](../standard-library/basic-string-view-class.md)的类型为**wchar_t**的元素的专用化。

```cpp
typedef basic_string_view<wchar_t, char_traits<wchar_t>> wstring_view;
```

### <a name="remarks"></a>备注

以下是等效声明：

```cpp
wstring_view wstr(L"Hello");

basic_string_view<wchar_t> wstr(L"Hello");
```

关于字符串构造函数的列表，请参阅 [basic_string:: basic_string](../standard-library/basic-string-class.md#basic_string)。

> [!NOTE]
> **Wchar_t**的大小在 Windows 上是两个字节，但对于所有平台，这并不一定是这种情况。 如果你需要一个 string_view 宽字符类型，该类型的宽度保证在所有平台上保持不变，请使用[u16string_view](../standard-library/string-view-typedefs.md#u16string_view)或[u32string_view](../standard-library/string-view-typedefs.md#u32string_view)。

## <a name="see-also"></a>请参阅

[\<string_view>](../standard-library/string-view.md)

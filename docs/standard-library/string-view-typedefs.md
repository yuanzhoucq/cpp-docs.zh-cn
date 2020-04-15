---
title: '&lt;string_view&gt;类型定义'
ms.date: 04/19/2019
f1_keywords:
- xstring/std::string_view
- xstring/std::u16string_view
- xstring/std::u32string_view
- xstring/std::wstring_view
ms.openlocfilehash: 0ec278484b7c1c9887771f6cbe7e5d0b05205dd7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376679"
---
# <a name="ltstring_viewgt-typedefs"></a>&lt;string_view&gt;类型定义

||||
|-|-|-|
|[string_view](#string_view)|[u16string_view](#u16string_view)|[u32string_view](#u32string_view)|
|[wstring_view](#wstring_view)|

## <a name="string_view"></a><a name="string_view"></a>string_view

描述类模板的专门化[basic_string_view](../standard-library/basic-string-view-class.md)类型**为 char。**

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

## <a name="u16string_view"></a><a name="u16string_view"></a>u16string_view

描述[类模板的](../standard-library/basic-string-view-class.md)专门化basic_string_view的类型，具有类型`char16_t`的元素。

```cpp
typedef basic_string_view<char16_t, char_traits<char16_t>> u16string_view;
```

### <a name="remarks"></a>备注

关于字符串构造函数的列表，请参阅 [basic_string:: basic_string](../standard-library/basic-string-class.md#basic_string)。

## <a name="u32string_view"></a><a name="u32string_view"></a>u32string_view

描述[类模板的](../standard-library/basic-string-view-class.md)专门化basic_string_view的类型，具有类型`char32_t`的元素。

```cpp
typedef basic_string_view<char32_t, char_traits<char32_t>> u32string_view;
```

### <a name="remarks"></a>备注

关于字符串构造函数的列表，请参阅 [basic_string:: basic_string](../standard-library/basic-string-class.md#basic_string)。

## <a name="wstring_view"></a><a name="wstring_view"></a>wstring_view

描述类模板的专门化的类型[basic_string_view，](../standard-library/basic-string-view-class.md)该类型**wchar_t**的元素。

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
> **wchar_t**的大小在 Windows 上为两个字节，但并非所有平台都如此。 如果需要string_view宽字符类型，其宽度保证在所有平台上保持不变，请使用[u16string_view](../standard-library/string-view-typedefs.md#u16string_view)或[u32string_view](../standard-library/string-view-typedefs.md#u32string_view)。

## <a name="see-also"></a>另请参阅

[\<string_view>](../standard-library/string-view.md)

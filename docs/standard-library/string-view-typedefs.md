---
title: '&lt;string_view&gt; typedefs'
ms.date: 04/19/2019
f1_keywords:
- xstring/std::string_view
- xstring/std::u16string_view
- xstring/std::u32string_view
- xstring/std::wstring_view
ms.openlocfilehash: 16d7ba49facf24dcffb7df444e445d83d92255e0
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "64346965"
---
# <a name="ltstringviewgt-typedefs"></a>&lt;string_view&gt; typedefs

||||
|-|-|-|
|[string_view](#string_view)|[u16string_view](#u16string_view)|[u32string_view](#u32string_view)|
|[wstring_view](#wstring_view)|

## <a name="string_view"></a> string_view

该类型描述的类模板专用化[basic_string_view](../standard-library/basic-string-view-class.md)类型的元素**char**。

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

该类型描述的类模板专用化[basic_string_view](../standard-library/basic-string-view-class.md)类型的元素`char16_t`。

```cpp
typedef basic_string_view<char16_t, char_traits<char16_t>> u16string_view;
```

### <a name="remarks"></a>备注

关于字符串构造函数的列表，请参阅 [basic_string:: basic_string](../standard-library/basic-string-class.md#basic_string)。

## <a name="u32string_view"></a> u32string_view

该类型描述的类模板专用化[basic_string_view](../standard-library/basic-string-view-class.md)类型的元素`char32_t`。

```cpp
typedef basic_string_view<char32_t, char_traits<char32_t>> u32string_view;
```

### <a name="remarks"></a>备注

关于字符串构造函数的列表，请参阅 [basic_string:: basic_string](../standard-library/basic-string-class.md#basic_string)。

## <a name="wstring_view"></a>  wstring_view

该类型描述的类模板专用化[basic_string_view](../standard-library/basic-string-view-class.md)类型的元素**wchar_t**。

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
> 大小**wchar_t**是在 Windows 上的两个字节，但并不一定所有平台这种情况。 如果您需要一个 string_view 宽字符类型保证保持不变，则在所有平台上宽度，使用[u16string_view](../standard-library/string-view-typedefs.md#u16string_view)或[u32string_view](../standard-library/string-view-typedefs.md#u32string_view)。

## <a name="see-also"></a>请参阅

[\<string_view>](../standard-library/string-view.md)<br/>

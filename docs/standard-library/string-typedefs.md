---
title: '&lt;string&gt; typedef | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- string/std::string
- string/std::u16string
- string/std::u32string
- string/std::wstring
ms.assetid: fdca01e9-f2f1-4b59-abda-0093d760b3cc
ms.openlocfilehash: 2d3f63ab29049e5f5a928186ba033bfe041bcfc1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="ltstringgt-typedefs"></a>&lt;string&gt; typedef

||||
|-|-|-|
|[string](#string)|[u16string](#u16string)|[u32string](#u32string)|
|[wstring](#wstring)|

## <a name="string"></a>  string

用 `char` 类型的元素描述 [basic_string](../standard-library/basic-string-class.md) 模板类的专用化的类型。

专用化 `basic_string` 的其他 typedef 包括 [wstring](../standard-library/string-typedefs.md#wstring)、[u16string](../standard-library/string-typedefs.md#u16string) 和 [u32string](../standard-library/string-typedefs.md#u32string)。

```cpp
typedef basic_string<char, char_traits<char>, allocator<char>> string;
```

### <a name="remarks"></a>备注

以下是等效声明：

```cpp
string str("");

basic_string<char> str("");
```

关于字符串构造函数的列表，请参阅 [basic_string:: basic_string](../standard-library/basic-string-class.md#basic_string)。

## <a name="u16string"></a>  u16string

用 `char16_t` 类型的元素描述 [basic_string](../standard-library/basic-string-class.md) 模板类的专用化的类型。

专用化 `basic_string` 的其他 typedef 包括 [wstring](../standard-library/string-typedefs.md#wstring)、[string](../standard-library/string-typedefs.md#string) 和 [u32string](../standard-library/string-typedefs.md#u32string)。

```cpp
typedef basic_string<char16_t, char_traits<char16_t>, allocator<char16_t>> u16string;
```

### <a name="remarks"></a>备注

关于字符串构造函数的列表，请参阅 [basic_string:: basic_string](../standard-library/basic-string-class.md#basic_string)。

## <a name="u32string"></a>  u32string

用 `char32_t` 类型的元素描述 [basic_string](../standard-library/basic-string-class.md) 模板类的专用化的类型。

专用化 `basic_string` 的其他 typedef 包括 [tring](../standard-library/string-typedefs.md#string)、[u16string](../standard-library/string-typedefs.md#u16string) 和 [wstring](../standard-library/string-typedefs.md#wstring)。

```cpp
typedef basic_string<char32_t, char_traits<char32_t>, allocator<char32_t>> u32string;
```

### <a name="remarks"></a>备注

关于字符串构造函数的列表，请参阅 [basic_string:: basic_string](../standard-library/basic-string-class.md#basic_string)。

## <a name="wstring"></a>  wstring

用 `wchar_t` 类型的元素描述 [basic_string](../standard-library/basic-string-class.md) 模板类的专用化的类型。

专用化 `basic_string` 的其他 typedef 包括 [string](../standard-library/string-typedefs.md#string)、[u16string](../standard-library/string-typedefs.md#u16string) 和 [u32string](../standard-library/string-typedefs.md#u32string)。

```cpp
typedef basic_string<wchar_t, char_traits<wchar_t>, allocator<wchar_t>> wstring;
```

### <a name="remarks"></a>备注

以下是等效声明：

```cpp
wstring wstr(L"");

basic_string<wchar_t> wstr(L"");
```

关于字符串构造函数的列表，请参阅 [basic_string:: basic_string](../standard-library/basic-string-class.md#basic_string)。

> [!NOTE]
> `wchar_t` 的大小是由实现定义的。 如果你的代码的大小取决于 `wchar_t`，请检查你平台的实现（例如，使用 `sizeof(wchar_t)`）。 如果需要保证宽度在所有平台上一致的字符串字符类型，请使用 [string](../standard-library/string-typedefs.md#string)、[u16string](../standard-library/string-typedefs.md#u16string) 或 [u32string](../standard-library/string-typedefs.md#u32string)。

## <a name="see-also"></a>请参阅

[\<string>](../standard-library/string.md)<br/>

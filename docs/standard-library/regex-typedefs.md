---
title: '&lt;regex&gt; typedefs'
ms.date: 11/04/2016
f1_keywords:
- regex/std::cmatch
- regex/std::cregex_iterator
- regex/std::cregex_token_iterator
- regex/std::csub_match
- regex/std::regex
- regex/std::smatch
- regex/std::sregex_iterator
- regex/std::sregex_token_iterator
- regex/std::ssub_match
- regex/std::wcmatch
- regex/std::wcregex_iterator
- regex/std::wcregex_token_iterator
- regex/std::wcsub_match
- regex/std::wregex
- regex/std::wsmatch
- regex/std::wsregex_iterator
- regex/std::wsregex_token_iterator
- regex/std::wssub_match
ms.assetid: e6a69067-106c-4a24-9e08-7c867a3a2260
ms.openlocfilehash: 5dbda2df4877da7594dd633e9f203a3780b4adb1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368543"
---
# <a name="ltregexgt-typedefs"></a>&lt;regex&gt; typedefs

||||
|-|-|-|
|[cmatch](#cmatch)|[cregex_iterator](#cregex_iterator)|[cregex_token_iterator](#cregex_token_iterator)|
|[csub_match](#csub_match)|[Regex](#regex)|[smatch](#smatch)|
|[sregex_iterator](#sregex_iterator)|[sregex_token_iterator](#sregex_token_iterator)|[ssub_match](#ssub_match)|
|[wcmatch](#wcmatch)|[wcregex_iterator](#wcregex_iterator)|[wcregex_token_iterator](#wcregex_token_iterator)|
|[wcsub_match](#wcsub_match)|[wregex](#wregex)|[wsmatch](#wsmatch)|
|[wsregex_iterator](#wsregex_iterator)|[wsregex_token_iterator](#wsregex_token_iterator)|[wssub_match](#wssub_match)|

## <a name="cmatch-typedef"></a><a name="cmatch"></a>cmatch 类型 def

char match_results 的类型定义。

```cpp
typedef match_results<const char*> cmatch;
```

### <a name="remarks"></a>备注

该类型描述了类模板的专门化[match_results类](../standard-library/match-results-class.md)的类型迭代器`const char*`。

## <a name="cregex_iterator-typedef"></a><a name="cregex_iterator"></a>cregex_iterator 类型 def

char regex_iterator 的类型定义。

```cpp
typedef regex_iterator<const char*> cregex_iterator;
```

### <a name="remarks"></a>备注

该类型描述了类模板的专门化[regex_iterator类](../standard-library/regex-iterator-class.md)的类型迭代器`const char*`。

## <a name="cregex_token_iterator-typedef"></a><a name="cregex_token_iterator"></a>cregex_token_iterator 类型 def

char regex_token_iterator 的类型定义

```cpp
typedef regex_token_iterator<const char*> cregex_token_iterator;
```

### <a name="remarks"></a>备注

该类型描述了类模板的专门化[regex_token_iterator类](../standard-library/regex-token-iterator-class.md)的类型迭代器`const char*`。

## <a name="csub_match-typedef"></a><a name="csub_match"></a>csub_match 类型def

char sub_match 的类型定义。

```cpp
typedef sub_match<const char*> csub_match;
```

### <a name="remarks"></a>备注

该类型描述了类模板的专门化[sub_match类](../standard-library/sub-match-class.md)的类型迭代器`const char*`。

## <a name="regex-typedef"></a><a name="regex"></a>正则类型def

char basic_regex 的类型定义。

```cpp
typedef basic_regex<char> regex;
```

### <a name="remarks"></a>备注

该类型描述了类模板的专门化[basic_regex类](../standard-library/basic-regex-class.md)类型**字符**的元素。

> [!NOTE]
> 用于 `regex` 时，高位字符的结果不可预测。 0 到 127 范围之外的值可能会导致未定义的行为。

## <a name="smatch-typedef"></a><a name="smatch"></a>比赛类型def

字符串 match_results 的类型定义。

```cpp
typedef match_results<string::const_iterator> smatch;
```

### <a name="remarks"></a>备注

该类型描述了类模板的专门化[match_results类](../standard-library/match-results-class.md)的类型迭代器`string::const_iterator`。

## <a name="sregex_iterator-typedef"></a><a name="sregex_iterator"></a>sregex_iterator 类型def

字符串 regex_iterator. 的类型定义。

```cpp
typedef regex_iterator<string::const_iterator> sregex_iterator;
```

### <a name="remarks"></a>备注

该类型描述了类模板的专门化[regex_iterator类](../standard-library/regex-iterator-class.md)的类型迭代器`string::const_iterator`。

## <a name="sregex_token_iterator-typedef"></a><a name="sregex_token_iterator"></a>sregex_token_iterator 类型 def

字符串 regex_token_iterator 的类型定义。

```cpp
typedef regex_token_iterator<string::const_iterator> sregex_token_iterator;
```

### <a name="remarks"></a>备注

该类型描述了类模板的专门化[regex_token_iterator类](../standard-library/regex-token-iterator-class.md)的类型迭代器`string::const_iterator`。

## <a name="ssub_match-typedef"></a><a name="ssub_match"></a>ssub_match 类型 def

字符串 sub_match 的类型定义。

```cpp
typedef sub_match<string::const_iterator> ssub_match;
```

### <a name="remarks"></a>备注

该类型描述了类模板的专门化[sub_match类](../standard-library/sub-match-class.md)的类型迭代器`string::const_iterator`。

## <a name="wcmatch-typedef"></a><a name="wcmatch"></a>wcmatch 类型 def

wchar_t match_results 的类型定义。

```cpp
typedef match_results<const wchar_t *> wcmatch;
```

### <a name="remarks"></a>备注

该类型描述了类模板的专门化[match_results类](../standard-library/match-results-class.md)的类型迭代器`const wchar_t*`。

## <a name="wcregex_iterator-typedef"></a><a name="wcregex_iterator"></a>wcregex_iterator 类型 def

wchar_t regex_iterator 的类型定义。

```cpp
typedef regex_iterator<const wchar_t*> wcregex_iterator;
```

### <a name="remarks"></a>备注

该类型描述了类模板的专门化[regex_iterator类](../standard-library/regex-iterator-class.md)的类型迭代器`const wchar_t*`。

## <a name="wcregex_token_iterator-typedef"></a><a name="wcregex_token_iterator"></a>wcregex_token_iterator 类型 def

wchar_t regex_token_iterator. 的类型定义。

```cpp
typedef regex_token_iterator<const wchar_t*> wcregex_token_iterator;
```

### <a name="remarks"></a>备注

该类型描述了类模板的专门化[regex_token_iterator类](../standard-library/regex-token-iterator-class.md)的类型迭代器`const wchar_t*`。

## <a name="wcsub_match-typedef"></a><a name="wcsub_match"></a>wcsub_match 类型 def

wchar_t sub_match 的类型定义。

```cpp
typedef sub_match<const wchar_t*> wcsub_match;
```

### <a name="remarks"></a>备注

该类型描述了类模板的专门化[sub_match类](../standard-library/sub-match-class.md)的类型迭代器`const wchar_t*`。

## <a name="wregex-typedef"></a><a name="wregex"></a>wregex 类型 def

wchar_t basic_regex 的类型定义。

```cpp
typedef basic_regex<wchar_t> wregex;
```

### <a name="remarks"></a>备注

该类型描述了类模板[basic_regex类](../standard-library/basic-regex-class.md)的专门化 **，wchar_t**类型元素。

## <a name="wsmatch-typedef"></a><a name="wsmatch"></a>wsmatch 类型 def

wstring match_results 的类型定义。

```cpp
typedef match_results<wstring::const_iterator> wsmatch;
```

### <a name="remarks"></a>备注

该类型描述了类模板的专门化[match_results类](../standard-library/match-results-class.md)的类型迭代器`wstring::const_iterator`。

## <a name="wsregex_iterator-typedef"></a><a name="wsregex_iterator"></a>wsregex_iterator类型

wstring regex_iterator 的类型定义。

```cpp
typedef regex_iterator<wstring::const_iterator> wsregex_iterator;
```

### <a name="remarks"></a>备注

该类型描述了类模板的专门化[regex_iterator类](../standard-library/regex-iterator-class.md)的类型迭代器`wstring::const_iterator`。

## <a name="wsregex_token_iterator-typedef"></a><a name="wsregex_token_iterator"></a>wsregex_token_iterator类型def

wstring regex_token_iterator 的类型定义。

```cpp
typedef regex_token_iterator<wstring::const_iterator> wsregex_token_iterator;
```

### <a name="remarks"></a>备注

该类型描述了类模板的专门化[regex_token_iterator类](../standard-library/regex-token-iterator-class.md)的类型迭代器`wstring::const_iterator`。

## <a name="wssub_match-typedef"></a><a name="wssub_match"></a>wssub_match 类型def

wstring sub_match 的类型定义。

```cpp
typedef sub_match<wstring::const_iterator> wssub_match;
```

### <a name="remarks"></a>备注

该类型描述了类模板的专门化[sub_match类](../standard-library/sub-match-class.md)的类型迭代器`wstring::const_iterator`。

## <a name="see-also"></a>另请参阅

[\<正则>](../standard-library/regex.md)\
[regex_constants类](../standard-library/regex-constants-class.md)\
[regex_error类](../standard-library/regex-error-class.md)\
[\<正则表达式>函数](../standard-library/regex-functions.md)\
[regex_iterator类](../standard-library/regex-iterator-class.md)\
[\<正则>运算符](../standard-library/regex-operators.md)\
[regex_token_iterator类](../standard-library/regex-token-iterator-class.md)\
[regex_traits类](../standard-library/regex-traits-class.md)

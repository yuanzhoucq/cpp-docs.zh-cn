---
title: '&lt;regex&gt; 函数 | Microsoft Docs'
ms.custom: ''
ms.date: 09/10/2018
ms.topic: reference
f1_keywords:
- regex/std::regex_match
- regex/std::regex_replace
- regex/std::regex_search
- regex/std::swap
dev_langs:
- C++
ms.assetid: 91a8314b-6f7c-4e33-b7d6-d8583dd75585
helpviewer_keywords:
- std::regex_match [C++]
- std::regex_replace [C++]
- std::regex_search [C++]
- std::swap [C++]
- std::swap [C++]
ms.openlocfilehash: b3b5171e60e9f9348a4e4d86d0b8032db7eb4726
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45726539"
---
# <a name="ltregexgt-functions"></a>&lt;regex&gt; 函数

|||
|-|-|
|[regex_match](#regex_match)|测试正则表达式是否与整个目标字符串相匹配。|
|[regex_replace](#regex_replace)|替换匹配正则表达式。|
|[regex_search](#regex_search)|搜索正则表达式匹配项。|
|[swap](#swap)|交换两个`basic_regex`或`match_results`对象。|

## <a name="regex_match"></a>  regex_match

测试正则表达式是否与整个目标字符串相匹配。

```cpp
// (1)
template <class BidIt, class Alloc, class Elem, class RXtraits, class Alloc2>
bool regex_match(
    BidIt first,
    Bidit last,
    match_results<BidIt, Alloc>& match,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

// (2)
template <class BidIt, class Elem, class RXtraits, class Alloc2>
bool regex_match(
    BidIt first,
    Bidit last,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

// (3)
template <class Elem, class Alloc, class RXtraits, class Alloc2>
bool regex_match(
    const Elem *ptr,
    match_results<const Elem*, Alloc>& match,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

// (4)
template <class Elem, class RXtraits, class Alloc2>
bool regex_match(
    const Elem *ptr,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

// (5)
template <class IOtraits, class IOalloc, class Alloc, class Elem, class RXtraits, class Alloc2>
bool regex_match(
    const basic_string<Elem, IOtraits, IOalloc>& str,
    match_results<typename basic_string<Elem, IOtraits, IOalloc>::const_iterator, Alloc>& match,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

// (6)
template <class IOtraits, class IOalloc, class Elem, class RXtraits, class Alloc2>
bool regex_match(
    const basic_string<Elem, IOtraits, IOalloc>& str,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);
```

### <a name="parameters"></a>参数

*BidIt*<br/>
子匹配项的迭代器类型。 一般情况下的这个`string::const_iterator`， `wstring::const_iterator`，`const char*`或`const wchar_t*`。

*分配*<br/>
匹配结果分配器类。

*Elem*<br/>
要匹配的元素的类型。 一般情况下这是`string`， `wstring`，`char*`或`wchar_t*`。

*RXtraits*<br/>
元素的特征类。

*Alloc2*<br/>
正则表达式分配器类。

*IOtraits*<br/>
字符串特征类。

*IOalloc*<br/>
字符串分配器类。

*flags*<br/>
匹配标志。

*first*<br/>
要匹配的序列的开头。

*最后一个*<br/>
要匹配的序列的结尾。

*match*<br/>
匹配结果。 对应于 Elem 类型： [smatch](../standard-library/regex-typedefs.md#smatch)有关`string`， [wsmatch](../standard-library/regex-typedefs.md#wsmatch)有关`wstring`， [cmatch](../standard-library/regex-typedefs.md#cmatch)为`char*`或[wcmatch](../standard-library/regex-typedefs.md#wcmatch)为`wchar_t*`。

*ptr*<br/>
指向要匹配的序列开头的指针。 如果*ptr*是`char*`，然后使用`cmatch`和`regex`。 如果*ptr*是`wchar_t*`然后使用`wcmatch`和`wregex`。

*re*<br/>
要匹配的正则表达式。 类型`regex`有关`string`并`char*`，或`wregex`有关`wstring`和`wchar_t*`。

*str*<br/>
要匹配的字符串。 为类型相对应*Elem*。

### <a name="remarks"></a>备注

每个模板函数返回 true，才在整个操作数序列*str*与正则表达式参数完全匹配*re*。 使用[regex_search](../standard-library/regex-functions.md#regex_search)匹配目标序列中的子字符串和`regex_iterator`查找多个匹配项。 采用 `match_results` 对象的函数将其成员设置为反映匹配是否成功，以及如果成功，正则表达式中的各种捕获组所捕获的内容。

采用 `match_results` 对象的函数将其成员设置为反映匹配是否成功，以及如果成功，正则表达式中的各种捕获组所捕获的内容。

### <a name="example"></a>示例

```cpp
// std__regex__regex_match.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

using namespace std;

int main()
{
    // (1) with char*
    // Note how const char* requires cmatch and regex
    const char *first = "abc";
    const char *last = first + strlen(first);
    cmatch narrowMatch;
    regex rx("a(b)c");

    bool found = regex_match(first, last, narrowMatch, rx);
    if (found)
        wcout << L"Regex found in abc" << endl;

    // (2) with std::wstring
    // Note how wstring requires wsmatch and wregex.
    // Note use of const iterators cbegin() and cend().
    wstring target(L"Hello");
    wsmatch wideMatch;
    wregex wrx(L"He(l+)o");

    if (regex_match(target.cbegin(), target.cend(), wideMatch, wrx))
        wcout << L"The matching text is:" << wideMatch.str() << endl;

    // (3) with std::string
    string target2("Drizzle");
    regex rx2(R"(D\w+e)"); // no double backslashes with raw string literal

    found = regex_match(target2.cbegin(), target2.cend(), rx2);
    if (found)
        wcout << L"Regex found in Drizzle" << endl;

    // (4) with wchar_t*
    const wchar_t* target3 = L"2014-04-02";
    wcmatch wideMatch2;

    // LR"(...)" is a  raw wide-string literal. Open and close parens
    // are delimiters, not string elements.
    wregex wrx2(LR"(\d{4}(-|/)\d{2}(-|/)\d{2})");
    if (regex_match(target3, wideMatch2, wrx2))
    {
        wcout << L"Matching text: " << wideMatch2.str() << endl;
    }

     return 0;
}
```

```Output
Regex found in abc
The matching text is: Hello
Regex found in Drizzle
The matching text is: 2014-04-02
```

## <a name="regex_replace"></a>  regex_replace

替换匹配正则表达式。

```cpp
template <class OutIt, class BidIt, class RXtraits, class Alloc, class Elem>
OutIt regex_replace(
    OutIt out,
    BidIt first,
    BidIt last,
    const basic_regex<Elem, RXtraits, Alloc>& re,
    const basic_string<Elem>& fmt,
    match_flag_type flags = match_default);

template <class RXtraits, class Alloc, class Elem>
basic_string<Elem> regex_replace(
    const basic_string<Elem>& str,
    const basic_regex<Elem, RXtraits, Alloc>& re,
    const basic_string<Elem>& fmt,
    match_flag_type flags = match_default);
```

### <a name="parameters"></a>参数

*OutIt*<br/>
替换内容的迭代器类型。

*BidIt*<br/>
子匹配项的迭代器类型。

*RXtraits*<br/>
元素的特征类。

*分配*<br/>
正则表达式分配器类。

*Elem*<br/>
要匹配的元素的类型。

*flags*<br/>
匹配标志。

*first*<br/>
要匹配的序列的开头。

*fmt*<br/>
替换内容的格式。

*最后一个*<br/>
要匹配的序列的结尾。

*out*<br/>
输出迭代器。

*re*<br/>
要匹配的正则表达式。

*str*<br/>
要匹配的字符串。

### <a name="remarks"></a>备注

第一个函数将构造[regex_iterator 类](../standard-library/regex-iterator-class.md)对象`iter(first, last, re, flags)`并使用它来拆分其输入的范围`[first, last)`为一系列的子序列`T0 M0 T1 M1...TN-1 MN-1 TN`，其中`Mn`第 n 个匹配项中检测到迭代器。 如果找不到任何匹配项，`T0` 则为整个输入范围且 `N` 为零。 如果 `(flags & format_first_only) != 0`，则仅使用第一个匹配项，`T1` 是匹配项后跟的全部输入文本，且 `N` 为 1。 每个`i`范围内`[0, N)`，则`(flags & format_no_copy) == 0`的文本复制范围内`Ti`到迭代器*出*。然后它调用 `m.format(out, fmt, flags)`，其中 `m` 是迭代器对象 `iter` 为子序列 `Mi` 返回的 `match_results` 对象。 最后，如果`(flags & format_no_copy) == 0`的文本复制范围内`TN`迭代器*出*。该函数将返回*出*。

第二个函数构造 `basic_string<charT>` 类型的本地变量 `result` 并调用 `regex_replace(back_inserter(result), str.begin(), str.end(), re, fmt, flags)`。 它将返回 `result`。

### <a name="example"></a>示例

```cpp
// std__regex__regex_replace.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
{
    char buf[20];
    const char *first = "axayaz";
    const char *last = first + strlen(first);
    std::regex rx("a");
    std::string fmt("A");
    std::regex_constants::match_flag_type fonly =
        std::regex_constants::format_first_only;

    *std::regex_replace(&buf[0], first, last, rx, fmt) = '\0';
    std::cout << "replacement == " << &buf[0] << std::endl;

    *std::regex_replace(&buf[0], first, last, rx, fmt, fonly) = '\0';
    std::cout << "replacement == " << &buf[0] << std::endl;

    std::string str("adaeaf");
    std::cout << "replacement == "
        << std::regex_replace(str, rx, fmt) << std::endl;

    std::cout << "replacement == "
        << std::regex_replace(str, rx, fmt, fonly) << std::endl;

    return (0);
}
```

```Output
replacement == AxAyAz
replacement == Axayaz
replacement == AdAeAf
replacement == Adaeaf
```

## <a name="regex_search"></a>  regex_search

搜索正则表达式匹配项。

```cpp
template <class BidIt, class Alloc, class Elem, class RXtraits, class Alloc2>
bool regex_search(
    BidIt first,
    Bidit last,
    match_results<BidIt, Alloc>& match,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

template <class BidIt, class Elem, class RXtraits, class Alloc2>
bool regex_search(
    BidIt first,
    Bidit last,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

template <class Elem, class Alloc, class RXtraits, class Alloc2>
bool regex_search(
    const Elem* ptr,
    match_results<const Elem*, Alloc>& match,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

template <class Elem, class RXtraits, class Alloc2>
bool regex_search(
    const Elem* ptr,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

template <class IOtraits, class IOalloc, class Alloc, class Elem, class RXtraits, class Alloc2>
bool regex_search(
    const basic_string<Elem, IOtraits, IOalloc>& str,
    match_results<typename basic_string<Elem, IOtraits, IOalloc>::const_iterator, Alloc>& match,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

template <class IOtraits, class IOalloc, class Elem, class RXtraits, class Alloc2>
bool regex_search(
    const basic_string<Elem, IOtraits, IOalloc>& str,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);
```

### <a name="parameters"></a>参数

*BidIt*<br/>
子匹配项的迭代器类型。

*分配*<br/>
匹配结果分配器类。

*Elem*<br/>
要匹配的元素的类型。

*RXtraits*<br/>
元素的特征类。

*Alloc2*<br/>
正则表达式分配器类。

*IOtraits*<br/>
字符串特征类。

*IOalloc*<br/>
字符串分配器类。

*flags*<br/>
匹配标志。

*first*<br/>
要匹配的序列的开头。

*最后一个*<br/>
要匹配的序列的结尾。

*match*<br/>
匹配结果。

*ptr*<br/>
指向要匹配的序列开头的指针。

*re*<br/>
要匹配的正则表达式。

*str*<br/>
要匹配的字符串。

### <a name="remarks"></a>备注

每个模板函数返回 true，仅当其正则表达式搜索*re*在其操作数序列中成功。 采用 `match_results` 对象的函数将其成员设置为反映搜索是否成功，以及如果成功，正则表达式中的各种捕获组所捕获的内容。

### <a name="example"></a>示例

```cpp
// std__regex__regex_search.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
{
    const char *first = "abcd";
    const char *last = first + strlen(first);
    std::cmatch mr;
    std::regex rx("abc");
    std::regex_constants::match_flag_type fl =
        std::regex_constants::match_default;

    std::cout << "search(f, f+1, \"abc\") == " << std::boolalpha
        << regex_search(first, first + 1, rx, fl) << std::endl;

    std::cout << "search(f, l, \"abc\") == " << std::boolalpha
        << regex_search(first, last, mr, rx) << std::endl;
    std::cout << "  matched: \"" << mr.str() << "\"" << std::endl;

    std::cout << "search(\"a\", \"abc\") == " << std::boolalpha
        << regex_search("a", rx) << std::endl;

    std::cout << "search(\"xabcd\", \"abc\") == " << std::boolalpha
        << regex_search("xabcd", mr, rx) << std::endl;
    std::cout << "  matched: \"" << mr.str() << "\"" << std::endl;

    std::cout << "search(string, \"abc\") == " << std::boolalpha
        << regex_search(std::string("a"), rx) << std::endl;

    std::string str("abcabc");
    std::match_results<std::string::const_iterator> mr2;
    std::cout << "search(string, \"abc\") == " << std::boolalpha
        << regex_search(str, mr2, rx) << std::endl;
    std::cout << "  matched: \"" << mr2.str() << "\"" << std::endl;

    return (0);
}
```

```Output
search(f, f+1, "abc") == false
search(f, l, "abc") == true
  matched: "abc"
search("a", "abc") == false
search("xabcd", "abc") == true
  matched: "abc"
search(string, "abc") == false
search(string, "abc") == true
  matched: "abc"
```

## <a name="swap"></a>  swap

交换两个`basic_regex`或`match_results`对象。

```cpp
template <class Elem, class RXtraits>
void swap(
    basic_regex<Elem, RXtraits, Alloc>& left,
    basic_regex<Elem, RXtraits>& right) noexcept;

template <class Elem, class IOtraits, class BidIt, class Alloc>
void swap(
    match_results<BidIt, Alloc>& left,
    match_results<BidIt, Alloc>& right) noexcept;
```

### <a name="parameters"></a>参数

*Elem*<br/>
要匹配的元素的类型。

*RXtraits*<br/>
元素的特征类。

### <a name="remarks"></a>备注

模板函数在常量时间内交换各自参数的内容，并且不会引发异常。

### <a name="example"></a>示例

```cpp
// std__regex__swap.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
{
    std::regex rx0("c(a*)|(b)");
    std::regex rx1;
    std::cmatch mr0;
    std::cmatch mr1;

    swap(rx0, rx1);
    std::regex_search("xcaaay", mr1, rx1);
    swap(mr0, mr1);

    std::csub_match sub = mr0[1];
    std::cout << "matched == " << std::boolalpha
        << sub.matched << std::endl;
    std::cout << "length == " << sub.length() << std::endl;
    std::cout << "string == " << sub << std::endl;

    return (0);
}
```

```Output
matched == true
length == 3
string == aaa
```

## <a name="see-also"></a>请参阅

[\<regex>](../standard-library/regex.md)<br/>
[regex_constants 类](../standard-library/regex-constants-class.md)<br/>
[regex_error 类](../standard-library/regex-error-class.md)<br/>
[regex_iterator 类](../standard-library/regex-iterator-class.md)<br/>
[\<regex> operators](../standard-library/regex-operators.md)<br/>
[regex_token_iterator 类](../standard-library/regex-token-iterator-class.md)<br/>
[regex_traits 类](../standard-library/regex-traits-class.md)<br/>
[\<regex> typedefs](../standard-library/regex-typedefs.md)<br/>

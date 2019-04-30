---
title: basic_regex 类
ms.date: 03/27/2019
f1_keywords:
- regex/std::basic_regex
helpviewer_keywords:
- basic_regex class
ms.assetid: 8a18c6b4-f22a-4cfd-bc16-b4267867ebc3
ms.openlocfilehash: e3a38dc186a52c8431442d58bb10e56837396b07
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62414147"
---
# <a name="basicregex-class"></a>basic_regex 类

包装正则表达式。

## <a name="syntax"></a>语法

```cpp
template <class Elem, class RXtraits>
class basic_regex
```

## <a name="parameters"></a>参数

*Elem*<br/>
要匹配的元素的类型。

*RXtraits*<br/>
元素的特征类。

## <a name="remarks"></a>备注

此模板类描述包含正则表达式的对象。 此模板类的对象可以传递给模板函数[regex_match](../standard-library/regex-functions.md#regex_match)， [regex_search](../standard-library/regex-functions.md#regex_search)，并[regex_replace](../standard-library/regex-functions.md#regex_replace)，结合适合的文本字符串自变量，若要搜索的正则表达式匹配的文本。 有两种类型定义此模板类专用化[正则表达式](../standard-library/regex-typedefs.md#regex)类型的元素**char**，并[wregex](../standard-library/regex-typedefs.md#wregex)类型的元素**wchar_t**。

模板参数*RXtraits*描述模板类支持的正则表达式语法的各种重要属性。 一个指定这些正则表达式特征的外部接口必须与模板类 [regex_traits Class](../standard-library/regex-traits-class.md) 的对象相同的类。

某些函数使用操作数序列来定义正则表达式。 可以通过多种方式指定此操作数序列：

`ptr` -以 null 结尾的序列 (如 C 字符串，对于*Elem*类型的**char**) 开始`ptr`（这必须不能为 null 指针），其中结尾元素为值`value_type()`并不是操作数序列的一部分

`ptr`, `count` - 从 `count`（不能为 null 指针）开始的 `ptr` 元素序列

`str` - `basic_string` 对象 `str` 指定的序列

`first`, `last` - 迭代器 `first` 和 `last` 在范围 `[first, last)` 中分隔的元素序列

`right` - `basic_regex` 对象 `right`

这些成员函数还使用参数`flags`，它指定用于解释除所描述的正则表达式的各种选项*RXtraits*类型。

### <a name="members"></a>成员

|成员|默认值|
|-|-|
|公共静态 const flag_type icase|regex_constants::icase|
|公共静态 const flag_type nosubs|regex_constants::nosubs|
|public static const flag_type optimize|regex_constants::optimize|
|public static const flag_type collate|regex_constants::collate|
|公共静态 const flag_type ECMAScript|regex_constants::ECMAScript|
|public static const flag_type basic|regex_constants::basic|
|public static const flag_type extended|regex_constants::extended|
|public static const flag_type awk|regex_constants::awk|
|public static const flag_type grep|regex_constants::grep|
|public static const flag_type egrep|regex_constants::egrep|
|专用 RXtraits 特征||

### <a name="constructors"></a>构造函数

|构造函数|描述|
|-|-|
|[basic_regex](#basic_regex)|构造正则表达式对象。|

### <a name="typedefs"></a>Typedef

|类型名称|描述|
|-|-|
|[flag_type](#flag_type)|语法选项标志的类型。|
|[locale_type](#locale_type)|存储的区域设置对象的类型。|
|[value_type](#value_type)|元素类型。|

### <a name="member-functions"></a>成员函数

|成员函数|描述|
|-|-|
|[assign](#assign)|将一个值分配到正则表达式对象。|
|[flags](#flags)|返回语法选项标志。|
|[getloc](#getloc)|返回存储的区域设置对象。|
|[imbue](#imbue)|更改存储的区域设置对象。|
|[mark_count](#mark_count)|返回匹配的子表达式的数目。|
|[swap](#swap)|交换两个正则表达式对象。|

### <a name="operators"></a>运算符

|运算符|描述|
|-|-|
|[operator=](#op_eq)|将一个值分配到正则表达式对象。|

## <a name="requirements"></a>要求

**标头：**\<regex 1>

**命名空间：** std

## <a name="example"></a>示例

```cpp
// std__regex__basic_regex.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

using namespace std;

int main()
{
    regex::value_type elem = 'x';
    regex::flag_type flag = regex::grep;

    elem = elem;  // to quiet "unused" warnings
    flag = flag;

    // constructors
    regex rx0;
    cout << "match(\"abc\", \"\") == " << boolalpha
        << regex_match("abc", rx0) << endl;

    regex rx1("abcd", regex::ECMAScript);
    cout << "match(\"abc\", \"abcd\") == " << boolalpha
        << regex_match("abc", rx1) << endl;

    regex rx2("abcd", 3);
    cout << "match(\"abc\", \"abc\") == " << boolalpha
        << regex_match("abc", rx2) << endl;

    regex rx3(rx2);
    cout << "match(\"abc\", \"abc\") == " << boolalpha
        << regex_match("abc", rx3) << endl;

    string str("abcd");
    regex rx4(str);
    cout << "match(string(\"abcd\"), \"abc\") == " << boolalpha
        << regex_match("abc", rx4) << endl;

    regex rx5(str.begin(), str.end() - 1);
    cout << "match(string(\"abc\"), \"abc\") == " << boolalpha
        << regex_match("abc", rx5) << endl;
    cout << endl;

    // assignments
    rx0 = "abc";
    rx0 = rx1;
    rx0 = str;

    rx0.assign("abcd", regex::ECMAScript);
    rx0.assign("abcd", 3);
    rx0.assign(rx1);
    rx0.assign(str);
    rx0.assign(str.begin(), str.end() - 1);

    rx0.swap(rx1);

    // mark_count
    cout << "\"abc\" mark_count == "
        << regex("abc").mark_count() << endl;
    cout << "\"(abc)\" mark_count == "
        << regex("(abc)").mark_count() << endl;

    // locales
    regex::locale_type loc = rx0.imbue(locale());
    cout << "getloc == imbued == " << boolalpha
        << (loc == rx0.getloc()) << endl;

    // initializer_list
    regex rx6({ 'a', 'b', 'c' }, regex::ECMAScript);
    cout << "match(\"abc\") == " << boolalpha
        << regex_match("abc", rx6);
    cout << endl;
}
```

```Output
match("abc", "") == false
match("abc", "abcd") == false
match("abc", "abc") == true
match("abc", "abc") == true
match(string("abcd"), "abc") == false
match(string("abc"), "abc") == true

"abc" mark_count == 0
"(abc)" mark_count == 1
getloc == imbued == true
match("abc") == true
```

## <a name="assign"></a>  basic_regex::assign

将一个值分配到正则表达式对象。

```cpp
basic_regex& assign(
    const basic_regex& right);

basic_regex& assign(
    const Elem* ptr,
    flag_type flags = ECMAScript);

basic_regex& assign(
    const Elem* ptr,
    size_type len,
    flag_type flags = ECMAScript);

basic_regex& assign(
    initializer_list<_Elem> IList,
    flag_type flags = regex_constants::ECMAScript);

template <class STtraits, class STalloc>
basic_regex& assign(
    const basic_string<Elem, STtraits, STalloc>& str,
    flag_type flags = ECMAScript);

template <class InIt>
basic_regex& assign(
    InIt first, InIt last,
    flag_type flags = ECMAScript);
```

### <a name="parameters"></a>参数

*STtraits*<br/>
字符串源的特征类。

*STalloc*<br/>
字符串源的分配器类。

*InIt*<br/>
范围源的输入迭代器类型。

*right*<br/>
要复制的正则表达式源。

*ptr*<br/>
指向要复制的序列开头的指针。

*flags*<br/>
复制时要添加的语法选项标志。

*len/TD>*<br/>
要复制的序列的长度。

*str*<br/>
要复制的字符串。

*first*<br/>
要复制的序列的开头。

*last*<br/>
要复制的序列的结尾。

*IList*<br/>
要复制的 initializer_list。

### <a name="remarks"></a>备注

每个成员函数将 `*this` 保留的正则表达式替换为操作数序列所描述的正则表达式，然后返回 `*this`。

## <a name="basic_regex"></a>  basic_regex::basic_regex

构造正则表达式对象。

```cpp
basic_regex();

explicit basic_regex(
    const Elem* ptr,
    flag_type flags);

explicit basic_regex(
    const Elem* ptr,
    size_type len,
    flag_type flags);

basic_regex(
    const basic_regex& right);

basic_regex(
    initializer_list<Type> IList,
    flag_type flags);

template <class STtraits, class STalloc>
explicit basic_regex(
    const basic_string<Elem, STtraits, STalloc>& str,
    flag_type flags);

template <class InIt>
explicit basic_regex(
    InIt first,
    InIt last,
    flag_type flags);
```

### <a name="parameters"></a>参数

*STtraits*<br/>
字符串源的特征类。

*STalloc*<br/>
字符串源的分配器类。

*InIt*<br/>
范围源的输入迭代器类型。

*right*<br/>
要复制的正则表达式源。

*ptr*<br/>
指向要复制的序列开头的指针。

*flags*<br/>
复制时要添加的语法选项标志。

*len/TD>*<br/>
要复制的序列的长度。

*str*<br/>
要复制的字符串。

*first*<br/>
要复制的序列的开头。

*last*<br/>
要复制的序列的结尾。

*IList*<br/>
要复制的 initializer_list。

### <a name="remarks"></a>备注

所有构造函数将存储类型 `RXtraits` 的默认构造对象。

第一个构造函数构造一个空 `basic_regex` 对象。 其他构造函数构造 `basic_regex` 对象，其中包含由操作数序列描述的正则表达式。

一个空`basic_regex`对象不匹配任何字符序列时传递给[regex_match](../standard-library/regex-functions.md#regex_match)， [regex_search](../standard-library/regex-functions.md#regex_search)，或[regex_replace](../standard-library/regex-functions.md#regex_replace)。

## <a name="flag_type"></a>  basic_regex::flag_type

语法选项标志的类型。

```cpp
typedef regex_constants::syntax_option_type flag_type;
```

### <a name="remarks"></a>备注

该类型是 [regex_constants::syntax_option_type](../standard-library/regex-constants-class.md#syntax_option_type) 的同义词。

## <a name="flags"></a>  basic_regex::flags

返回语法选项标志。

```cpp
flag_type flags() const;
```

### <a name="remarks"></a>备注

成员函数返回 `flag_type` 自变量的值，该值传递到对一个 [basic_regex::assign](#assign) 成员函数的最近调用，或者如果没有实施这类调用，则返回传递到构造函数的值。

## <a name="getloc"></a>  basic_regex::getloc

返回存储的区域设置对象。

```cpp
locale_type getloc() const;
```

### <a name="remarks"></a>备注

成员函数将返回 `traits.`[regex_traits::getloc](../standard-library/regex-traits-class.md#getloc)`()`。

## <a name="imbue"></a>  basic_regex::imbue

更改存储的区域设置对象。

```cpp
locale_type imbue(locale_type loc);
```

### <a name="parameters"></a>参数

*loc*<br/>
要存储的区域设置对象。

### <a name="remarks"></a>备注

该成员函数将清空 `*this` 并返回 `traits.`[regex_traits::imbue](../standard-library/regex-traits-class.md#imbue)`(loc)`。

## <a name="locale_type"></a>  basic_regex::locale_type

存储的区域设置对象的类型。

```cpp
typedef typename RXtraits::locale_type locale_type;
```

### <a name="remarks"></a>备注

该类型是 [regex_traits::locale_type](../standard-library/regex-traits-class.md#locale_type) 的同义词。

## <a name="mark_count"></a>  basic_regex::mark_count

返回匹配的子表达式的数目。

```cpp
unsigned mark_count() const;
```

### <a name="remarks"></a>备注

成员函数将返回正则表达式中的捕获组数量。

## <a name="op_eq"></a>  basic_regex::operator=

将一个值分配到正则表达式对象。

```cpp
basic_regex& operator=(const basic_regex& right);

basic_regex& operator=(const Elem *str);

template <class STtraits, class STalloc>
basic_regex& operator=(const basic_string<Elem, STtraits, STalloc>& str);
```

### <a name="parameters"></a>参数

*STtraits*<br/>
字符串源的特征类。

*STalloc*<br/>
字符串源的分配器类。

*right*<br/>
要复制的正则表达式源。

*str*<br/>
要复制的字符串。

### <a name="remarks"></a>备注

每个运算符将 `*this` 保留的正则表达式替换为操作数序列所描述的正则表达式，然后返回 `*this`。

## <a name="swap"></a>  basic_regex::swap

交换两个正则表达式对象。

```cpp
void swap(basic_regex& right) throw();
```

### <a name="parameters"></a>参数

*right*<br/>
要交换的正则表达式对象。

### <a name="remarks"></a>备注

成员函数交换之间的正则表达式`*this`并*右*。 它定时执行此操作且不引发异常。

## <a name="value_type"></a>  basic_regex::value_type

元素类型。

```cpp
typedef Elem value_type;
```

### <a name="remarks"></a>备注

该类型是模板参数的同义词*Elem*。

## <a name="see-also"></a>请参阅

[\<regex>](../standard-library/regex.md)<br/>
[regex_match](../standard-library/regex-functions.md#regex_match)<br/>
[regex_search](../standard-library/regex-functions.md#regex_search)<br/>
[regex_replace](../standard-library/regex-functions.md#regex_replace)<br/>
[regex](../standard-library/regex-typedefs.md#regex)<br/>
[wregex](../standard-library/regex-typedefs.md#wregex)<br/>
[regex_traits 类](../standard-library/regex-traits-class.md)<br/>

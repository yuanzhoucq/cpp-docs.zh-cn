---
title: regex_traits 类
ms.date: 09/10/2018
f1_keywords:
- regex/std::regex_traits
- regex/std::regex_traits::char_type
- regex/std::regex_traits::size_type
- regex/std::regex_traits::string_type
- regex/std::regex_traits::locale_type
- regex/std::regex_traits::char_class_type
- regex/std::regex_traits::length
- regex/std::regex_traits::translate
- regex/std::regex_traits::translate_nocase
- regex/std::regex_traits::transform
- regex/std::regex_traits::transform_primary
- regex/std::regex_traits::lookup_classname
- regex/std::regex_traits::lookup_collatename
- regex/std::regex_traits::isctype
- regex/std::regex_traits::value
- regex/std::regex_traits::imbue
- regex/std::regex_traits::getloc
helpviewer_keywords:
- std::regex_traits [C++]
- std::regex_traits [C++], char_type
- std::regex_traits [C++], size_type
- std::regex_traits [C++], string_type
- std::regex_traits [C++], locale_type
- std::regex_traits [C++], char_class_type
- std::regex_traits [C++], length
- std::regex_traits [C++], translate
- std::regex_traits [C++], translate_nocase
- std::regex_traits [C++], transform
- std::regex_traits [C++], transform_primary
- std::regex_traits [C++], lookup_classname
- std::regex_traits [C++], lookup_collatename
- std::regex_traits [C++], isctype
- std::regex_traits [C++], value
- std::regex_traits [C++], imbue
- std::regex_traits [C++], getloc
ms.assetid: bc5a5eed-32fc-4eb7-913d-71c42e729e81
ms.openlocfilehash: 80739d3d8f4bfd38dc3d252a5f3d6308653a7bb9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50484053"
---
# <a name="regextraits-class"></a>regex_traits 类

描述用于匹配的元素的特征。

## <a name="syntax"></a>语法

```cpp
template<class Elem>
class regex_traits
```

## <a name="parameters"></a>参数

*Elem*<br/>
要描述的字符元素类型。

## <a name="remarks"></a>备注

此模板类描述各种类型的正则表达式特征*Elem*。 此模板类[basic_regex 类](../standard-library/basic-regex-class.md)使用此信息来操作类型的元素*Elem*。

每个 `regex_traits` 对象包含 `regex_traits::locale` 类型的对象，该对象由它的一些成员函数使用。 默认区域设置是一份 `regex_traits::locale()`副本。 成员函数 `imbue` 替换区域设置对象，而成员函数 `getloc` 返回区域设置对象的副本。

### <a name="constructors"></a>构造函数

|构造函数|描述|
|-|-|
|[regex_traits](#regex_traits)|构造对象。|

### <a name="typedefs"></a>Typedef

|类型名称|描述|
|-|-|
|[char_class_type](#char_class_type)|字符类指示符的类型。|
|[char_type](#char_type)|元素的类型。|
|[locale_type](#locale_type)|存储的区域设置对象的类型。|
|[size_type](#size_type)|序列长度的类型。|
|[string_type](#string_type)|元素字符串的类型。|

### <a name="member-functions"></a>成员函数

|成员函数|描述|
|-|-|
|[getloc](#getloc)|返回存储的区域设置对象。|
|[imbue](#imbue)|更改存储的区域设置对象。|
|[isctype](#isctype)|类成员资格测试。|
|[length](#length)|返回以 null 结尾的序列的长度。|
|[lookup_classname](#lookup_classname)|将序列映射到字符类。|
|[lookup_collatename](#lookup_collatename)|将序列映射到排序规则元素。|
|[transform](#transform)|转换为等效顺序序列。|
|[transform_primary](#transform_primary)|转换为不区分大小写的顺序等效序列。|
|[翻译](#translate)|转换为等效的匹配元素。|
|[translate_nocase](#translate_nocase)|转换为不区分大小写的等效匹配序列。|
|[value](#value)|将元素转换为数字值。|

## <a name="requirements"></a>要求

**标头：**\<regex 1>

**命名空间：** std

## <a name="example"></a>示例

```cpp
// std__regex__regex_traits.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

typedef std::regex_traits<char> Mytr;
int main()
    {
    Mytr tr;

    Mytr::char_type ch = tr.translate('a');
    std::cout << "translate('a') == 'a' == " << std::boolalpha
        << (ch == 'a') << std::endl;

    std::cout << "nocase 'a' == 'A' == " << std::boolalpha
        << (tr.translate_nocase('a') == tr.translate_nocase('A'))
        << std::endl;

    const char *lbegin = "abc";
    const char *lend = lbegin + strlen(lbegin);
    Mytr::size_type size = tr.length(lbegin);
    std::cout << "length(\"abc\") == " << size <<std::endl;

    Mytr::string_type str = tr.transform(lbegin, lend);
    std::cout << "transform(\"abc\") < \"abc\" == " << std::boolalpha
        << (str < "abc") << std::endl;

    const char *ubegin = "ABC";
    const char *uend = ubegin + strlen(ubegin);
    std::cout << "primary \"ABC\" < \"abc\" == " << std::boolalpha
        << (tr.transform_primary(ubegin, uend) <
            tr.transform_primary(lbegin, lend))
        << std::endl;

    const char *dig = "digit";
    Mytr::char_class_type cl = tr.lookup_classname(dig, dig + 5);
    std::cout << "class digit == d == " << std::boolalpha
        << (cl == tr.lookup_classname(dig, dig + 1))
        << std::endl;

    std::cout << "'3' is digit == " <<std::boolalpha
        << tr.isctype('3', tr.lookup_classname(dig, dig + 5))
        << std::endl;

    std::cout << "hex C == " << tr.value('C', 16) << std::endl;

// other members
    str = tr.lookup_collatename(dig, dig + 5);

    Mytr::locale_type loc = tr.getloc();
    tr.imbue(loc);

    return (0);
    }
```

```Output
translate('a') == 'a' == true
nocase 'a' == 'A' == true
length("abc") == 3
transform("abc") < "abc" == false
primary "ABC" < "abc" == false
class digit == d == true
'3' is digit == true
hex C == 12
```

## <a name="char_class_type"></a>regex_traits::char_class_type

字符类指示符的类型。

```cpp
typedef T8 char_class_type;
```

### <a name="remarks"></a>备注

类型用于指定字符类的未指定类型的同义词。 可以使用 `|` 运算符指定属于由操作数指定的类并集的字符类，从而组合此类型的值。

## <a name="char_type"></a>  regex_traits::char_type

元素的类型。

```cpp
typedef Elem char_type;
```

### <a name="remarks"></a>备注

Typedef 是模板参数 `Elem`的同义词。

## <a name="getloc"></a>  regex_traits::getloc

返回存储的区域设置对象。

```cpp
locale_type getloc() const;
```

### <a name="remarks"></a>备注

此成员函数返回存储的 `locale` 对象。

## <a name="imbue"></a>  regex_traits::imbue

更改存储的区域设置对象。

```cpp
locale_type imbue(locale_type loc);
```

### <a name="parameters"></a>参数

*Loc*<br/>
要存储的区域设置对象。

### <a name="remarks"></a>备注

成员函数副本*loc*到存储`locale`对象，并返回以前存储的值的副本`locale`对象。

## <a name="isctype"></a>  regex_traits::isctype

类成员资格测试。

```cpp
bool isctype(char_type ch, char_class_type cls) const;
```

### <a name="parameters"></a>参数

*ch*<br/>
要测试的元素。

*符合 cls*<br/>
要测试的类。

### <a name="remarks"></a>备注

仅当成员函数将返回 true 字符*ch*中指定的字符类*cls*。

## <a name="length"></a>  regex_traits::length

返回以 null 结尾的序列的长度。

```cpp
static size_type length(const char_type *str);
```

### <a name="parameters"></a>参数

*str*<br/>

Null 终止的序列。

### <a name="remarks"></a>备注

此静态成员函数返回 `std::char_traits<char_type>::length(str)`。

## <a name="locale_type"></a>  regex_traits::locale_type

存储的区域设置对象的类型。

```cpp
typedef T7 locale_type;
```

### <a name="remarks"></a>备注

Typedef 是封装区域设置的类型的同义词。 在专业 `regex_traits<char>` 和 `regex_traits<wchar_t>` 中，它是 `std::locale` 的同义词。

## <a name="lookup_classname"></a>  regex_traits::lookup_classname

将序列映射到字符类。

```cpp
template <class FwdIt>
char_class_type lookup_classname(FwdIt first, FwdIt last) const;
```

### <a name="parameters"></a>参数

*first*<br/>
要查找的序列的开头。

*最后一个*<br/>
要查找的序列的结尾。

### <a name="remarks"></a>备注

该成员函数返回一个值，该值指定由其自变量指向的字符序列命名的字符类。 该值不依赖序列中字符的大小写。

专用化 `regex_traits<char>` 识别名称 `"d"`、`"s"`、`"w"`、`"alnum"`、`"alpha"`、`"blank"`、`"cntrl"`、`"digit"`、`"graph"`、`"lower"`、`"print"`、`"punct"`、`"space"`、`"upper"` 和 `"xdigit"`，均不区分大小写。

专用化 `regex_traits<wchar_t>` 识别名称 `L"d"`、`L"s"`、`L"w"`、`L"alnum"`、`L"alpha"`、`L"blank"`、`L"cntrl"`、`L"digit"`、`L"graph"`、`L"lower"`、`L"print"`、`L"punct"`、`L"space"`、`L"upper"` 和 `L"xdigit"`，均不区分大小写。

## <a name="lookup_collatename"></a>  regex_traits::lookup_collatename

将序列映射到排序规则元素。

```cpp
template <class FwdIt>
string_type lookup_collatename(FwdIt first, FwdIt last) const;
```

### <a name="parameters"></a>参数

*first*<br/>
要查找的序列的开头。

*最后一个*<br/>
要查找的序列的结尾。

### <a name="remarks"></a>备注

此成员函数将返回一个字符串对象，它包含对应于序列 `[first, last)`的排序规则元素；如果该序列不是有效的排序规则元素，则返回空字符串。

## <a name="regex_traits"></a>regex_traits::regex_traits

构造对象。

```cpp
regex_traits();
```

### <a name="remarks"></a>备注

构造函数构造其存储的 `locale` 对象初始化为默认区域设置的对象。

## <a name="size_type"></a>regex_traits::size_type

序列长度的类型。

```cpp
typedef T6 size_type;
```

### <a name="remarks"></a>备注

typedef 是无符号整数类型的同义词。 在专业 `regex_traits<char>` 和 `regex_traits<wchar_t>` 中，它是 `std::size_t` 的同义词。

typedef 是 `std::size_t`的同义词。

## <a name="string_type"></a>regex_traits::string_type

元素字符串的类型。

```cpp
typedef basic_string<Elem> string_type;
```

### <a name="remarks"></a>备注

typedef 是 `basic_string<Elem>`的同义词。

## <a name="transform"></a>regex_traits::transform

转换为等效顺序序列。

```cpp
template <class FwdIt>
string_type transform(FwdIt first, FwdIt last) const;
```

### <a name="parameters"></a>参数

*first*<br/>
要转换的序列的开头。

*最后一个*<br/>
要转换的序列的结尾。

### <a name="remarks"></a>备注

此成员函数返回它使用转换规则生成的字符串，转换规则依赖于 `locale` 对象。 对于由迭代器范围 `[first1, last1)` 和 `[first2, last2)`指定的两个字符序列，如果由迭代器范围 `transform(first1, last1) < transform(first2, last2)` 指定的字符序列排序在由迭代器范围 `[first1, last1)` 指定的字符序列之前，则 `[first2, last2)`。

## <a name="transform_primary"></a>regex_traits::transform_primary

转换为不区分大小写的顺序等效序列。

```cpp
template <class FwdIt>
string_type transform_primary(FwdIt first, FwdIt last) const;
```

### <a name="parameters"></a>参数

*first*<br/>
要转换的序列的开头。

*最后一个*<br/>
要转换的序列的结尾。

### <a name="remarks"></a>备注

此成员函数返回它使用转换规则生成的字符串，转换规则依赖于 `locale` 对象。 对于由迭代器范围 `[first1, last1)` 和 `[first2, last2)`指定的两个字符序列，如果由迭代器范围 `transform_primary(first1, last1) < transform_primary(first2, last2)` 指定的字符序列排序在由迭代器范围 `[first1, last1)` 指定的字符序列之前（不考虑大小写或重音字符），则 `[first2, last2)` 。

## <a name="translate"></a>regex_traits::translate

转换为等效的匹配元素。

```cpp
char_type translate(char_type ch) const;
```

### <a name="parameters"></a>参数

*ch*<br/>
要转换的元素。

### <a name="remarks"></a>备注

此成员函数返回一个字符，它通过使用取决于存储的 `locale` 对象的转换规则而生成。 对于两个 `char_type` 对象（ `ch1` 和 `ch2`），只有 `translate(ch1) == translate(ch2)` 和 `ch1` 匹配（在其中一个在正则表达式定义中出现且另一个在区分区域设置匹配的目标序列中的相应位置出现时），才为 `ch2` 。

## <a name="translate_nocase"></a>  regex_traits::translate_nocase

转换为不区分大小写的等效匹配序列。

```cpp
char_type translate_nocase(char_type ch) const;
```

### <a name="parameters"></a>参数

*ch*<br/>
要转换的元素。

### <a name="remarks"></a>备注

此成员函数返回一个字符，它通过使用取决于存储的 `locale` 对象的转换规则而生成。 对于两个 `char_type` 对象（ `ch1` 和 `ch2`），只有当 `translate_nocase(ch1) == translate_nocase(ch2)` 和 `ch1` 的匹配条件为其中一个在正则表达式中出现且另一个在不区分大小写匹配的目标序列中的相应位置出现时，才为 `ch2` 。

## <a name="value"></a>  regex_traits::value

将元素转换为数字值。

```cpp
int value(Elem ch, int radix) const;
```

### <a name="parameters"></a>参数

*ch*<br/>
要转换的元素。

*radix*<br/>
要使用的算术基数。

### <a name="remarks"></a>备注

此成员函数返回的值的字符表示形式*ch*中的*基数*，则为-1 *ch*不是有效的数字中的*基数*. 仅将与调用函数*基数*参数 8、 10 或 16。

## <a name="see-also"></a>请参阅

[\<regex>](../standard-library/regex.md)<br/>
[regex_constants 类](../standard-library/regex-constants-class.md)<br/>
[regex_error 类](../standard-library/regex-error-class.md)<br/>
[\<regex> functions](../standard-library/regex-functions.md)<br/>
[regex_iterator 类](../standard-library/regex-iterator-class.md)<br/>
[\<regex> operators](../standard-library/regex-operators.md)<br/>
[regex_token_iterator 类](../standard-library/regex-token-iterator-class.md)<br/>
[\<regex> typedefs](../standard-library/regex-typedefs.md)<br/>
[regex_traits\<char > 类](../standard-library/regex-traits-char-class.md)<br/>
[regex_traits\<wchar_t> Class](../standard-library/regex-traits-wchar-t-class.md)<br/>

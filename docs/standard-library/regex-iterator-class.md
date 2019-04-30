---
title: regex_iterator 类
ms.date: 09/10/2018
f1_keywords:
- regex/std::regex_iterator
- regex/std::regex_iterator::operator==
- regex/std::regex_iterator::operator!=
- regex/std::regex_iterator::operator*
- regex/std::regex_iterator::operator->
- regex/std::regex_iterator::operator++
helpviewer_keywords:
- std::regex_iterator
- std::regex_iterator::operator==
- std::regex_iterator::operator!=
- std::regex_iterator::operator*
- std::regex_iterator::operator->
- std::regex_iterator::operator++
ms.assetid: 0cfd8fd0-5a95-4f3c-bf8e-6ef028c423d3
ms.openlocfilehash: 937c217cdef6895aaa3adb1499f1fde8f67fd513
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62369484"
---
# <a name="regexiterator-class"></a>regex_iterator 类

匹配项的迭代器类。

## <a name="syntax"></a>语法

```cpp
template<class BidIt,
   class Elem = typename std::iterator_traits<BidIt>::value_type,
   class RxTraits = regex_traits<Elem> >
class regex_iterator
```

## <a name="parameters"></a>参数

*BidIt*<br/>
子匹配项的迭代器类型。

*Elem*<br/>
要匹配的元素的类型。

*RXtraits*<br/>
元素的特征类。

## <a name="remarks"></a>备注

此模板类描述常量前向迭代器对象。 它将其正则表达式对象 `match_results<BidIt>` 重复应用到迭代器范围 `*pregex` 定义的字符序列，以提取 `[begin, end)`类型的对象。

### <a name="constructors"></a>构造函数

|构造函数|描述|
|-|-|
|[regex_iterator](#regex_iterator)|构造迭代器。|

### <a name="typedefs"></a>Typedef

|类型名称|描述|
|-|-|
|[difference_type](#difference_type)|迭代器差异的类型。|
|[iterator_category](#iterator_category)|迭代器类别的类型。|
|[pointer](#pointer)|指向一个匹配的指针的类型。|
|[reference](#reference)|对匹配项的引用的类型。|
|[regex_type](#regex_type)|要匹配的正则表达式类型。|
|[value_type](#value_type)|匹配的类型。|

### <a name="operators"></a>运算符

|运算符|描述|
|-|-|
|[operator!=](#op_neq)|比较不相等的迭代器。|
|[operator*](#op_star)|访问指定的匹配项。|
|[operator++](#op_add_add)|递增迭代器。|
|[operator=](#op_eq)|比较迭代器是否相等。|
|[operator->](#op_arrow)|访问指定的匹配项。|

## <a name="requirements"></a>要求

**标头：**\<regex 1>

**命名空间：** std

## <a name="examples"></a>示例

有关正则表达式的示例，请参阅下面的主题：

- [regex_match](../standard-library/regex-functions.md#regex_match)

- [regex_replace](../standard-library/regex-functions.md#regex_replace)

- [regex_search](../standard-library/regex-functions.md#regex_search)

- [swap](../standard-library/regex-functions.md#swap)

```cpp
// std__regex__regex_iterator.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

typedef std::regex_iterator<const char *> Myiter;
int main()
    {
    const char *pat = "axayaz";
    Myiter::regex_type rx("a");
    Myiter next(pat, pat + strlen(pat), rx);
    Myiter end;

    for (; next != end; ++next)
        std::cout << "match == " << next->str() << std::endl;

// other members
    Myiter it1(pat, pat + strlen(pat), rx);
    Myiter it2(it1);
    next = it1;

    Myiter::iterator_category cat = std::forward_iterator_tag();
    Myiter::difference_type dif = -3;
    Myiter::value_type mr = *it1;
    Myiter::reference ref = mr;
    Myiter::pointer ptr = &ref;

    dif = dif; // to quiet "unused" warnings
    ptr = ptr;

    return (0);
    }
```

```Output
match == a
match == a
match == a
```

## <a name="difference_type"></a>  regex_iterator::difference_type

迭代器差异的类型。

```cpp
typedef std::ptrdiff_t difference_type;
```

### <a name="remarks"></a>备注

该类型是 `std::ptrdiff_t` 的同义词。

## <a name="iterator_category"></a>  regex_iterator::iterator_category

迭代器类别的类型。

```cpp
typedef std::forward_iterator_tag iterator_category;
```

### <a name="remarks"></a>备注

该类型是 `std::forward_iterator_tag` 的同义词。

## <a name="op_neq"></a>  regex_iterator::operator!=

比较不相等的迭代器。

```cpp
bool operator!=(const regex_iterator& right);
```

### <a name="parameters"></a>参数

*right*<br/>
要进行比较的迭代器。

### <a name="remarks"></a>备注

成员函数返回 `!(*this == right)`。

## <a name="op_star"></a>regex_iterator::operator*

访问指定的匹配项。

```cpp
const match_results<BidIt>& operator*();
```

### <a name="remarks"></a>备注

该成员函数将返回存储值 `match`。

## <a name="op_add_add"></a>regex_iterator::operator++

递增迭代器。

```cpp
regex_iterator& operator++();
regex_iterator& operator++(int);
```

### <a name="remarks"></a>备注

如果当前匹配项不具有字符，则第一个运算符将调用 `regex_search(begin, end, match, *pregex, flags | regex_constants::match_prev_avail | regex_constants::match_not_null)`；否则它会将存储的值 `begin` 推进到指向当前匹配项后的第一个字符，然后调用 `regex_search(begin, end, match, *pregex, flags | regex_constants::match_prev_avail)`。 在任一情况下，如果搜索失败，则该运算符会将对象设置为序列末迭代器。 运算符返回该对象。

第二个运算符生成对象的副本，递增对象，然后返回副本。

## <a name="op_eq"></a>regex_iterator::operator=

比较迭代器是否相等。

```cpp
bool operator==(const regex_iterator& right);
```

### <a name="parameters"></a>参数

*right*<br/>
要进行比较的迭代器。

### <a name="remarks"></a>备注

如果成员函数将返回 true`*this`并*右*为序列末迭代器或如果两者都不是一个序列末迭代器，并`begin == right.begin`， `end == right.end`， `pregex == right.pregex`，和`flags == right.flags`。 否则，返回 false。

## <a name="op_arrow"></a>  regex_iterator::operator-&gt;

访问指定的匹配项。

```cpp
const match_results<BidIt> * operator->();
```

### <a name="remarks"></a>备注

此成员函数返回存储值 `match`的地址。

## <a name="pointer"></a>  regex_iterator::pointer

指向一个匹配的指针的类型。

```cpp
typedef match_results<BidIt> *pointer;
```

### <a name="remarks"></a>备注

类型是 `match_results<BidIt>*` 的同义词，其中 `BidIt` 是模板参数。

## <a name="reference"></a>  regex_iterator::reference

对匹配项的引用的类型。

```cpp
typedef match_results<BidIt>& reference;
```

### <a name="remarks"></a>备注

类型是 `match_results<BidIt>&` 的同义词，其中 `BidIt` 是模板参数。

## <a name="regex_iterator"></a>  regex_iterator::regex_iterator

构造迭代器。

```cpp
regex_iterator();

regex_iterator(BidIt first,
    BidIt last,
    const regex_type& re,
    regex_constants::match_flag_type f = regex_constants::match_default);
```

### <a name="parameters"></a>参数

*first*<br/>
要匹配的序列的开头。

*last*<br/>
要匹配的序列的结尾。

*re*<br/>
匹配项正则表达式。

*f*<br/>
匹配标志。

### <a name="remarks"></a>备注

第一个构造函数将构造序列末迭代器。 第二个构造函数初始化存储的值`begin`与*第一个*，则存储值`end`与*最后一个*，则存储值`pregex`与`&re`，和存储值`flags`与*f*。 然后，它调用 `regex_search(begin, end, match, *pregex, flags)`。 如果搜索失败，则构造函数会将对象设置为序列末迭代器。

## <a name="regex_type"></a>  regex_iterator::regex_type

要匹配的正则表达式类型。

```cpp
typedef basic_regex<Elem, RXtraits> regex_type;
```

### <a name="remarks"></a>备注

typedef 是 `basic_regex<Elem, RXtraits>`的同义词。

## <a name="value_type"></a>  regex_iterator::value_type

匹配的类型。

```cpp
typedef match_results<BidIt> value_type;
```

### <a name="remarks"></a>备注

类型是 `match_results<BidIt>` 的同义词，其中 `BidIt` 是模板参数。

## <a name="see-also"></a>请参阅

[\<regex>](../standard-library/regex.md)<br/>
[regex_constants 类](../standard-library/regex-constants-class.md)<br/>
[regex_error 类](../standard-library/regex-error-class.md)<br/>
[\<regex> functions](../standard-library/regex-functions.md)<br/>
[regex_iterator 类](../standard-library/regex-iterator-class.md)<br/>
[\<regex> operators](../standard-library/regex-operators.md)<br/>
[regex_token_iterator 类](../standard-library/regex-token-iterator-class.md)<br/>
[regex_traits 类](../standard-library/regex-traits-class.md)<br/>
[\<regex> typedefs](../standard-library/regex-typedefs.md)<br/>

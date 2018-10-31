---
title: sub_match 类 | Microsoft Docs
ms.custom: ''
ms.date: 09/10/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- regex/std::sub_match
- regex/std::sub_match::matched
- regex/std::sub_match::compare
- regex/std::sub_match::length
- regex/std::sub_match::str
- regex/std::sub_match::difference_type
- regex/std::sub_match::iterator
- regex/std::sub_match::value_type
dev_langs:
- C++
helpviewer_keywords:
- std::sub_match [C++]
- std::sub_match [C++], matched
- std::sub_match [C++], compare
- std::sub_match [C++], length
- std::sub_match [C++], str
- std::sub_match [C++], difference_type
- std::sub_match [C++], iterator
- std::sub_match [C++], value_type
ms.assetid: 804e2b9e-d16a-4c4c-ac60-024e0b2dd0e8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 65d873c4e7188b3000cee65e03c4ce6edcad8046
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/03/2018
ms.locfileid: "48235329"
---
# <a name="submatch-class"></a>sub_match 类

介绍子匹配项。

## <a name="syntax"></a>语法

```cpp
template <class BidIt>
class sub_match
    : public std::pair<BidIt, BidIt>
```

## <a name="parameters"></a>参数

*BidIt*<br/>
子匹配项的迭代器类型。

## <a name="remarks"></a>备注

此模板类描述指定字符序列的对象，该字符序列与调用 [regex_match](../standard-library/regex-functions.md#regex_match) 或 [regex_search](../standard-library/regex-functions.md#regex_search)的捕获组匹配。 [match_results Class](../standard-library/match-results-class.md) 类型的对象保存这些对象的数组，每个数组用于搜索中所用正则表达式中的每个捕获组。

如果捕获组不匹配，则对象的数据成员 `matched` 保持为 false，两个迭代器 `first` 和 `second` （继承自基类 `std::pair`）相等。 如果捕获组匹配，则 `matched` 保持为 true，迭代器 `first` 指向与捕获组匹配的目标序列中第一个字符，迭代器 `second` 与捕获组匹配的目标序列中最后一个字符后紧邻的位置。 请注意，对于长度为零的匹配项，成员 `matched` 保持为 true，两个迭代器将相等并将同时将指向匹配项的位置。

当捕获组仅由一个断言或一个允许重复次数为零的重复组成时，可能出现长度为零的匹配项。 例如：

“^”匹配目标序列“a”； `sub_match` 对象对应捕获组 0 持有两个迭代器，它们均指向序列中第一个字符。

“b(a*)b”匹配目标序列“bb”； `sub_match` 对象对应捕获组 0 持有两个迭代器，它们均指向序列中第二个字符。

### <a name="typedefs"></a>Typedef

|类型名称|描述|
|-|-|
|[difference_type](#difference_type)|迭代器差异的类型。|
|[Iterator](#iterator)|迭代器的类型。|
|[value_type](#value_type)|元素的类型。|

### <a name="member-functions"></a>成员函数

|成员函数|描述|
|-|-|
|[compare](#compare)|将子匹配项与序列进行比较。|
|[length](#length)|返回子匹配项的长度。|
|[匹配](#matched)|指示是否匹配成功。|
|[str](#str)|将子匹配转换为字符串。|

### <a name="operators"></a>运算符

|运算符|描述|
|-|-|
|[operator basic_string < value_type >](#op_basic_string_lt_value_type_gt)|将子匹配转换为字符串。|

## <a name="example"></a>示例

```cpp
// std__regex__sub_match.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
    {
    std::regex rx("c(a*)|(b)");
    std::cmatch mr;

    std::regex_search("xcaaay", mr, rx);

    std::csub_match sub = mr[1];
    std::cout << "matched == " << std::boolalpha
        << sub.matched << std::endl;
    std::cout << "length == " << sub.length() << std::endl;

    std::csub_match::difference_type dif = std::distance(sub.first, sub.second);
    std::cout << "difference == " << dif << std::endl;

    std::csub_match::iterator first = sub.first;
    std::csub_match::iterator last = sub.second;
    std::cout << "range == " << std::string(first, last)
        << std::endl;
    std::cout << "string == " << sub << std::endl;

    std::csub_match::value_type const *ptr = "aab";
    std::cout << "compare(\"aab\") == "
        << sub.compare(ptr) << std::endl;
    std::cout << "compare(string) == "
        << sub.compare(std::string("AAA")) << std::endl;
    std::cout << "compare(sub) == "
        << sub.compare(sub) << std::endl;

    return (0);
    }
```

```Output
matched == true
length == 3
difference == 3
range == aaa
string == aaa
compare("aab") == -1
compare(string) == 1
compare(sub) == 0
```

## <a name="requirements"></a>要求

**标头：**\<regex 1>

**命名空间：** std

## <a name="compare"></a>  sub_match::compare

将子匹配项与序列进行比较。

```cpp
int compare(const sub_match& right) const;
int compare(const basic_string<value_type>& str) const;
int compare(const value_type *ptr) const;
```

### <a name="parameters"></a>参数

*right*<br/>
要比较的子匹配项。

*str*<br/>
要与之比较的字符串。

*ptr*<br/>
要比较的以 null 结尾的序列。

### <a name="remarks"></a>备注

第一个成员函数将匹配序列 `[first, second)` 与匹配序列 `[right.first, right.second)` 进行比较。 第二个成员函数将匹配序列 `[first, second)` 与字符序列 `[right.begin(), right.end())` 进行比较。 第三个成员函数将匹配序列 `[first, second)` 与字符序列 `[right, right + std::char_traits<value_type>::length(right))` 进行比较。

每个函数的返回结果：

如果匹配序列中的第一个不同值小于操作数序列中的相应元素（如 `std::char_traits<value_type>::compare` 所确定），或二者前缀相同但目标序列较长，则返回一个负值

如果二者的元素一一对应且长度相同，则返回零

否则返回正值

## <a name="difference_type"></a>  sub_match::difference_type

迭代器差异的类型。

```cpp
typedef typename iterator_traits<BidIt>::difference_type difference_type;
```

### <a name="remarks"></a>备注

typedef 是 `iterator_traits<BidIt>::difference_type`的同义词。

## <a name="iterator"></a>  sub_match::iterator

迭代器的类型。

```cpp
typedef BidIt iterator;
```

### <a name="remarks"></a>备注

typedef 是模板类型参数 `Bidit` 的同义词。

## <a name="length"></a>  sub_match::length

返回子匹配项的长度。

```cpp
difference_type length() const;
```

### <a name="remarks"></a>备注

如果没有任何匹配的序列，则成员函数返回匹配的序列的长度或零。

## <a name="matched"></a>  sub_match::matched

指示是否匹配成功。

```cpp
bool matched;
```

### <a name="remarks"></a>备注

成员保留 **，则返回 true**仅当与关联的捕获组`*this`是正则表达式匹配的一部分。

## <a name="op_basic_string_lt_value_type_gt"></a>sub_match::operator basic_string&lt;value_type&gt;

将子匹配转换为字符串。

```cpp
operator basic_string<value_type>() const;
```

### <a name="remarks"></a>备注

该成员运算符将返回 `str()`。

## <a name="str"></a>  sub_match::str

将子匹配转换为字符串。

```cpp
basic_string<value_type> str() const;
```

### <a name="remarks"></a>备注

成员函数返回 `basic_string<value_type>(first, second)`。

## <a name="value_type"></a>  sub_match::value_type

元素的类型。

```cpp
typedef typename iterator_traits<BidIt>::value_type value_type;
```

### <a name="remarks"></a>备注

typedef 是 `iterator_traits<BidIt>::value_type`的同义词。

## <a name="see-also"></a>请参阅

[\<regex>](../standard-library/regex.md)<br/>
[sub_match](../standard-library/sub-match-class.md)<br/>

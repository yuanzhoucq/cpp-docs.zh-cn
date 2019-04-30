---
title: '&lt;string_view&gt;运算符'
ms.date: 04/19/2019
f1_keywords:
- xstring/basic_string_view::operator!=
- xstring/basic_string_view::operator&gt;
- xstring/basic_string_view::operator&gt;=
- xstring/basic_string_view::operator&lt;
- xstring/basic_string_view::operator&lt;&lt;
- xstring/basic_string_view::operator&lt;=
- xstring/basic_string_view::operator+
- xstring/basic_string_view::operator==
helpviewer_keywords:
- std::basic_string_view::operator!=
- std::basic_string_view::operator&gt;
- std::basic_string_view::operator&gt;=
- std::basic_string_view::operator&lt;
- std::basic_string_view::operator&lt;&lt;
- std::basic_string_view::operator&lt;=, std::basic_string_view::operator==
ms.openlocfilehash: 1fbb7faf7d6fc92a053c0f4d47575c5c53c7968e
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "64346915"
---
# <a name="ltstringviewgt-operators"></a>&lt;string_view&gt;运算符

这些运算符用于比较两个 string_view 对象，或 string_view 和一些其他字符串对象 (例如[std:: string](basic-string-class.md)，或**char\***) 为提供的隐式转换。 

||||
|-|-|-|
|[operator!=](#op_neq)|[operator&gt;](#op_gt)|[operator&gt;=](#op_gt_eq)|
|[operator&lt;](#op_lt)|[operator&lt;&lt;](#op_lt_lt)|[operator&lt;=](#op_lt_eq)|
|[operator==](#op_eq_eq)|[operator""sv](#op_sv)|

## <a name="op_neq"></a> 运算符 ！ =

测试运算符左侧的对象是否不等于右侧的对象。

```cpp
template <class CharType, class Traits>
bool operator!=(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator!=(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator!=(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>参数

*left*<br/>
任何无法转换的字符串类型或类型的对象`basic_string_view`进行比较。

*right*<br/>
任何无法转换的字符串类型或类型的对象`basic_string_view`进行比较。

### <a name="return-value"></a>返回值

**true**如果运算符左侧的对象不是按字典顺序等于右侧的对象; 否则为**false**。

### <a name="remarks"></a>备注

必须存在从隐式转换*convertible_string_type*到 string_view 的另一端。 

比较基于元素的字符序列按字典序比较。 如果它们具有相同数目的元素，并且元素为均相等，则两个对象相等。 否则，它们不相等。

## <a name="op_eq_eq"></a> 运算符 = =

测试运算符左侧的对象是否等于右侧的对象。

```cpp
template <class CharType, class Traits>
bool operator==(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator==(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator==(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>参数

*left*<br/>
任何无法转换的字符串类型或类型的对象`basic_string_view`进行比较。

*right*<br/>
任何无法转换的字符串类型或类型的对象`basic_string_view`进行比较。

### <a name="return-value"></a>返回值

**true**运算符左侧的对象是否按字典顺序等于右侧的对象; 否则为**false**。

### <a name="remarks"></a>备注

必须存在从隐式转换*convertible_string_type*到 string_view 的另一端。 

比较基于元素的字符序列按字典序比较。 如果它们具有相同数目的元素，并且元素为均相等，则两个对象相等。


## <a name="op_lt"></a> 运算符&lt;

测试运算符左侧的对象是否小于右侧 sidestring_view 上的对象
```cpp
template <class CharType, class Traits>
bool operator<(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator<(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator<(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>参数

*left*<br/>
任何无法转换的字符串类型或类型的对象`basic_string_view`进行比较。

*right*<br/>
任何无法转换的字符串类型或类型的对象`basic_string_view`进行比较。

### <a name="return-value"></a>返回值

**true**如果运算符左侧的对象是按字典顺序小于对象右侧; 否则为**false**。

### <a name="remarks"></a>备注

必须存在从隐式转换*convertible_string_type*到 string_view 的另一端。 

比较基于元素的字符序列按字典序比较。 当遇到字符的第一个不相等对时，返回该比较的结果。 如果找到任何不相等的字符，但一个序列长度较短，较短的序列小于长的一个。 换而言之，"cat"小于"猫"。

### <a name="example"></a>示例

```cpp
#include <string>
#include <string_view>

using namespace std;

int main()
{
    string_view sv1 { "ABA" };
    string_view sv2{ "ABAC" };
    string_view sv3{ "ABAD" };
    string_view sv4{ "ABACE" };

    bool result = sv2 > sv1; // true
    result = sv3 > sv2; // true
    result = sv3 != sv1; // true
    result = sv4 < sv3; // true because `C` < `D`
}
```

## <a name="op_lt_eq"></a> 运算符&lt;=

测试运算符左侧的对象是否小于或等于右侧的对象。

```cpp
template <class CharType, class Traits>
bool operator<=(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator<=(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator<=(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>参数

*left*<br/>
任何无法转换的字符串类型或类型的对象`basic_string_view`进行比较。

*right*<br/>
任何无法转换的字符串类型或类型的对象`basic_string_view`进行比较。

### <a name="return-value"></a>返回值

**true**如果运算符左侧的对象是按照字典顺序小于或等于右侧的对象，; 否则为**false**。

### <a name="remarks"></a>备注

请参阅[运算符&lt;](#op_lt)。

## <a name="op_lt_lt"></a> 运算符&lt;&lt;

将 string_view 写入到输出流。

```cpp
template <class CharType, class Traits>
inline basic_ostream<CharType, Traits>& operator<<(
    basic_ostream<CharType, Traits>& Ostr, const basic_string_view<CharType, Traits> Str);
```

### <a name="parameters"></a>参数

*Ostr*<br/>
正在写入到输出流。

*Str*<br/>
要输入到输出流 string_view。

### <a name="return-value"></a>返回值

正在写入到输出流。

### <a name="remarks"></a>备注

使用此运算符将 string_view 的内容插入到输出流，例如使用[std:: cout](iostream.md#cout)。

## <a name="op_gt"></a> 运算符&gt;

测试运算符左侧的对象是否大于右侧的对象。

```cpp
template <class CharType, class Traits>
bool operator>(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator>(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator>(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>参数

*left*<br/>
任何无法转换的字符串类型或类型的对象`basic_string_view`进行比较。

*right*<br/>
任何无法转换的字符串类型或类型的对象`basic_string_view`进行比较。

### <a name="return-value"></a>返回值

**true**运算符左侧的对象是否按字典顺序大于右侧的 string_view 对象; 否则为**false**。

### <a name="remarks"></a>备注

请参阅[运算符&lt;](#op_lt)。

## <a name="op_gt_eq"></a> 运算符&gt;=

测试运算符左侧的对象是否大于或等于右侧的对象。

```cpp
template <class CharType, class Traits>
bool operator>=(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator>=(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator>=(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>参数

*left*<br/>
任何无法转换的字符串类型或类型的对象`basic_string_view`进行比较。

*right*<br/>
任何无法转换的字符串类型或类型的对象`basic_string_view`进行比较。

### <a name="return-value"></a>返回值

**true**运算符左侧的对象是否按字典顺序大于或等于右侧的对象; 否则为**false**。

### <a name="remarks"></a>备注

请参阅[运算符&lt;](#op_lt)。

## <a name="op_sv"></a> 运算符""sv (string_view 文本)

构造 string_view 从字符串文字。 需要命名空间`std::literals::string_view_literals`。 

### <a name="example"></a>示例

```cpp

using namespace std;
using namespace literals::string_view_literals;

    string_view sv{ "Hello"sv };
    wstring_view wsv{ L"Hello"sv };
    u16string_view sv16{ u"Hello"sv };
    u32string_view sv32{ U"Hello"sv };
```

## <a name="see-also"></a>请参阅

[\<string_view>](../standard-library/string-view.md)<br/>

---
title: basic_string_view 类
ms.date: 04/20/2019
f1_keywords:
- xstring/std::basic_string_view
- xstring/std::basic_string_view::allocator_type
- xstring/std::basic_string_view::const_iterator
- xstring/std::basic_string_view::const_pointer
- xstring/std::basic_string_view::const_reference
- xstring/std::basic_string_view::const_reverse_iterator
- xstring/std::basic_string_view::difference_type
- xstring/std::basic_string_view::iterator
- xstring/std::basic_string_view::npos
- xstring/std::basic_string_view::pointer
- xstring/std::basic_string_view::reference
- xstring/std::basic_string_view::reverse_iterator
- xstring/std::basic_string_view::size_type
- xstring/std::basic_string_view::traits_type
- xstring/std::basic_string_view::value_type
- xstring/std::basic_string_view::append
- xstring/std::basic_string_view::assign
- xstring/std::basic_string_view::at
- xstring/std::basic_string_view::back
- xstring/std::basic_string_view::begin
- xstring/std::basic_string_view::c_str
- xstring/std::basic_string_view::capacity
- xstring/std::basic_string_view::cbegin
- xstring/std::basic_string_view::cend
- xstring/std::basic_string_view::clear
- xstring/std::basic_string_view::compare
- xstring/std::basic_string_view::copy
- xstring/std::basic_string_view::_Copy_s
- xstring/std::basic_string_view::crbegin
- xstring/std::basic_string_view::crend
- xstring/std::basic_string_view::data
- xstring/std::basic_string_view::empty
- xstring/std::basic_string_view::end
- xstring/std::basic_string_view::erase
- xstring/std::basic_string_view::find
- xstring/std::basic_string_view::find_first_not_of
- xstring/std::basic_string_view::find_first_of
- xstring/std::basic_string_view::find_last_not_of
- xstring/std::basic_string_view::find_last_of
- xstring/std::basic_string_view::front
- xstring/std::basic_string_view::get_allocator
- xstring/std::basic_string_view::insert
- xstring/std::basic_string_view::length
- xstring/std::basic_string_view::max_size
- xstring/std::basic_string_view::pop_back
- xstring/std::basic_string_view::push_back
- xstring/std::basic_string_view::rbegin
- xstring/std::basic_string_view::rend
- xstring/std::basic_string_view::remove_prefix
- xstring/std::basic_string_view::remove_suffix
- xstring/std::basic_string_view::replace
- xstring/std::basic_string_view::reserve
- xstring/std::basic_string_view::resize
- xstring/std::basic_string_view::rfind
- xstring/std::basic_string_view::shrink_to_fit
- xstring/std::basic_string_view::size
- xstring/std::basic_string_view::substr
- xstring/std::basic_string_view::swap
helpviewer_keywords:
- std::basic_string_view
- std::basic_string_view, allocator_type
- std::basic_string_view, const_iterator
- std::basic_string_view, const_pointer
- std::basic_string_view, const_reference
- std::basic_string_view, const_reverse_iterator
- std::basic_string_view, difference_type
- std::basic_string_view, iterator
- std::basic_string_view, npos
- std::basic_string_view, pointer
- std::basic_string_view, reference
- std::basic_string_view, reverse_iterator
- std::basic_string_view, size_type
- std::basic_string_view, traits_type
- std::basic_string_view, value_type
- std::basic_string_view, append
- std::basic_string_view, assign
- std::basic_string_view, at
- std::basic_string_view, back
- std::basic_string_view, begin
- std::basic_string_view, c_str
- std::basic_string_view, capacity
- std::basic_string_view, cbegin
- std::basic_string_view, cend
- std::basic_string_view, clear
- std::basic_string_view, compare
- std::basic_string_view, copy
- std::basic_string_view, crbegin
- std::basic_string_view, crend
- std::basic_string_view, data
- std::basic_string_view, empty
- std::basic_string_view, end
- std::basic_string_view, erase
- std::basic_string_view, find
- std::basic_string_view, find_first_not_of
- std::basic_string_view, find_first_of
- std::basic_string_view, find_last_not_of
- std::basic_string_view, find_last_of
- std::basic_string_view, front
- std::basic_string_view, get_allocator
- std::basic_string_view, insert
- std::basic_string_view, length
- std::basic_string_view, max_size
- std::basic_string_view, pop_back
- std::basic_string_view, push_back
- std::basic_string_view, rbegin
- std::basic_string_view, rend
- std::basic_string_view, remove_prefix
- std::basic_string_view, remove_suffix
- std::basic_string_view, replace
- std::basic_string_view, reserve
- std::basic_string_view, resize
- std::basic_string_view, rfind
- std::basic_string_view, shrink_to_fit
- std::basic_string_view, size
- std::basic_string_view, substr
- std::basic_string_view, swap
ms.assetid: a9c3e0a2-39bf-4c8a-b093-9abe30839591
ms.openlocfilehash: 0ac5e3d528881f7b1caa0a1dcdae0161a6777e57
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "64346935"
---
# <a name="basicstringview-class"></a>basic_string_view 类

类模板`basic_string_view<charT>`C + + 17，将其作为函数可以接受各种安全、 高效的方法不相关的字符串类型而无需具有要模板化这些类型的函数中添加了。 类包含一系列连续字符数据，并在序列中指定的字符数的长度非拥有指针。 相对于序列是否是以 null 结尾不进行任何假设。

标准库定义的元素的类型所基于的多个专用化：

-  `string_view`
-  `wstring_view`
-  `u16string_view`
-  `u32string_view`

在本文档中，术语"string_view"指通常任何这些 typedef。

String_view 介绍读取字符串数据所需的最小公共接口。 它提供对基础数据; const 访问它使任何副本 (除`copy`函数)。 数据可能会或可能不包含 null 值 (\0) 在任意位置。 String_view 具有无法控制对象的生存期。 它是调用方负责确保基础字符串数据有效。

可接受的参数的类型 string_view 的函数以使用任何类似于字符串的类型，而无需使函数成为一个模板，或限制对特定子集的字符串类型的函数。 唯一要求是存在从字符串类型的隐式转换到 string_view。 所有的标准字符串类型都隐式转换为包含相同的元素类型 string_view。 换而言之，`std::string`转换为`string_view`而不适用于`wstring_view`。

下面的示例演示非模板函数`f`带有类型的参数的`wstring_view`。 它可调用类型的参数`std::wstring`， `wchar_t*`，和`winrt::hstring`。

```cpp
// compile with: /std:c++17
// string_view that uses elements of wchar_t
void f(wstring_view);

// pass a std::wstring:
const std::wstring& s { L"Hello" };
f(s);

// pass a C-style null-terminated string (string_view is not null-terminated):
const wchar_t* ns = L"Hello";
f(ns);

// pass a C-style character array of len characters (excluding null terminator):
const wchar_t* cs { L"Hello" };
size_t len { 5 };
f({cs,len});

// pass a WinRT string
winrt::hstring hs { L"Hello" };
f(hs);
```

## <a name="syntax"></a>语法

```cpp
template <class CharType, class Traits = char_traits<CharType>>
class basic_string_view;
```

### <a name="parameters"></a>参数

*CharType*<br/>
存储在 string_view 的字符的类型。 C++标准库为此模板的专用化提供了以下的 typedef。
- [string_view](../standard-library/string-view-typedefs.md#string_view)类型的元素**char**
- [wstring_view](../standard-library/string-view-typedefs.md#wstring_view)，为**wchar_t**
- [u16string_view](../standard-library/string-view-typedefs.md#u16string_view) for **char16_t**
- [u32string_view](../standard-library/string-view-typedefs.md#u32string_view)有关**char32_t**。

*特征*<br/>
默认情况下[char_traits](char-traits-struct.md)<*CharType*>。

### <a name="constructors"></a>构造函数

|构造函数|描述|
|-|-|
|[basic_string_view](#basic_string_view)|构造 string_view 的为空，否则指向所有或某些其他一个字符串对象的数据的一部分或 C 样式字符数组。|

### <a name="typedefs"></a>Typedef

|类型名称|描述|
|-|-|
|**const_iterator**|随机访问迭代器，可以读取**const**元素。|
|**const_pointer**|`using const_pointer = const value_type*;`|
|**const_reference**|`using const_reference = const value_type&;`|
|**const_reverse_iterator**|`using const_reverse_iterator = std::reverse_iterator<const_iterator>;`|
|**difference_type**|`using difference_type = ptrdiff_t;`|
|**Iterator**|`using iterator = const_iterator;`|
|**npos**|`static constexpr size_type npos = size_type(-1);`|
|**pointer**|`using pointer = value_type*;`|
|**reference**|`using reference = value_type&;`|
|**reverse_iterator**|`using reverse_iterator = const_reverse_iterator;`|
|**size_type**|`using size_type = size_t;`|
|**traits_type**|`using traits_type = Traits;`|
|**value_type**|`using value_type = CharType;`|

### <a name="member-operators"></a>成员运算符

|运算符|描述|
|-|-|
|[operator=](#op_eq)|将 string_view 或可转换为字符串对象分配给另一个 string_view。|
|[operator\[\]](#op_at)|返回指定索引处的元素。|

### <a name="member-functions"></a>成员函数

|成员函数|描述|
|-|-|
|[at](#at)|返回指定位置处的元素 const_reference。|
|[back](#back)|最后一个元素返回 const_reference。|
|[begin](#begin)|返回的第一个元素的常量迭代器。 （string_views 是不可变。）|
|[cbegin](#cbegin)|与相同[开始](#begin)。|
|[cend](#cend)|返回指向一个过去的最后一个元素的常量迭代器。|
|[copy](#copy)|最多指定的数目的字符将从复制中源 string_view 的索引位置到目标字符数组。 （不建议这样做。 改为使用 _Copy_s。）|
|[_Copy_s](#_copy_s)|是安全的 CRT 副本函数。|
|[compare](#compare)|将使用以确定它们是否相等或如果其中一个按字典顺序小于另指定 string_view string_view 进行比较。|
|[crbegin](#crbegin)|与相同[rbegin](#rbegin)。|
|[crend](#crend)|与相同[rend](#rend)。|
|[data](#data)|返回原始的非拥有指针与字符序列。|
|[empty](#empty)|测试是否 string_view 包含字符。|
|[end](#end)|与相同[cend](#cend)。|
|[find](#find)|指定的字符序列匹配的子字符串的第一个匹配项向前搜索。|
|[find_first_not_of](#find_first_not_of)|搜索不是指定的 string_view 或无法转换的字符串对象的任何元素的第一个字符。|
|[find_first_of](#find_first_of)|搜索指定的 string_view 或无法转换的字符串对象的任何元素匹配的第一个字符。|
|[find_last_not_of](#find_last_not_of)|搜索不是指定的 string_view 或无法转换的字符串对象的任何元素的最后一个字符。|
|[find_last_of](#find_last_of)|是指定的 string_view 或无法转换的字符串对象的一个元素的最后一个字符的搜索。|
|[front](#front)|返回第一个元素 const_reference。|
|[length](#length)|返回当前的元素数。|
|[max_size](#max_size)|返回的最大 string_view 可能包含的字符数。|
|[rbegin](#rbegin)|返回发现反向 string_view 中的第一个元素的常量迭代器。|
|[remove_prefix](#remove_prefix)|将指针向前移动指定数量的元素。|
|[remove_suffix](#remove_suffix)|视图的大小减少指定数量的元素从后开始。|
|[rend](#rend)|返回一个常量迭代器指向一个反向 string_view 的最后一个元素之后。|
|[rfind](#rfind)|搜索指定的字符序列匹配的子字符串的第一个匹配项的反向 string_view。|
|[size](#size)|返回当前的元素数。|
|[substr](#substr)|返回指定索引处开始的指定长度的子字符串。|
|[swap](#swap)|交换两个 string_views 的内容。|

## <a name="remarks"></a>备注

如果要求函数生成的序列长于 [max_size](#max_size) 元素，这个函数将通过引发 [length_error](../standard-library/length-error-class.md) 类型的对象来报告长度错误。

## <a name="requirements"></a>要求

[/std: c + + 17](../build/reference/std-specify-language-standard-version.md)或更高版本

**标头：** \<string_view >

**命名空间：** std

## <a name="at"></a>  basic_string_view::at

返回从 0 开始的指定索引处的字符 const_reference。

```cpp
constexpr const_reference at(size_type offset) const;
```

### <a name="parameters"></a>参数

*offset*<br/>
要引用的元素的索引。

### <a name="return-value"></a>返回值

到位于指定的参数索引位置处的字符 const_reference。

### <a name="remarks"></a>备注

第一个元素的索引为零和后续元素由正整数，连续索引，以便长度 string_view *n*已*n*th 元素编制索引的数量*n-* 1。 **在**不同于引发无效索引异常[运算符\[\]](#op_at)。 

一般情况下，我们建议**处**如序列`std::vector`，string_view 应永远不会使用。 无效的索引传递给序列是应发现并修复了在开发过程的逻辑错误。 如果程序不完全确定其索引都有效，它应该对其进行测试，不调用 at()，并根据异常来抵御粗心的编程。

请参阅[basic_string_view::operator\[ \] ](#op_at)有关详细信息。

### <a name="example"></a>示例

```cpp
// basic_string_view_at.cpp
// compile with: /EHsc
#include <string_view>
#include <iostream>

int main()
{
    using namespace std;

    const string_view  str1("Hello world");
    string_view::const_reference refStr2 = str1.at(8); // 'r'
}
```

## <a name="back"></a>  basic_string_view::back

最后一个元素返回 const_reference。

```cpp
constexpr const_reference back() const;
```

### <a name="return-value"></a>返回值

最后一个元素中 string_view const_reference。

### <a name="remarks"></a>备注

String_view 是否为空，则引发异常。

请记住，string_view 修改后，例如通过调用`remove_suffix`，则此函数返回的元素不能再为基础数据中的最后一个元素。

### <a name="example"></a>示例

使用 C 字符串文本构造 string_view 不包括终止 null，因此在下面的示例`back`返回 p 和不 \0。

```cpp
char c[] = "Help"; // char[5]
string_view sv{ c };
cout << sv.size(); // size() == 4
cout << sv.back() << endl; // p 
```

内嵌的 null 值被视为其他任何字符：

```cpp
string_view e = "embedded\0nulls"sv;
cout << boolalpha << (e.back() == 's'); // true
```

## <a name="basic_string_view"></a>  basic_string_view::basic_string_view

构造 string_view。

```cpp
constexpr basic_string_view() noexcept;
constexpr basic_string_view(const basic_string_view&) noexcept = default;
constexpr basic_string_view(const charT* str);
constexpr basic_string_view(const charT* str, size_type len);
```

### <a name="parameters"></a>参数

*str*<br/>
指向字符值的指针。

len<br/>
要在视图中包含的字符数。

## <a name="remarks"></a>备注

使用图表 * 参数的构造函数假设以 null 结尾的输入是但 string_view 中不包括终止 null。

您还可以构造 string_view 为文字。 请参阅[运算符""sv](string-view-operators.md#op_sv)。

## <a name="begin"></a>  basic_string_view::begin

与相同[cbegin](#cbegin)。

```cpp
constexpr const_iterator begin() const noexcept;
```

### <a name="return-value"></a>返回值
返回的第一个元素的 const_iterator。

## <a name="cbegin"></a>  basic_string_view::cbegin

返回范围中的第一个元素的 const_iterator。

```cpp
constexpr const_iterator cbegin() const noexcept;
```

### <a name="return-value"></a>返回值

一个**const**指向的范围或刚超出空范围末尾的位置的第一个元素的随机访问迭代器 (对于空范围， `cbegin() == cend()`)。

## <a name="cend"></a>  basic_string_view::cend

返回刚超出范围中的最后一个元素的位置的 const_iterator。

```cpp
constexpr const_iterator cend() const noexcept;
```

### <a name="return-value"></a>返回值

一个**const**指向刚超出范围末尾的随机访问迭代器。

### <a name="remarks"></a>备注

不应对 `cend` 返回的值取消引用。

## <a name="compare"></a> basic_string_view::compare

通过使用指定的 string_view （或无法转换的字符串类型） 来确定两个对象是否相等或如果其中一个按字典顺序小于另区分大小写比较。 [ \<String_view > 运算符](string-view-operators.md)使用此成员函数来执行比较。

```cpp
constexpr int compare(basic_string_view strv) const noexcept;
constexpr int compare(size_type pos, size_type num, basic_string_view strv) const;
constexpr int compare(size_type pos, size_type num, basic_string_view strv, size_type offset, size_type num2) const;
constexpr int compare(const charT* ptr) const;
constexpr int compare(size_type pos, size_type num, const charT* ptr) const;
constexpr int compare(size_type pos, size_type num, const charT* ptr, size_type num2) const;
```

### <a name="parameters"></a>参数

*strv*<br/>
与此 string_view 比较 string_view。

*pos*<br/>
开始比较此 string_view 的索引。

*num*<br/>
此 string_view 进行比较的字符数目上限。

*num2*<br/>
最大字符数*strv*进行比较。

*offset*<br/>
索引*strv*在此处开始比较。

*ptr*<br/>
要与此 string_view 进行比较的 C 字符串。

### <a name="return-value"></a>返回值

如果此 string_view 是负值小于*strv*或*ptr*; 为零，如果两个字符序列是相等; 或一个正值，如果此 string_view 大于*strv*或*ptr*。

### <a name="remarks"></a>备注

`compare`成员函数执行的全部或一部分的每个字符序列的区分大小写比较。 

### <a name="example"></a>示例

```cpp
// basic_string_view_compare.cpp
// compile with: /EHsc
#include <string_view>
#include <iostream>
#include <string>

using namespace std;

string to_alpha(int result)
{
   if (result < 0) return " less than ";
   else if (result == 0) return " equal to ";
   else return " greater than ";
}

int main()
{
   // The first member function compares
   // two string_views
   string_view sv_A("CAB");
   string_view sv_B("CAB");
   cout << "sv_A is " << sv_A << endl;
   cout << "sv_B is " << sv_B << endl;
   int comp1 = sv_A.compare(sv_B);
   cout << "sv_A is" << to_alpha(comp1) << "sv_B.\n";

   // The second member function compares part of
   // an operand string_view to another string_view
   string_view sv_C("AACAB");
   string_view sv_D("CAB");
   cout << "sv_C is: " << sv_C << endl;
   cout << "sv_D is: " << sv_D << endl;
   int comp2a = sv_C.compare(2, 3, sv_D);
   cout << "The last three characters of sv_C are" 
       << to_alpha(comp2a) << "sv_D.\n";

   int comp2b = sv_C.compare(0, 3, sv_D);
   cout << "The first three characters of sv_C are" 
       << to_alpha(comp2b) << "sv_D.\n";

   // The third member function compares part of
   // an operand string_view to part of another string_view
   string_view sv_E("AACAB");
   string_view sv_F("DCABD");
   cout << "sv_E: " << sv_E << endl;
   cout << "sv_F is: " << sv_F << endl;
   int comp3a = sv_E.compare(2, 3, sv_F, 1, 3);
   cout << "The three characters from position 2 of sv_E are"
       << to_alpha(comp3a) 
       << "the 3 characters of sv_F from position 1.\n";

   // The fourth member function compares
   // an operand string_view to a C string
   string_view sv_G("ABC");
   const char* cs_A = "DEF";
   cout << "sv_G is: " << sv_G << endl;
   cout << "cs_A is: " << cs_A << endl;
   int comp4a = sv_G.compare(cs_A);
   cout << "sv_G is" << to_alpha(comp4a) << "cs_A.\n";

   // The fifth member function compares part of
   // an operand string_view to a C string
   string_view sv_H("AACAB");
   const char* cs_B = "CAB";
   cout << "sv_H is: " << sv_H << endl;
   cout << "cs_B is: " << cs_B << endl;
   int comp5a = sv_H.compare(2, 3, cs_B);
   cout << "The last three characters of sv_H are"
      << to_alpha(comp5a) << "cs_B.\n";

   // The sixth member function compares part of
   // an operand string_view to part of an equal length of
   // a C string
   string_view sv_I("AACAB");
   const char* cs_C = "ACAB";
   cout << "sv_I is: " << sv_I << endl;
   cout << "cs_C: " << cs_C << endl;
   int comp6a = sv_I.compare(1, 3, cs_C, 3);
   cout << "The 3 characters from position 1 of sv_I are"
      << to_alpha(comp6a) << "the first 3 characters of cs_C.\n";
}
```

```Output
sv_A is CAB
sv_B is CAB
sv_A is equal to sv_B.
sv_C is: AACAB
sv_D is: CAB
The last three characters of sv_C are equal to sv_D.
The first three characters of sv_C are less than sv_D.
sv_E: AACAB
sv_F is: DCABD
The three characters from position 2 of sv_E are equal to the 3 characters of sv_F from position 1.
sv_G is: ABC
cs_A is: DEF
sv_G is less than cs_A.
sv_H is: AACAB
cs_B is: CAB
The last three characters of sv_H are equal to cs_B.
sv_I is: AACAB
cs_C: ACAB
The 3 characters from position 1 of sv_I are equal to the first 3 characters of cs_C.
```

## <a name="copy"></a>  basic_string_view::copy

最多指定的数目的字符将从复制中源 string_view 的索引位置到目标字符数组。 我们建议使用安全的函数[basic_string_view::_Copy_s](#_copy_s)相反。

```cpp
size_type copy(charT* ptr, size_type count, size_type offset = 0) const;
```

### <a name="parameters"></a>参数

*ptr*<br/>
要复制的元素的目标字符数组。

*count*<br/>
要从中复制，最多源 string_view 的字符数。

*offset*<br/>
要从中复制源 string_view 中的开始位置。

### <a name="return-value"></a>返回值

实际复制的字符数。

### <a name="remarks"></a>备注

空字符不追加到副本的末尾。

## <a name="_copy_s"></a>  basic_string_view::_Copy_s

保护而不是要使用 CRT 复制函数[复制](#copy)。

```cpp
size_type _Copy_s(
    value_type* dest,
    size_type dest_size,
    size_type count,
    size_type _Off = 0) const;
```

### <a name="parameters"></a>参数

*dest*<br/>
要复制的元素的目标字符数组。

*dest_size*<br/>
大小*dest*。

_*计数*要最多从复制的源字符串的字符数。

*_Off*<br/>
要进行复制的源字符串中的开始位置。

### <a name="return-value"></a>返回值

实际复制的字符数。

### <a name="remarks"></a>备注

空字符不追加到副本的末尾。

 有关详细信息，请参阅[c-runtime-library/security-features-in-the-crt](../c-runtime-library/security-features-in-the-crt.md)。

## <a name="crbegin"></a>  basic_string_view::crbegin

返回发现反向 string_view 中的第一个元素 const_reverse_iterator。

```cpp
constexpr const_reverse_iterator crbegin() const noexcept;
```

### <a name="return-value"></a>返回值

Const_reverse_iterator 反向 string_view 中的第一个元素。 

## <a name="crend"></a>  basic_string_view::crend

与相同[rend](#rend)。 

```cpp
constexpr const_reverse_iterator crend() const noexcept;
```

### <a name="return-value"></a>返回值

返回某个超出末尾的反向 string_view const_reverse_iterator。

## <a name="data"></a>  basic_string_view::data

返回到的对象，用于构造 string_view const 的字符序列的原始非拥有指针。

```cpp
constexpr value_type *data() const noexcept;
```

### <a name="return-value"></a>返回值

一个指针-到-常量字符序列的第一个元素。

### <a name="remarks"></a>备注

指针不能修改字符。

String_view 字符序列不一定以 null 结尾。 返回类型`data`不是有效的 C 字符串，因为获取不附加任何空字符。 Null 字符 \0 类型 string_view 的对象中没有任何特殊的意义，并可能属于 string_view 对象就像任何其他字符一样。

## <a name="empty"></a>  basic_string_view::empty

测试是否 string_view 或不包含字符。

```cpp
constexpr bool empty() const noexcept;
```

### <a name="return-value"></a>返回值

**true** string_view 对象不包含任何字符; 如果**false**如果它具有至少一个字符。

### <a name="remarks"></a>备注

成员函数等效于[大小](#size)（) = = 0。

## <a name="end"></a>  basic_string_view::end

返回指向一个过去的最后一个元素的随机访问 const_iterator。

```cpp
constexpr const_iterator end() const noexcept;
```

### <a name="return-value"></a>返回值

返回指向一个过去的最后一个元素的随机访问 const_iterator。

### <a name="remarks"></a>备注

`end` 用于测试是否 const_iterator 已到达其 string_view 的末尾。 不应对 `end` 返回的值取消引用。

## <a name="find"></a>  basic_string_view::find

字符或指定的字符序列匹配的子字符串的第一个匹配项向前搜索 string_view。

```cpp
constexpr size_type find(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find(const charT* ptr, size_type offset = 0) const;
```

### <a name="parameters"></a>参数

*str*<br/>
为其成员函数是搜索 string_view。

*chVal*<br/>
成员函数要搜索的字符值。

*offset*<br/>
搜索即将开始的索引。

*ptr*<br/>
C 为其成员函数要搜索字符串。

*count*<br/>
中的字符数*ptr*，从第一个字符开始计数。

### <a name="return-value"></a>返回值

搜索成功时，则为搜索的子字符串的首个字符的索引；否则为 `npos`。

## <a name="find_first_not_of"></a>  basic_string_view::find_first_not_of

搜索不是指定的 string_view 或无法转换的字符串对象的元素的第一个字符。

```cpp
constexpr size_type find_first_not_of(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find_first_not_of(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find_first_not_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_first_not_of(const charT* ptr, size_type offset = 0) const;
```

### <a name="parameters"></a>参数

*str*<br/>
为其成员函数是搜索 string_view。

*chVal*<br/>
成员函数要搜索的字符值。

*offset*<br/>
搜索即将开始的索引。

*ptr*<br/>
C 为其成员函数要搜索字符串。

*count*<br/>
从为其成员函数是要搜索的 C 字符串中的第一个字符开始计数的字符数。

### <a name="return-value"></a>返回值

搜索成功时，则为搜索的子字符串的首个字符的索引；否则为 `npos`。

## <a name="find_first_of"></a>  basic_string_view::find_first_of

搜索指定 string_view 任何元素匹配的第一个字符。

```cpp
constexpr size_type find_first_of(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find_first_of(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find_first_of(const charT* str, size_type offset, size_type count) const;
constexpr size_type find_first_of(const charT* str, size_type offset = 0) const;
```

### <a name="parameters"></a>参数

*chVal*<br/>
成员函数要搜索的字符值。

*offset*<br/>
搜索即将开始的索引。

*ptr*<br/>
C 为其成员函数要搜索字符串。

*count*<br/>
从为其成员函数是要搜索的 C 字符串中的第一个字符开始计数的字符数。

*str*<br/>
为其成员函数是搜索 string_view。

### <a name="return-value"></a>返回值

搜索成功时，则为搜索的子字符串的首个字符的索引；否则为 `npos`。

## <a name="find_last_not_of"></a>  basic_string_view::find_last_not_of

搜索不是指定 string_view 任何元素的最后一个字符。

```cpp
constexpr size_type find_last_not_of(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type find_last_not_of(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type find_last_not_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_last_not_of(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>参数

*str*<br/>
为其成员函数是搜索 string_view。

*chVal*<br/>
成员函数要搜索的字符值。

*offset*<br/>
索引搜索的时间才能完成。

*ptr*<br/>
C 为其成员函数要搜索字符串。

*count*<br/>
的字符数，包括向前的第一个字符，在*ptr*。

### <a name="return-value"></a>返回值

搜索成功时，则为搜索的子字符串的首个字符的索引；否则为 `string_view::npos`。

## <a name="find_last_of"></a>  basic_string_view::find_last_of

搜索指定 string_view 任何元素匹配的最后一个字符。

```cpp
constexpr size_type find_last_of(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type find_last_of(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type find_last_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_last_of(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>参数

*str*<br/>
为其成员函数是搜索 string_view。

*chVal*<br/>
成员函数要搜索的字符值。

*offset*<br/>
索引搜索的时间才能完成。

*ptr*<br/>
C 为其成员函数要搜索字符串。

*count*<br/>
从为其成员函数是要搜索的 C 字符串中的第一个字符开始计数的字符数。

### <a name="return-value"></a>返回值

搜索成功时，则为搜索的子字符串的最后一个字符的索引；否则为 `npos`。

## <a name="front"></a>  basic_string_view::front

返回第一个元素 const_reference。

```cpp
constexpr const_reference front() const;
```

### <a name="return-value"></a>返回值

第一个元素到 const_reference。

### <a name="remarks"></a>备注

String_view 是否为空，则引发异常。

## <a name="length"></a> basic_string_view::length

返回当前的元素数。

```cpp
constexpr size_type length() const noexcept;
```

### <a name="remarks"></a>备注

成员函数与 [size](#size) 相同。

## <a name="max_size"></a>  basic_string_view::max_size

返回的最大 string_view 可以包含的字符数。

```cpp
constexpr size_type max_size() const noexcept;
```

### <a name="return-value"></a>返回值

最大 string_view 可以包含的字符数。

### <a name="remarks"></a>备注

类型的异常[length_error](../standard-library/length-error-class.md)当运算生成长度大于 string_view 时引发`max_size()`。

## <a name="op_eq"></a>  basic_string_view::operator=

将 string_view 或可转换为字符串对象分配给另一个 string_view。

```cpp
constexpr basic_string_view& operator=(const basic_string_view&) noexcept = default;
```
### <a name="example"></a>示例

```cpp
   string_view s = "Hello";
   string_view s2 = s;
```
## <a name="op_at"></a>  basic_string_view::operator[]

具有指定索引提供 const_reference 的字符。

```cpp
constexpr const_reference operator[](size_type offset) const;
```

### <a name="parameters"></a>参数

*offset*<br/>
要引用的元素的索引。

### <a name="return-value"></a>返回值

到位于指定的参数索引位置处的字符 const_reference。

### <a name="remarks"></a>备注

第一个元素的索引为零，并且后续元素由正整数，连续索引，以便长度 string_view *n*具有*n*th 元素编制索引的数量*n* -1。

`operator[]` 比成员函数更快[在](#at)提供读取访问权限的 string_view 元素。

`operator[]` 不会检查作为参数传递的索引是否有效。 无效的索引传递给`operator[]`导致未定义的行为。

如果修改或删除由所属对象的基础字符串数据，返回的引用可能会失效。

使用编译时[\_迭代器\_调试\_级别](../standard-library/iterator-debug-level.md)设置为 1 或 2，则运行时将出现错误如果你尝试访问 string_view 的边界之外的元素。 有关更多信息，请参见 [Checked Iterators](../standard-library/checked-iterators.md)。

## <a name="rbegin"></a>  basic_string_view::rbegin

返回到反向 string_view 的第一个元素的常量迭代器。

```cpp
constexpr const_reverse_iterator rbegin() const noexcept;
```

### <a name="return-value"></a>返回值

返回到反向 string_view，用于寻址相应非反向 string_view 的最后一个元素的第一个元素的随机访问迭代器。

### <a name="remarks"></a>备注

`rbegin` 用于反向 string_view 就像[开始](#begin)与 string_view 一起使用。 `rbegin` 可用于向后初始化一次迭代。

## <a name="remove_prefix"></a> basic_string_view::remove_prefix

将指针向前移动指定数量的元素。

```cpp
constexpr void remove_prefix(size_type n);
```

### <a name="remarks"></a>备注

保留单元保持不变的基础数据。 将 string_view 指针向前移动 n 个元素并设置私有`size`到大小-n 的数据成员。

## <a name="remove_suffix"></a> basic_string_view::remove_suffix

视图的大小减少指定数量的元素从后开始。

```cpp
constexpr void remove_suffix(size_type n);
```

### <a name="remarks"></a>备注

离开基础数据和指针到其原来的位置。 设置私有`size`到大小-n 的数据成员。

## <a name="rend"></a>  basic_string_view::rend

返回一个常量迭代器指向一个反向 string_view 的最后一个元素之后。

```cpp
constexpr reverse_iterator rend() const noexcept;
```

### <a name="return-value"></a>返回值

一个常量反向随机访问迭代器指向一个反向 string_view 的最后一个元素之后。

### <a name="remarks"></a>备注

`rend` 用于反向 string_view 就像[最终](#end)与 string_view 一起使用。 `rend` 可用于测试反向迭代器已到达其 string_view 末尾是否。 不应对 `rend` 返回的值取消引用。

## <a name="rfind"></a>  basic_string_view::rfind

按相反的顺序指定的字符序列匹配的子字符串搜索 string_view。

```cpp
constexpr size_type rfind(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type rfind(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type rfind(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type rfind(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>参数

*chVal*<br/>
成员函数要搜索的字符值。

*offset*<br/>
搜索即将开始的索引。

*ptr*<br/>
C 为其成员函数要搜索字符串。

*count*<br/>
从为其成员函数是要搜索的 C 字符串中的第一个字符开始计数的字符数。

*str*<br/>
为其成员函数是搜索 string_view。

### <a name="return-value"></a>返回值

当成功; 的子字符串的第一个字符的索引否则为`npos`。

## <a name="size"></a>  basic_string_view::size

在 string_view 中返回元素的数。

```cpp
constexpr size_type size() const noexcept;
```

### <a name="return-value"></a>返回值

String_view 的长度。

### <a name="remarks"></a>备注

String_view 可以修改它的长度，例如`remove_prefix`和`remove_suffix`。 这不会修改基础字符串数据，因为 string_view 的大小不一定是基础数据的大小。

## <a name="substr"></a>  basic_string_view::substr

返回表示从指定位置的指定的数量的字符 （至少） string_view。

```cpp
constexpr basic_string_view substr(size_type offset = 0, size_type count = npos) const;
```

### <a name="parameters"></a>参数

*offset*<br/>
查找从该副本，默认值为 0 位置处的元素索引。

*count*<br/>
如果它们存在的子字符串中包含的字符数。

### <a name="return-value"></a>返回值

表示指定的子序列的元素的 string_view 对象。

## <a name="swap"></a>  basic_string_view::swap

交换两个 string_views，即对基础字符串数据，大小值的指针。

```cpp
constexpr void swap(basic_string_view& sv) noexcept;
```

### <a name="parameters"></a>参数

*sv*<br/>
其指针和大小的值将要进行交换的目标 string_view 源 string_view。

## <a name="see-also"></a>请参阅

[\<string_view>](../standard-library/string-view.md)<br/>
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>

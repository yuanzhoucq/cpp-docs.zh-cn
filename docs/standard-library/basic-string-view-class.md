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
ms.openlocfilehash: ac65dca931f821c717e9c081c8d3479fd0b3bb0e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364889"
---
# <a name="basic_string_view-class"></a>basic_string_view 类

类模板`basic_string_view<charT>`在 C++17 中添加，作为函数接受各种不相关的字符串类型的一种安全有效的方法，而无需对这些类型进行模板化。 类包含指向连续字符数据序列的非拥有指针，以及指定序列中字符数的长度。 对于序列是否为 null 终止，不进行假设。

标准库根据元素的类型定义多个专门化：

- `string_view`
- `wstring_view`
- `u16string_view`
- `u32string_view`

在本文档中，"string_view"一词通常是指其中任何一个类型。

string_view描述读取字符串数据所需的最小公共接口。 它提供了对基础数据的一致访问;它不复制（`copy`函数除外）。 数据在任何位置可能包含空值 （"{0}"），也可能不包含。 string_view无法控制对象的生存期。 调用方有责任确保基础字符串数据有效。

可以使接受类型string_view参数的函数用于任何类似字符串的类型，而不将函数制作成模板，或将函数约束到字符串类型的特定子集。 唯一的要求是从字符串类型到string_view存在隐式转换。 所有标准字符串类型都隐式转换为包含相同元素类型的string_view。 换句话说，可`std::string`转换为 ，`string_view`但不能转换为 。 `wstring_view`

下面的示例显示了一个非模板函数，`f`该函数采用类型的`wstring_view`参数。 可以使用 类型`std::wstring`参数 调用`wchar_t*`， 和`winrt::hstring`。

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

*字符类型*\
存储在string_view中的字符的类型。 C++标准库为此模板的专门化提供以下类型定义。

- [字符](../standard-library/string-view-typedefs.md#string_view)**类型元素**的string_view
- [wstring_view](../standard-library/string-view-typedefs.md#wstring_view) **，wchar_t**
- [char16_tu16string_view](../standard-library/string-view-typedefs.md#u16string_view) **char16_t**
- [u32string_view](../standard-library/string-view-typedefs.md#u32string_view) **u32string_viewchar32_t。**

*性状*\
默认值为[char_traits](char-traits-struct.md)<*字符类型*>。

### <a name="constructors"></a>构造函数

|构造函数|说明|
|-|-|
|[basic_string_view](#basic_string_view)|构造空string_view，或者指向其他字符串对象的全部或部分数据或 C 样式字符数组。|

### <a name="typedefs"></a>Typedef

|类型名称|说明|
|-|-|
|**const_iterator**|随机访问迭代器，可以读取**const**元素。|
|**const_pointer**|`using const_pointer = const value_type*;`|
|**const_reference**|`using const_reference = const value_type&;`|
|**const_reverse_iterator**|`using const_reverse_iterator = std::reverse_iterator<const_iterator>;`|
|**difference_type**|`using difference_type = ptrdiff_t;`|
|**迭 代**|`using iterator = const_iterator;`|
|**npos**|`static constexpr size_type npos = size_type(-1);`|
|**指针 (pointer)**|`using pointer = value_type*;`|
|**参考**|`using reference = value_type&;`|
|**reverse_iterator**|`using reverse_iterator = const_reverse_iterator;`|
|**size_type**|`using size_type = size_t;`|
|**traits_type**|`using traits_type = Traits;`|
|**value_type**|`using value_type = CharType;`|

### <a name="member-operators"></a>会员运算符

|操作员|说明|
|-|-|
|[运算符*](#op_eq)|将string_view或可转换字符串对象分配给另一个string_view。|
|[算子\[\]](#op_at)|返回指定索引处的元素。|

### <a name="member-functions"></a>成员职能

|成员函数|说明|
|-|-|
|[在](#at)|返回const_reference到指定位置的元素。|
|[返回](#back)|返回最后一个元素的const_reference。|
|[开始](#begin)|返回处理第一个元素的 const 迭代器。 （string_views是不可变的。|
|[cbegin](#cbegin)|与[开始相同](#begin)。|
|[cend](#cend)|返回指向最后一个元素的 const 迭代器。|
|[复制](#copy)|从源string_view索引位置到目标字符数组的索引位置最多复制指定数量的字符。 （不推荐。 改用_Copy_s。|
|[_Copy_s](#_copy_s)|保护 CRT 复制功能。|
|[比较](#compare)|将string_view与指定的string_view进行比较，以确定它们是否相等，或者一个在字典中是否小于另一个。|
|[crbegin](#crbegin)|与[rbegin 相同](#rbegin)。|
|[crend](#crend)|与[rend](#rend)相同。|
|[数据](#data)|返回指向字符序列的原始非拥有指针。|
|[空](#empty)|测试string_view是否包含字符。|
|[结束](#end)|与[cend](#cend)相同。|
|[find](#find)|以正向方向搜索与指定字符序列匹配的子字符串的第一次出现。|
|[find_first_not_of](#find_first_not_of)|搜索不是指定string_view或可转换字符串对象的任何元素的第一个字符。|
|[find_first_of](#find_first_of)|搜索与指定string_view或可转换字符串对象的任何元素匹配的第一个字符。|
|[find_last_not_of](#find_last_not_of)|搜索不是指定string_view或可转换字符串对象的任何元素的最后一个字符。|
|[find_last_of](#find_last_of)|搜索作为指定string_view或可转换字符串对象元素的最后一个字符。|
|[前面](#front)|返回第一个元素的const_reference。|
|[length](#length)|返回当前元素数。|
|[max_size](#max_size)|返回string_view可以包含的最大字符数。|
|[rbegin](#rbegin)|返回一个 const 迭代器，该迭代器处理反转string_view中的第一个元素。|
|[remove_prefix](#remove_prefix)|按指定数量的元素向前移动指针。|
|[remove_suffix](#remove_suffix)|按从背面开始的指定元素数减小视图的大小。|
|[rend](#rend)|返回一个 const 迭代器，该迭代器指向反转string_view中最后一个元素的一个。|
|[rfind](#rfind)|反向搜索string_view，以寻找与指定字符序列匹配的子字符串的第一次出现。|
|[大小](#size)|返回当前元素数。|
|[子](#substr)|返回从指定索引开始的指定长度的子字符串。|
|[交换](#swap)|交换两string_views的内容。|

## <a name="remarks"></a>备注

如果要求函数生成的序列长于 [max_size](#max_size) 元素，这个函数将通过引发 [length_error](../standard-library/length-error-class.md) 类型的对象来报告长度错误。

## <a name="requirements"></a>要求

[std：c++17](../build/reference/std-specify-language-standard-version.md)或更高版本

**标题：string_view>** \<

**命名空间:** std

## <a name="basic_string_viewat"></a><a name="at"></a>basic_string_view：在

在指定的 0 个索引处向字符返回const_reference。

```cpp
constexpr const_reference at(size_type offset) const;
```

### <a name="parameters"></a>参数

*抵消*\
要引用的元素的索引。

### <a name="return-value"></a>返回值

const_reference参数索引指定位置的字符。

### <a name="remarks"></a>备注

第一个元素的索引为零，以下元素由正整数连续索引，因此长度*n* string_view具有由数字*n -* 1 索引的第*n*个元素。 **在**引发无效索引的异常，与[运算符\[](#op_at)不同。

通常，我们建议在序列 **（** 如`std::vector`和 string_view 时，绝不应使用。 传递给序列的无效索引是应在开发过程中发现和修复的逻辑错误。 如果程序不能完全确定其索引是否有效，则应测试它们，而不是调用 at（），并依靠异常来防御粗心的编程。

有关详细信息，请参阅[basic_string_view：：运算符\[](#op_at)。

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

## <a name="basic_string_viewback"></a><a name="back"></a>basic_string_view：返回

返回最后一个元素的const_reference。

```cpp
constexpr const_reference back() const;
```

### <a name="return-value"></a>返回值

const_referencestring_view中的最后一个元素。

### <a name="remarks"></a>备注

如果string_view为空，则引发异常。

请记住，在修改string_view后，例如调用`remove_suffix`，则此函数返回的元素不再是基础数据中的最后一个元素。

### <a name="example"></a>示例

使用 C 字符串文本构造的string_view不包括终止 null，因此在下面的示例中`back`返回"p"而不是"\0"。

```cpp
char c[] = "Help"; // char[5]
string_view sv{ c };
cout << sv.size(); // size() == 4
cout << sv.back() << endl; // p
```

嵌入的 null 被视为任何其他字符：

```cpp
string_view e = "embedded\0nulls"sv;
cout << boolalpha << (e.back() == 's'); // true
```

## <a name="basic_string_viewbasic_string_view"></a><a name="basic_string_view"></a>basic_string_view：basic_string_view

构造string_view。

```cpp
constexpr basic_string_view() noexcept;
constexpr basic_string_view(const basic_string_view&) noexcept = default;
constexpr basic_string_view(const charT* str);
constexpr basic_string_view(const charT* str, size_type len);
```

### <a name="parameters"></a>参数

*Str*\
指向字符值的指针。

*莱恩*\
要包含在视图中的字符数。

## <a name="remarks"></a>备注

具有 charT_ 参数的构造函数假定输入为 null 终止，但终止空不包括在string_view中。

还可以使用文本构造string_view。 请参阅[运算符"sv](string-view-operators.md#op_sv)"。

## <a name="basic_string_viewbegin"></a><a name="begin"></a>basic_string_view：开始

与[cbegin 相同](#cbegin)。

```cpp
constexpr const_iterator begin() const noexcept;
```

### <a name="return-value"></a>返回值

返回寻址第一个元素const_iterator。

## <a name="basic_string_viewcbegin"></a><a name="cbegin"></a>basic_string_view：：cbegin

返回一个const_iterator，该const_iterator处理范围内的第一个元素。

```cpp
constexpr const_iterator cbegin() const noexcept;
```

### <a name="return-value"></a>返回值

指向范围的第一个元素或略高于空范围末尾的位置（对于空范围，）`cbegin() == cend()`的**const**随机访问迭代器。

## <a name="basic_string_viewcend"></a><a name="cend"></a>basic_string_view：：cend

返回一个const_iterator，该const_iterator位于范围中最后一个元素之外的位置。

```cpp
constexpr const_iterator cend() const noexcept;
```

### <a name="return-value"></a>返回值

指向范围末尾的**集中**随机访问迭代器。

### <a name="remarks"></a>备注

不应对 `cend` 返回的值取消引用。

## <a name="basic_string_viewcompare"></a><a name="compare"></a>basic_string_view：比较

与指定的string_view（或可转换字符串类型）执行区分大小写的比较，以确定两个对象是否相等，或者一个对象在字典上是否小于另一个对象。 [ \<string_view>运算符](string-view-operators.md)使用此成员函数执行比较。

```cpp
constexpr int compare(basic_string_view strv) const noexcept;
constexpr int compare(size_type pos, size_type num, basic_string_view strv) const;
constexpr int compare(size_type pos, size_type num, basic_string_view strv, size_type offset, size_type num2) const;
constexpr int compare(const charT* ptr) const;
constexpr int compare(size_type pos, size_type num, const charT* ptr) const;
constexpr int compare(size_type pos, size_type num, const charT* ptr, size_type num2) const;
```

### <a name="parameters"></a>参数

*斯特夫*\
要与这种string_view相比，string_view。

*Pos*\
此string_view开始比较的索引。

*Num*\
要比较的最大字符数string_view。

*num2*\
要比较*的 strv*的最大字符数。

*抵消*\
比较开始的*strv*索引。

*Ptr*\
要与此string_view比较的 C 字符串。

### <a name="return-value"></a>返回值

如果此string_view小于*strv*或*ptr，* 则为负值;如果两个字符序列相等，则为零;或正值，如果此string_view大于*strv*或*ptr*。

### <a name="remarks"></a>备注

成员`compare`函数执行每个字符序列的全部或部分区分大小写的比较。

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

## <a name="basic_string_viewcopy"></a><a name="copy"></a>basic_string_view：复制

从源string_view索引位置到目标字符数组的索引位置最多复制指定数量的字符。 我们建议您改用安全函数[basic_string_view：_Copy_s。](#_copy_s)

```cpp
size_type copy(charT* ptr, size_type count, size_type offset = 0) const;
```

### <a name="parameters"></a>参数

*Ptr*\
要复制的元素的目标字符数组。

*计数*\
最多从源string_view复制的字符数。

*抵消*\
源中的开始位置string_view从中复制。

### <a name="return-value"></a>返回值

实际复制的字符数。

### <a name="remarks"></a>备注

空字符不追加到副本的末尾。

## <a name="basic_string_view_copy_s"></a><a name="_copy_s"></a>basic_string_view：_Copy_s

使用而不是[复制](#copy)的安全 CRT 复制函数。

```cpp
size_type _Copy_s(
    value_type* dest,
    size_type dest_size,
    size_type count,
    size_type _Off = 0) const;
```

### <a name="parameters"></a>参数

*dest*\
要复制的元素的目标字符数组。

*dest_size*\
*dest*的大小。

*• 计算*最多要从源字符串复制的字符数。

*_Off*\
要进行复制的源字符串中的开始位置。

### <a name="return-value"></a>返回值

实际复制的字符数。

### <a name="remarks"></a>备注

空字符不追加到副本的末尾。

有关详细信息，请参阅[c 运行时库/安全功能](../c-runtime-library/security-features-in-the-crt.md)-

## <a name="basic_string_viewcrbegin"></a><a name="crbegin"></a>basic_string_view：克·克贝京

返回一个const_reverse_iterator，该const_reverse_iterator处理反转string_view中的第一个元素。

```cpp
constexpr const_reverse_iterator crbegin() const noexcept;
```

### <a name="return-value"></a>返回值

解决反向string_view中的第一个元素const_reverse_iterator。

## <a name="basic_string_viewcrend"></a><a name="crend"></a>basic_string_view：克伦德

与[rend](#rend)相同。

```cpp
constexpr const_reverse_iterator crend() const noexcept;
```

### <a name="return-value"></a>返回值

返回一个const_reverse_iterator，该const_reverse_iterator处理一个经过反转string_view末尾的一个。

## <a name="basic_string_viewdata"></a><a name="data"></a>basic_string_view：:d阿塔

返回指向用于构造string_view的对象的 const 字符序列的原始非拥有指针。

```cpp
constexpr value_type *data() const noexcept;
```

### <a name="return-value"></a>返回值

指向字符序列的第一个元素的指针到 const。

### <a name="remarks"></a>备注

指针无法修改字符。

string_view字符序列不一定是 null 终止的。 的`data`返回类型不是有效的 C 字符串，因为不会追加任何空字符。 空字符"\0"在类型string_view的对象中没有特殊含义，并且可能像任何其他字符一样是string_view对象的一部分。

## <a name="basic_string_viewempty"></a><a name="empty"></a>basic_string_view：：空

测试string_view是否包含字符。

```cpp
constexpr bool empty() const noexcept;
```

### <a name="return-value"></a>返回值

如果string_view对象不包含字符，**则为 true;** 如果对象不包含字符。"string_view"对象为 true。**假**，如果它至少有一个字符。

### <a name="remarks"></a>备注

成员函数等效于[大小](#size)（） = 0。

## <a name="basic_string_viewend"></a><a name="end"></a>basic_string_view：结束

返回指向最后一个元素的随机访问const_iterator。

```cpp
constexpr const_iterator end() const noexcept;
```

### <a name="return-value"></a>返回值

返回指向最后一个元素的随机访问const_iterator。

### <a name="remarks"></a>备注

`end`用于测试const_iterator是否已达到其string_view的末尾。 不应对 `end` 返回的值取消引用。

## <a name="basic_string_viewfind"></a><a name="find"></a>basic_string_view：查找

在前进方向搜索string_view，寻找与指定字符序列匹配的字符或子字符串的第一次出现。

```cpp
constexpr size_type find(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find(const charT* ptr, size_type offset = 0) const;
```

### <a name="parameters"></a>参数

*Str*\
成员函数要搜索的string_view。

*chVal*\
成员函数要搜索的字符值。

*抵消*\
开始搜索的索引。

*Ptr*\
成员函数要为其搜索的 C 字符串。

*计数*\
*ptr*中的字符数，从第一个字符向前计数。

### <a name="return-value"></a>返回值

搜索成功时，则为搜索的子字符串的首个字符的索引；否则为 `npos`。

## <a name="basic_string_viewfind_first_not_of"></a><a name="find_first_not_of"></a>basic_string_view：find_first_not_of

搜索不是指定string_view或可转换字符串对象元素的第一个字符。

```cpp
constexpr size_type find_first_not_of(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find_first_not_of(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find_first_not_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_first_not_of(const charT* ptr, size_type offset = 0) const;
```

### <a name="parameters"></a>参数

*Str*\
成员函数要搜索的string_view。

*chVal*\
成员函数要搜索的字符值。

*抵消*\
开始搜索的索引。

*Ptr*\
成员函数要为其搜索的 C 字符串。

*计数*\
成员函数要搜索的 C 字符串中从第一个字符向前计数的字符数。

### <a name="return-value"></a>返回值

搜索成功时，则为搜索的子字符串的首个字符的索引；否则为 `npos`。

## <a name="basic_string_viewfind_first_of"></a><a name="find_first_of"></a>basic_string_view：find_first_of

搜索与指定string_view的任何元素匹配的第一个字符。

```cpp
constexpr size_type find_first_of(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find_first_of(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find_first_of(const charT* str, size_type offset, size_type count) const;
constexpr size_type find_first_of(const charT* str, size_type offset = 0) const;
```

### <a name="parameters"></a>参数

*chVal*\
成员函数要搜索的字符值。

*抵消*\
开始搜索的索引。

*Ptr*\
成员函数要为其搜索的 C 字符串。

*计数*\
成员函数要搜索的 C 字符串中从第一个字符向前计数的字符数。

*Str*\
成员函数要搜索的string_view。

### <a name="return-value"></a>返回值

搜索成功时，则为搜索的子字符串的首个字符的索引；否则为 `npos`。

## <a name="basic_string_viewfind_last_not_of"></a><a name="find_last_not_of"></a>basic_string_view：find_last_not_of

搜索不是指定string_view的任何元素的最后一个字符。

```cpp
constexpr size_type find_last_not_of(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type find_last_not_of(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type find_last_not_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_last_not_of(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>参数

*Str*\
成员函数要搜索的string_view。

*chVal*\
成员函数要搜索的字符值。

*抵消*\
要完成搜索的索引。

*Ptr*\
成员函数要为其搜索的 C 字符串。

*计数*\
从第一个字符向前计数的字符数，以*ptr*中计算。

### <a name="return-value"></a>返回值

搜索成功时，则为搜索的子字符串的首个字符的索引；否则为 `string_view::npos`。

## <a name="basic_string_viewfind_last_of"></a><a name="find_last_of"></a>basic_string_view：：find_last_of

搜索与指定string_view的任何元素匹配的最后一个字符。

```cpp
constexpr size_type find_last_of(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type find_last_of(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type find_last_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_last_of(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>参数

*Str*\
成员函数要搜索的string_view。

*chVal*\
成员函数要搜索的字符值。

*抵消*\
要完成搜索的索引。

*Ptr*\
成员函数要为其搜索的 C 字符串。

*计数*\
成员函数要搜索的 C 字符串中从第一个字符向前计数的字符数。

### <a name="return-value"></a>返回值

搜索成功时，则为搜索的子字符串的最后一个字符的索引；否则为 `npos`。

## <a name="basic_string_viewfront"></a><a name="front"></a>basic_string_view：前

返回第一个元素的const_reference。

```cpp
constexpr const_reference front() const;
```

### <a name="return-value"></a>返回值

对第一个元素const_reference。

### <a name="remarks"></a>备注

如果string_view为空，则引发异常。

## <a name="basic_string_viewlength"></a><a name="length"></a>basic_string_view：长度

返回当前元素数。

```cpp
constexpr size_type length() const noexcept;
```

### <a name="remarks"></a>备注

成员函数与 [size](#size) 相同。

## <a name="basic_string_viewmax_size"></a><a name="max_size"></a>basic_string_view：：max_size

返回string_view可以包含的最大字符数。

```cpp
constexpr size_type max_size() const noexcept;
```

### <a name="return-value"></a>返回值

string_view可以包含的最大字符数。

### <a name="remarks"></a>备注

当操作生成长度[length_error](../standard-library/length-error-class.md)大于`max_size()`string_view 时，将引发类型length_error的异常。

## <a name="basic_string_viewoperator"></a><a name="op_eq"></a>basic_string_view：：操作员*

将string_view或可转换字符串对象分配给另一个string_view。

```cpp
constexpr basic_string_view& operator=(const basic_string_view&) noexcept = default;
```

### <a name="example"></a>示例

```cpp
   string_view s = "Hello";
   string_view s2 = s;
```

## <a name="basic_string_viewoperator"></a><a name="op_at"></a>basic_string_view：运算符*

提供具有指定索引的字符const_reference。

```cpp
constexpr const_reference operator[](size_type offset) const;
```

### <a name="parameters"></a>参数

*抵消*\
要引用的元素的索引。

### <a name="return-value"></a>返回值

const_reference参数索引指定位置的字符。

### <a name="remarks"></a>备注

第一个元素的索引为零，以下元素由正整数连续索引，因此长度*n* string_view具有由数字*n* - 1 索引的第*n*个元素。

`operator[]`提供对string_view元素的读取访问时，比[成员函数快](#at)。

`operator[]`不检查作为参数传递的索引是否有效。 传递给的无效索引`operator[]`会导致未定义的行为。

如果所属对象修改或删除基础字符串数据，则返回的引用可能会失效。

使用[\_\_\_](../standard-library/iterator-debug-level.md)设置为 1 或 2 的 ITERATOR DEBUG LEVEL 编译时，如果尝试访问string_view边界之外的元素，则会出现运行时错误。 有关更多信息，请参见 [Checked Iterators](../standard-library/checked-iterators.md)。

## <a name="basic_string_viewrbegin"></a><a name="rbegin"></a>basic_string_view：rbegin

将 const 迭代器返回到反转string_view中的第一个元素。

```cpp
constexpr const_reverse_iterator rbegin() const noexcept;
```

### <a name="return-value"></a>返回值

将随机访问迭代器返回到反向string_view中的第一个元素，寻址相应未反转string_view中的最后一个元素。

### <a name="remarks"></a>备注

`rbegin`与反向string_view一起使用，就像[与](#begin)string_view一起使用一样。 `rbegin`可用于向后初始化迭代。

## <a name="basic_string_viewremove_prefix"></a><a name="remove_prefix"></a>basic_string_view：remove_prefix

按指定数量的元素向前移动指针。

```cpp
constexpr void remove_prefix(size_type n);
```

### <a name="remarks"></a>备注

保持不变基础数据。 按 n 元素向前移动string_view指针，并将私有`size`数据成员设置为大小 - n。

## <a name="basic_string_viewremove_suffix"></a><a name="remove_suffix"></a>basic_string_view：remove_suffix

按从背面开始的指定元素数减小视图的大小。

```cpp
constexpr void remove_suffix(size_type n);
```

### <a name="remarks"></a>备注

使基础数据和指向它的指针保持不变。 将私有`size`数据成员设置为大小 - n。

## <a name="basic_string_viewrend"></a><a name="rend"></a>basic_string_view：rend

返回一个 const 迭代器，该迭代器指向反转string_view中最后一个元素的一个。

```cpp
constexpr reverse_iterator rend() const noexcept;
```

### <a name="return-value"></a>返回值

一个反向随机访问迭代器，指向反转string_view中最后一个元素的一个。

### <a name="remarks"></a>备注

`rend`与反向string_view一起使用，就像[端](#end)与string_view一起使用一样。 `rend`可用于测试反向迭代器是否已到达其string_view的末尾。 不应对 `rend` 返回的值取消引用。

## <a name="basic_string_viewrfind"></a><a name="rfind"></a>basic_string_view：如发现

反向搜索string_view，搜索与指定字符序列匹配的子字符串。

```cpp
constexpr size_type rfind(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type rfind(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type rfind(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type rfind(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>参数

*chVal*\
成员函数要搜索的字符值。

*抵消*\
开始搜索的索引。

*Ptr*\
成员函数要为其搜索的 C 字符串。

*计数*\
成员函数要搜索的 C 字符串中从第一个字符向前计数的字符数。

*Str*\
成员函数要搜索的string_view。

### <a name="return-value"></a>返回值

子字符串成功时的第一个字符的索引;否则`npos`。

## <a name="basic_string_viewsize"></a><a name="size"></a>basic_string_view：大小

返回string_view中的元素数。

```cpp
constexpr size_type size() const noexcept;
```

### <a name="return-value"></a>返回值

string_view的长度。

### <a name="remarks"></a>备注

string_view可以修改其长度，例如 ， `remove_prefix` `remove_suffix` 由于这不能修改基础字符串数据，因此string_view的大小不一定是基础数据的大小。

## <a name="basic_string_viewsubstr"></a><a name="substr"></a>basic_string_view：：子

返回表示（最多）指定位置的指定字符数string_view。

```cpp
constexpr basic_string_view substr(size_type offset = 0, size_type count = npos) const;
```

### <a name="parameters"></a>参数

*抵消*\
在创建副本的位置定位元素的索引，默认值为 0。

*计数*\
要包含在子字符串中的字符数（如果存在）。

### <a name="return-value"></a>返回值

表示元素的指定子序列string_view对象。

## <a name="basic_string_viewswap"></a><a name="swap"></a>basic_string_view：：交换

交换两string_views，换言之，指向基础字符串数据的指针和大小值。

```cpp
constexpr void swap(basic_string_view& sv) noexcept;
```

### <a name="parameters"></a>参数

*Sv*\
源string_view其指针和大小值要与目标string_view的值交换。

## <a name="see-also"></a>另请参阅

[\<string_view>](../standard-library/string-view.md)\
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)

---
title: '&lt;string&gt; 函数'
ms.date: 11/04/2016
f1_keywords:
- string/std::getline
- string/std::stod
- string/std::stof
- string/std::stoi
- string/std::stol
- string/std::stold
- string/std::stoll
- string/std::stoul
- string/std::stoull
- string/std::swap
- string/std::to_string
- string/std::to_wstring
ms.assetid: 1a4ffd11-dce5-4cc6-a043-b95de034c7c4
helpviewer_keywords:
- std::getline [C++]
- std::stod [C++]
- std::stof [C++]
- std::stoi [C++]
- std::stol [C++]
- std::stold [C++]
- std::stoll [C++]
- std::stoul [C++]
- std::stoull [C++]
- std::swap [C++]
- std::to_string [C++]
- std::to_wstring [C++]
ms.openlocfilehash: 3f1dca71a6bb9d5461150378191b9373f907ecd1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376662"
---
# <a name="ltstringgt-functions"></a>&lt;string&gt; 函数

||||
|-|-|-|
|[getline](#getline)|[斯托德](#stod)|[stof](#stof)|
|[斯托伊](#stoi)|[stol](#stol)|[stold](#stold)|
|[stoll](#stoll)|[stoul](#stoul)|[斯图尔](#stoull)|
|[交换](#swap)|[to_string](#to_string)|[to_wstring](#to_wstring)|

## <a name="getline"></a><a name="getline"></a>getline

将字符串从输入流中一行一行地提取出来。

```cpp
// (1) delimiter as parameter
template <class CharType, class Traits, class Allocator>
basic_istream<CharType, Traits>& getline(
    basic_istream<CharType, Traits>& in_stream,
    basic_string<CharType, Traits, Allocator>& str,
    CharType delimiter);

template <class CharType, class Traits, class Allocator>
basic_istream<CharType, Traits>& getline(
    basic_istream<CharType, Traits>&& in_stream,
    basic_string<CharType, Traits, Allocator>& str,
    const CharType delimiter);

// (2) default delimiter used
template <class CharType, class Traits, class Allocator>
basic_istream<CharType, Traits>& getline(
    basic_istream<CharType, Traits>& in_stream,
    basic_string<CharType, Traits, Allocator>& str);

template <class Allocator, class Traits, class Allocator>
basic_istream<Allocator, Traits>& getline(
    basic_istream<Allocator, Traits>&& in_stream,
    basic_string<Allocator, Traits, Allocator>& str);
```

### <a name="parameters"></a>参数

*in_stream*\
要从其中提取字符串的输入流。

*Str*\
从输入流读取的字符将放入的字符串。

*分隔符*\
行分隔符。

### <a name="return-value"></a>返回值

输入流*in_stream*。

### <a name="remarks"></a>备注

标记`(1)`从*in_stream*中提取字符的函数签名对，直到找到*分隔符*，将它们存储在*str*中。

标记`(2)`的函数签名对使用 newline 作为默认行分隔符，并且行为为`getline(in_stream, str, in_stream. widen('\n'))`。

每对函数中的第二个函数是第一个的模拟，它的作用是支持 [rvalue 引用](../cpp/lvalues-and-rvalues-visual-cpp.md)。

发生下列情况之一时，提取将停止：

- 在文件末尾，在这种情况下 *，in_stream*的内部状态标志设置为`ios_base::eofbit`。

- 函数提取一个与*分隔符*相等的元素。 元素不会放回或追加到受控序列中。

- 函数提取`str.`[max_size](../standard-library/basic-string-class.md#max_size)元素后。 *in_stream*的内部状态标志设置为`ios_base::failbit`。

- 除了之前列出的错误之外，其他一些错误;*in_stream*的内部状态标志设置为`ios_base::badbit`。

有关内部状态标志的信息，请参阅 [ios_base::iostate](../standard-library/ios-base-class.md#iostate)。

如果函数不提取任何元素，则*in_stream*的内部状态标志设置为`ios_base::failbit`。 在任何情况下，`getline`返回*in_stream*。

如果引发异常，*则in_stream*和*str*处于有效状态。

### <a name="example"></a>示例

以下代码演示两种模式下的 `getline()`：第一种使用默认分隔符（换行），第二种使用空格作为分隔符。 文件尾字符（键盘上的 CTRL-Z）用于控制 while 循环的终止。 此值设置 到`cin``eofbit`的内部状态标志，在第二个循环正常工作之前，必须用[basic_ios：：clear（）](../standard-library/basic-ios-class.md#clear)清除该标志。

```cpp
// compile with: /EHsc /W4
#include <string>
#include <iostream>
#include <vector>

using namespace std;

int main()
{
    string str;
    vector<string> v1;
    cout << "Enter a sentence, press ENTER between sentences. (Ctrl-Z to stop): " << endl;
    // Loop until end-of-file (Ctrl-Z) is input, store each sentence in a vector.
    // Default delimiter is the newline character.
    while (getline(cin, str)) {
        v1.push_back(str);
    }

    cout << "The following input was stored with newline delimiter:" << endl;
    for (const auto& p : v1) {
        cout << p << endl;
    }

    cin.clear();

    vector<string> v2;
    // Now try it with a whitespace delimiter
    while (getline(cin, str, ' ')) {
        v2.push_back(str);
    }

    cout << "The following input was stored with whitespace as delimiter:" << endl;
    for (const auto& p : v2) {
        cout << p << endl;
    }
}
```

## <a name="stod"></a><a name="stod"></a>斯托德

将字符序列转换为 。 **`double`**

```cpp
double stod(
    const string& str,
    size_t* idx = 0);

double stod(
    const wstring& str,
    size_t* idx = 0
;
```

### <a name="parameters"></a>参数

*Str*\
要转换的字符序列。

*idx*\
首个未转换字符的索引值。

### <a name="return-value"></a>返回值

值**`double`**。

### <a name="remarks"></a>备注

函数将*str*中的元素序列转换为类型**`double`** 值，就像通过调用`strtod( str.c_str(), _Eptr)`，其中`_Eptr`是函数内部的对象。 如果`str.c_str() == *_Eptr`，它将引发类型的对象`invalid_argument`。 如果此类调用将设置 `errno`，它将引发 `out_of_range` 类型的对象。 否则，如果*idx*不是空指针，则函数将存储`*_Eptr -  str.c_str()`并`*idx`返回该值。

## <a name="stof"></a><a name="stof"></a>斯特下

将字符序列转换为浮动的。

```cpp
float stof(
    const string& str,
    size_t* idx = 0);

float stof(
    const wstring& str,
    size_t* idx = 0);
```

### <a name="parameters"></a>参数

*Str*\
要转换的字符序列。

*idx*\
首个未转换字符的索引值。

### <a name="return-value"></a>返回值

值**`float`**。

### <a name="remarks"></a>备注

函数将*str*中的元素序列转换为类型**`float`** 值，就像通过调用`strtof( str.c_str(), _Eptr)`，其中`_Eptr`是函数内部的对象。 如果`str.c_str() == *_Eptr`，它将引发类型的对象`invalid_argument`。 如果此类调用将设置 `errno`，它将引发 `out_of_range` 类型的对象。 否则，如果*idx*不是空指针，则函数将存储`*_Eptr -  str.c_str()`并`*idx`返回该值。

## <a name="stoi"></a><a name="stoi"></a>斯托伊

将字符序列转换为整数。

```cpp
int stoi(
    const string& str,
    size_t* idx = 0,
    int base = 10);

int stoi(
    const wstring& str,
    size_t* idx = 0,
    int base = 10);
```

### <a name="return-value"></a>返回值

整数值。

### <a name="parameters"></a>参数

*Str*\
要转换的字符序列。

*idx*\
首个未转换字符的索引值。

*基地*\
要使用的号码基。

### <a name="remarks"></a>备注

函数`stoi`将*str*中的字符序列转换为类型的**`int`** 值并返回该值。 例如，在传递字符序列“10”时，`stoi` 返回的值为整数 10.

`stoi`当以单字节字符的方式调用`strtol`时`strtol( str.c_str(), _Eptr, idx)`，其行为类似于该函数，其中`_Eptr`是函数内部的对象;或`wcstol`对于宽字符，当它以类似的方式调用时， `wcstol(Str.c_str(), _Eptr, idx)`。 有关详细信息，请参阅 [strtol、wcstol、_strtol_l、_wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)。

如果`str.c_str() == *_Eptr``stoi`引发类型`invalid_argument`的对象 。 如果这样的调用将设置`errno`，或者如果返回的值不能表示为类型**`int`** 的对象，则它将引发类型`out_of_range`的对象。 否则，如果*idx*不是空指针，则函数将存储在`*_Eptr - str.c_str()``*idx`中。

## <a name="stol"></a><a name="stol"></a>斯托尔

将字符序列转换为 。 **`long`**

```cpp
long stol(
    const string& str,
    size_t* idx = 0,
    int base = 10);

long stol(
    const wstring& str,
    size_t* idx = 0,
    int base = 10);
```

### <a name="parameters"></a>参数

*Str*\
要转换的字符序列。

*idx*\
首个未转换字符的索引值。

*基地*\
要使用的号码基。

### <a name="return-value"></a>返回值

长整数的值。

### <a name="remarks"></a>备注

函数将*str*中的元素序列转换为类型**`long`** 值，就像通过调用`strtol( str.c_str(), _Eptr, idx)`，其中`_Eptr`是函数内部的对象。 如果`str.c_str() == *_Eptr`，它将引发类型的对象`invalid_argument`。 如果此类调用将设置 `errno`，它将引发 `out_of_range` 类型的对象。 否则，如果*idx*不是空指针，则函数将存储`*_Eptr -  str.c_str()`并`*idx`返回该值。

## <a name="stold"></a><a name="stold"></a>斯代

将字符序列转换为 。 **`long double`**

```cpp
double stold(
    const string& str,
    size_t* idx = 0);

double stold(
    const wstring& str,
    size_t* idx = 0);
```

### <a name="parameters"></a>参数

*Str*\
要转换的字符序列。

*idx*\
首个未转换字符的索引值。

### <a name="return-value"></a>返回值

值**`long double`**。

### <a name="remarks"></a>备注

函数将*str*中的元素序列转换为类型**`long double`** 值，就像通过调用`strtold( str.c_str(), _Eptr)`，其中`_Eptr`是函数内部的对象。 如果`str.c_str() == *_Eptr`，它将引发类型的对象`invalid_argument`。 如果此类调用将设置 `errno`，它将引发 `out_of_range` 类型的对象。 否则，如果*idx*不是空指针，则函数将存储`*_Eptr -  str.c_str()`并`*idx`返回该值。

## <a name="stoll"></a><a name="stoll"></a>斯托尔

将字符序列转换为 。 **`long long`**

```cpp
long long stoll(
    const string& str,
    size_t* idx = 0,
    int base = 10);

long long stoll(
    const wstring& str,
    size_t* idx = 0,
    int base = 10);
```

### <a name="parameters"></a>参数

*Str*\
要转换的字符序列。

*idx*\
首个未转换字符的索引值。

*基地*\
要使用的号码基。

### <a name="return-value"></a>返回值

值**`long long`**。

### <a name="remarks"></a>备注

函数将*str*中的元素序列转换为类型**`long long`** 值，就像通过调用`strtoll( str.c_str(), _Eptr, idx)`，其中`_Eptr`是函数内部的对象。 如果`str.c_str() == *_Eptr`，它将引发类型的对象`invalid_argument`。 如果此类调用将设置 `errno`，它将引发 `out_of_range` 类型的对象。 否则，如果*idx*不是空指针，则函数将存储`*_Eptr -  str.c_str()`并`*idx`返回该值。

## <a name="stoul"></a><a name="stoul"></a>斯图尔

将字符序列转换为无符号长整数。

```cpp
unsigned long stoul(
    const string& str,
    size_t* idx = 0,
    int base = 10);

unsigned long stoul(
    const wstring& str,
    size_t* idx = 0,
    int base = 10);
```

### <a name="parameters"></a>参数

*Str*\
要转换的字符序列。

*idx*\
首个未转换字符的索引值。

*基地*\
要使用的号码基。

### <a name="return-value"></a>返回值

无符号长整数的值。

### <a name="remarks"></a>备注

函数将*str*中的元素序列转换为类型**`unsigned long`** 值，就像通过调用`strtoul( str.c_str(), _Eptr, idx)`，其中`_Eptr`是函数内部的对象。 如果`str.c_str() == *_Eptr`，它将引发类型的对象`invalid_argument`。 如果此类调用将设置 `errno`，它将引发 `out_of_range` 类型的对象。 否则，如果*idx*不是空指针，则函数将存储`*_Eptr -  str.c_str()`并`*idx`返回该值。

## <a name="stoull"></a><a name="stoull"></a>斯图尔

将字符序列转换为**`unsigned long long`**。

```cpp
unsigned long long stoull(
    const string& str,
    size_t* idx = 0,
    int base = 10);

unsigned long long stoull(
    const wstring& str,
    size_t* idx = 0,
    int base = 10);
```

### <a name="parameters"></a>参数

*Str*\
要转换的字符序列。

*idx*\
首个未转换字符的索引值。

*基地*\
要使用的号码基。

### <a name="return-value"></a>返回值

值**`unsigned long long`**。

### <a name="remarks"></a>备注

函数将*str*中的元素序列转换为类型**`unsigned long long`** 值，就像通过调用`strtoull( str.c_str(), _Eptr, idx)`，其中`_Eptr`是函数内部的对象。 如果`str.c_str() == *_Eptr`，它将引发类型的对象`invalid_argument`。 如果此类调用将设置 `errno`，它将引发 `out_of_range` 类型的对象。 否则，如果*idx*不是空指针，则函数将存储`*_Eptr -  str.c_str()`并`*idx`返回该值。

## <a name="swap"></a><a name="swap"></a>交换

交换两个字符串的字符数组。

```cpp
template <class Traits, class Allocator>
void swap(basic_string<CharType, Traits, Allocator>& left, basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>参数

*离开*\
其元素要与另一个字符串的元素交换的字符串。

*对*\
要与第一个字符串交换元素的另一个字符串。

### <a name="remarks"></a>备注

模板函数执行*左侧*的专用成员函数。[交换](../standard-library/basic-string-class.md#swap)字符串 （*右*）， 保证恒定的复杂性.

### <a name="example"></a>示例

```cpp
// string_swap.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   // Declaring an object of type basic_string<char>
   string s1 ( "Tweedledee" );
   string s2 ( "Tweedledum" );
   cout << "Before swapping string s1 and s2:" << endl;
   cout << "The basic_string s1 = " << s1 << "." << endl;
   cout << "The basic_string s2 = " << s2 << "." << endl;

   swap ( s1 , s2 );
   cout << "\nAfter swapping string s1 and s2:" << endl;
   cout << "The basic_string s1 = " << s1 << "." << endl;
   cout << "The basic_string s2 = " << s2 << "." << endl;
}
```

```Output
Before swapping string s1 and s2:
The basic_string s1 = Tweedledee.
The basic_string s2 = Tweedledum.

After swapping string s1 and s2:
The basic_string s1 = Tweedledum.
The basic_string s2 = Tweedledee.
```

## <a name="to_string"></a><a name="to_string"></a>to_string

将一个值转换为 `string`。

```cpp
string to_string(int value);
string to_string(unsigned int value);
string to_string(long value);
string to_string(unsigned long value);
string to_string(long long value);
string to_string(unsigned long long value);
string to_string(float value);
string to_string(double value);
string to_string(long double value);
```

### <a name="parameters"></a>参数

*价值*\
要转换的值。

### <a name="return-value"></a>返回值

表示该值的 `string`。

### <a name="remarks"></a>备注

函数将*值*转换为存储在函数内部数组对象`Buf`中的元素序列，就像通过调用`sprintf(Buf, Fmt, value)``Fmt`

- `"%d"`如果*值*为类型**`int`**

- `"%u"`如果*值*为类型**`unsigned int`**

- `"%ld"`如果*值*为类型**`long`**

- `"%lu"`如果*值*为类型**`unsigned long`**

- `"%lld"`如果*值*为类型**`long long`**

- `"%llu"`如果*值*为类型**`unsigned long long`**

- `"%f"`如果*值*为类型**`float`** 或**`double`**

- `"%Lf"`如果*值*为类型**`long double`**

该函数返回 `string(Buf)`。

## <a name="to_wstring"></a><a name="to_wstring"></a>to_wstring

将一个值转换为宽字符串。

```cpp
wstring to_wstring(int value);
wstring to_wstring(unsigned int value);
wstring to_wstring(long value);
wstring to_wstring(unsigned long value);
wstring to_wstring(long long value);
wstring to_wstring(unsigned long long value);
wstring to_wstring(float value);
wstring to_wstring(double value);
wstring to_wstring(long double value);
```

### <a name="parameters"></a>参数

*价值*\
要转换的值。

### <a name="return-value"></a>返回值

表示该值的宽字符串。

### <a name="remarks"></a>备注

函数将*值*转换为存储在函数内部数组对象`Buf`中的元素序列，就像通过调用`swprintf(Buf, Len, Fmt, value)``Fmt`

- `L"%d"`如果*值*为类型**`int`**

- `L"%u"`如果*值*为类型**`unsigned int`**

- `L"%ld"`如果*值*为类型**`long`**

- `L"%lu"`如果*值*为类型**`unsigned long`**

- `L"%lld"`如果*值*为类型**`long long`**

- `L"%llu"`如果*值*为类型**`unsigned long long`**

- `L"%f"`如果*值*为类型**`float`** 或**`double`**

- `L"%Lf"`如果*值*为类型**`long double`**

该函数返回 `wstring(Buf)`。

## <a name="see-also"></a>另请参阅

[\<字符串>](../standard-library/string.md)

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
ms.openlocfilehash: d10af9bc32acd730db1fe9da3775ac2aa84e5fff
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412340"
---
# <a name="ltstringgt-functions"></a>&lt;string&gt; 函数

||||
|-|-|-|
|[getline](#getline)|[stod](#stod)|[stof](#stof)|
|[stoi](#stoi)|[stol](#stol)|[stold](#stold)|
|[stoll](#stoll)|[stoul](#stoul)|[stoull](#stoull)|
|[swap](#swap)|[to_string](#to_string)|[to_wstring](#to_wstring)|

## <a name="getline"></a>  getline

将字符串从输入流中一行一行地提取出来。

```cpp
// (1) delimiter as parameter
template <class CharType, class Traits, class Allocator>
basic_istream<CharType, Traits>& getline(
    basic_istream<CharType, Traits>& is,
    basic_string<CharType, Traits, Allocator>& str,
    CharType delim);

template <class CharType, class Traits, class Allocator>
basic_istream<CharType, Traits>& getline(
    basic_istream<CharType, Traits>&& is,
    basic_string<CharType, Traits, Allocator>& str,
    const CharType delim);

// (2) default delimiter used
template <class CharType, class Traits, class Allocator>
basic_istream<CharType, Traits>& getline(
    basic_istream<CharType, Traits>& is,
    basic_string<CharType, Traits, Allocator>& str);

template <class Allocator, class Traits, class Allocator>
basic_istream<Allocator, Traits>& getline(
    basic_istream<Allocator, Traits>&& is,
    basic_string<Allocator, Traits, Allocator>& str);
```

### <a name="parameters"></a>参数

*is*<br/>
要从其中提取字符串的输入流。

*str*<br/>
从输入流读取的字符将放入的字符串。

*delim*<br/>
行分隔符。

### <a name="return-value"></a>返回值

输入的流*是*。

### <a name="remarks"></a>备注

函数签名对标记为`(1)`从中提取字符*是*直到*delim*找到，则将它们存储在*str*。

函数签名对标记为`(2)`使用换行符作为默认行分隔符，并且像**getline**(`is`， `str`， `is`。 `widen`(' `\n`')).

每对函数中的第二个函数是第一个的模拟，它的作用是支持 [rvalue 引用](../cpp/lvalues-and-rvalues-visual-cpp.md)。

发生下列情况之一时，提取将停止：

- 文件末尾的内部状态标志，在这种情况下*是*设置为`ios_base::eofbit`。

- 函数提取经比较与 `delim` 相等的元素后，既不放回该元素，也不将它追加到受控序列的情况。

- 函数提取`str.` [max_size](../standard-library/basic-string-class.md#max_size)元素，在这种情况下的内部状态标志*是*设置为`ios_base::failbit`。

- 以外的其他一些错误前面列出，在这种情况下的内部状态标志的*是*设置为 `ios_base::badbit`

有关内部状态标志的信息，请参阅 [ios_base::iostate](../standard-library/ios-base-class.md#iostate)。

如果函数没有提取任何元素，内部状态标志*是*设置为`ios_base::failbit`。 在任何情况下，`getline`将返回*是*。

如果引发异常，*是*并*str*处于有效状态。

### <a name="example"></a>示例

以下代码演示两种模式下的 `getline()`：第一种使用默认分隔符（换行），第二种使用空格作为分隔符。 文件尾字符（键盘上的 CTRL-Z）用于控制 while 循环的终止。 这会将 `cin` 的内部状态标志设置为 `eofbit`，后者必须使用 [basic_ios::clear()](../standard-library/basic-ios-class.md#clear) 进行消除，这样第二个 while 循环才能正确运行。

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

## <a name="stod"></a>  stod

将转换为字符序列**double**。

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

|参数|描述|
|---------------|-----------------|
|*str*|要转换的字符序列。|
|*idx*|首个未转换字符的索引值。|

### <a name="return-value"></a>返回值

**Double**值。

### <a name="remarks"></a>备注

该函数中的元素的序列转换*str*为值`val`类型的**double**通过调用`strtod( str.c_str(), _Eptr)`，其中`_Eptr`是函数的内部对象。 如果 ` str.c_str() == *_Eptr`，它将引发 `invalid_argument` 类型的对象。 如果此类调用将设置 `errno`，它将引发 `out_of_range` 类型的对象。 否则为如果*idx*不是 null 指针，函数存储`*_Eptr -  str.c_str()`中`*idx`，并返回`val`。

## <a name="stof"></a>  stof

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

|参数|描述|
|---------------|-----------------|
|*str*|要转换的字符序列。|
|*idx*|首个未转换字符的索引值。|

### <a name="return-value"></a>返回值

浮动值。

### <a name="remarks"></a>备注

该函数中的元素的序列转换*str*为值`val`类型的**float**通过调用`strtof( str.c_str(), _Eptr)`，其中`_Eptr`是函数的内部对象。 如果 ` str.c_str() == *_Eptr`，它将引发 `invalid_argument` 类型的对象。 如果此类调用将设置 `errno`，它将引发 `out_of_range` 类型的对象。 否则为如果*idx*不是 null 指针，函数存储`*_Eptr -  str.c_str()`中`*idx`，并返回`val`。

## <a name="stoi"></a>  stoi

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

|参数|描述|
|---------------|-----------------|
|*str*|要转换的字符序列。|
|*idx*|返回时包含首个未转换字符的索引。|
|*base*|要使用的号码基。|

### <a name="remarks"></a>备注

该函数`stoi`中的字符序列转换*str*类型的值为**int**和返回值。 例如，在传递字符序列“10”时，`stoi` 返回的值为整数 10.

当以 `stoi` 方式调用时，`strtol` 的行为方式与针对单字节字符的 `strtol( str.c_str(), _Eptr, idx)` 函数相似，其中，`_Eptr` 是函数的内部对象；而当以类似的方式 `wcstol` 调用时，其行为与针对宽字符的 `wcstol(Str.c_str(), _Eptr, idx)` 相似。 有关详细信息，请参阅 [strtol、wcstol、_strtol_l、_wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)。

如果`str.c_str() == *_Eptr`，`stoi`将引发类型的对象`invalid_argument`。 如果此类调用将设置`errno`，或如果返回的值不能表示为类型的对象**int**，则会引发类型的对象`out_of_range`。 否则为如果*idx*不是 null 指针，函数存储`*_Eptr - str.c_str()`中`*idx`。

## <a name="stol"></a>  stol

将转换为字符序列**长**。

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

|参数|描述|
|---------------|-----------------|
|*str*|要转换的字符序列。|
|*idx*|首个未转换字符的索引值。|
|*base*|要使用的号码基。|

### <a name="return-value"></a>返回值

长整数的值。

### <a name="remarks"></a>备注

该函数中的元素的序列转换*str*为值`val`类型的**长**通过调用`strtol( str.c_str(), _Eptr, idx)`，其中`_Eptr`是函数的内部对象。 如果 ` str.c_str() == *_Eptr`，它将引发 `invalid_argument` 类型的对象。 如果此类调用将设置 `errno`，它将引发 `out_of_range` 类型的对象。 否则为如果*idx*不是 null 指针，函数存储`*_Eptr -  str.c_str()`中`*idx`，并返回`val`。

## <a name="stold"></a>  stold

将转换为字符序列**长双精度型**。

```cpp
double stold(
    const string& str,
    size_t* idx = 0);

double stold(
    const wstring& str,
    size_t* idx = 0);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*str*|要转换的字符序列。|
|*idx*|首个未转换字符的索引值。|

### <a name="return-value"></a>返回值

**长双精度型**值。

### <a name="remarks"></a>备注

该函数中的元素的序列转换*str*为值`val`类型的**长双精度型**通过调用`strtold( str.c_str(), _Eptr)`，其中`_Eptr`是函数的内部对象。 如果 ` str.c_str() == *_Eptr`，它将引发 `invalid_argument` 类型的对象。 如果此类调用将设置 `errno`，它将引发 `out_of_range` 类型的对象。 否则为如果*idx*不是 null 指针，函数存储`*_Eptr -  str.c_str()`中`*idx`，并返回`val`。

## <a name="stoll"></a>  stoll

将转换为字符序列**超长**。

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

|参数|描述|
|---------------|-----------------|
|*str*|要转换的字符序列。|
|*idx*|首个未转换字符的索引值。|
|*base*|要使用的号码基。|

### <a name="return-value"></a>返回值

**超长**值。

### <a name="remarks"></a>备注

该函数中的元素的序列转换*str*为值`val`类型的**超长**通过调用`strtoll( str.c_str(), _Eptr, idx)`，其中`_Eptr`是函数的内部对象。 如果 ` str.c_str() == *_Eptr`，它将引发 `invalid_argument` 类型的对象。 如果此类调用将设置 `errno`，它将引发 `out_of_range` 类型的对象。 否则为如果*idx*不是 null 指针，函数存储`*_Eptr -  str.c_str()`中`*idx`，并返回`val`。

## <a name="stoul"></a>  stoul

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

|参数|描述|
|---------------|-----------------|
|*str*|要转换的字符序列。|
|*idx*|首个未转换字符的索引值。|
|*base*|要使用的号码基。|

### <a name="return-value"></a>返回值

无符号长整数的值。

### <a name="remarks"></a>备注

该函数中的元素的序列转换*str*为值`val`类型的**无符号长**通过调用`strtoul( str.c_str(), _Eptr, idx)`，其中`_Eptr`是函数的内部对象. 如果 ` str.c_str() == *_Eptr`，它将引发 `invalid_argument` 类型的对象。 如果此类调用将设置 `errno`，它将引发 `out_of_range` 类型的对象。 否则为如果*idx*不是 null 指针，函数存储`*_Eptr -  str.c_str()`中`*idx`，并返回`val`。

## <a name="stoull"></a>  stoull

将转换为字符序列**无符号长长**。

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

|参数|描述|
|---------------|-----------------|
|*str*|要转换的字符序列。|
|*idx*|首个未转换字符的索引值。|
|*base*|要使用的号码基。|

### <a name="return-value"></a>返回值

**无符号长长**值。

### <a name="remarks"></a>备注

该函数中的元素的序列转换*str*为值`val`类型的**unsigned long long**通过调用`strtoull( str.c_str(), _Eptr, idx)`，其中`_Eptr`是一个对象的内部函数。 如果 ` str.c_str() == *_Eptr`，它将引发 `invalid_argument` 类型的对象。 如果此类调用将设置 `errno`，它将引发 `out_of_range` 类型的对象。 否则为如果*idx*不是 null 指针，函数存储`*_Eptr -  str.c_str()`中`*idx`，并返回`val`。

## <a name="swap"></a>  swap

交换两个字符串的字符数组。

```cpp
template <class Traits, class Allocator>
void swap(basic_string<CharType, Traits, Allocator>& left, basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>参数

*left*<br/>
要与另一个字符串交换元素的字符串。

*right*<br/>
要与第一个字符串交换元素的另一个字符串。

### <a name="remarks"></a>备注

该模板函数执行专用的成员函数*左*。[交换](../standard-library/basic-string-class.md#swap)(*右*) 对于字符串，这样可以保证恒定的复杂性。

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

## <a name="to_string"></a>  to_string

将一个值转换为 `string`。

```cpp
string to_string(int Val);
string to_string(unsigned int Val);
string to_string(long Val);
string to_string(unsigned long Val);
string to_string(long long Val);
string to_string(unsigned long long Val);
string to_string(float Val);
string to_string(double Val);
string to_string(long double Val);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*Val*|要转换的值。|

### <a name="return-value"></a>返回值

表示该值的 `string`。

### <a name="remarks"></a>备注

该函数将转换*Val*为数组对象中存储的元素的顺序`Buf`内部函数通过调用`sprintf(Buf, Fmt, Val)`，其中`Fmt`是

- `"%d"` 如果`Val`具有类型**int**

- `"%u"` 如果`Val`具有类型**无符号的整数**

- `"%ld"` 如果`Val`具有类型**长**

- `"%lu"` 如果`Val`具有类型**无符号长**

- `"%lld"` 如果`Val`具有类型**长时间长**

- `"%llu"` 如果`Val`具有类型**无符号长时间长**

- `"%f"` 如果`Val`具有类型**float**或**双精度**

- `"%Lf"` 如果`Val`具有类型**长双精度**

该函数返回 `string(Buf)`。

## <a name="to_wstring"></a>  to_wstring

将一个值转换为宽字符串。

```cpp
wstring to_wstring(int Val);
wstring to_wstring(unsigned int Val);
wstring to_wstring(long Val);
wstring to_wstring(unsigned long Val);
wstring to_wstring(long long Val);
wstring to_wstring(unsigned long long Val);
wstring to_wstring(float Val);
wstring to_wstring(double Val);
wstring to_wstring(long double Val);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|`Val`|要转换的值。|

### <a name="return-value"></a>返回值

表示该值的宽字符串。

### <a name="remarks"></a>备注

此函数可将 `Val` 转换为存储在函数内部数组对象 `Buf` 中的元素序列，就像调用 `swprintf(Buf, Len, Fmt, Val)` 一样，其中 `Fmt` 是

- `L"%d"` 如果`Val`具有类型**int**

- `L"%u"` 如果`Val`具有类型**无符号的整数**

- `L"%ld"` 如果`Val`具有类型**长**

- `L"%lu"` 如果`Val`具有类型**无符号长**

- `L"%lld"` 如果`Val`具有类型**长时间长**

- `L"%llu"` 如果`Val`具有类型**无符号长时间长**

- `L"%f"` 如果`Val`具有类型**float**或**双精度**

- `L"%Lf"` 如果`Val`具有类型**长双精度**

该函数返回 `wstring(Buf)`。

## <a name="see-also"></a>请参阅

[\<string>](../standard-library/string.md)<br/>

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
ms.openlocfilehash: 828aeb975178850f5c0a7ea3b7e982bbadd6e7c4
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455599"
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

*is*\
要从其中提取字符串的输入流。

*字符串*\
从输入流读取的字符将放入的字符串。

*delim*\
行分隔符。

### <a name="return-value"></a>返回值

输入流*是*。

### <a name="remarks"></a>备注

标记`(1)`为从中提取字符的函数签名对在找到*delim* *之前,* 将它们存储在*str*中。

标记`(2)`为使用换行符作为默认行分隔符的函数签名对, 并表现为**getline**(`is`、 `str`、 `is`)。 `widen`(' `\n`')).

每对函数中的第二个函数是第一个的模拟，它的作用是支持 [rvalue 引用](../cpp/lvalues-and-rvalues-visual-cpp.md)。

发生下列情况之一时，提取将停止：

- 在文件结尾处, 的内部状态标志设置为。  `ios_base::eofbit`

- 函数提取经比较与 `delim` 相等的元素后，既不放回该元素，也不将它追加到受控序列的情况。

- 函数提取`str.`了[max_size](../standard-library/basic-string-class.md#max_size)元素后, 在这种情况下 *, 的内部*状态标志设置为`ios_base::failbit`。

- 除前面列出的其他一些错误, 在这种情况下 *, 的内部*状态标志设置为`ios_base::badbit`

有关内部状态标志的信息，请参阅 [ios_base::iostate](../standard-library/ios-base-class.md#iostate)。

如果该函数未提取任何元素, 则的内部状态标志设置为`ios_base::failbit`。 在任何情况下`getline` ,*均返回为*。

如果引发异常,*则为*, 并且*str*处于有效状态。

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

将字符序列转换为**双精度型**。

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

**双精度**值。

### <a name="remarks"></a>备注

函数将*str*中的元素序列转换为**double**类型的`val`值, 就像调用`strtod( str.c_str(), _Eptr)`一样, 其中`_Eptr` , 是函数的内部对象。 如果 ` str.c_str() == *_Eptr`，它将引发 `invalid_argument` 类型的对象。 如果此类调用将设置 `errno`，它将引发 `out_of_range` 类型的对象。 否则, 如果*idx*不是 null 指针, 该函数将存储`*_Eptr -  str.c_str()`在`*idx`中并`val`返回。

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

函数将*str*中的元素序列转换为**float**类型的`val`值, 就像调用`strtof( str.c_str(), _Eptr)`一样, 其中`_Eptr` , 是函数的内部对象。 如果 ` str.c_str() == *_Eptr`，它将引发 `invalid_argument` 类型的对象。 如果此类调用将设置 `errno`，它将引发 `out_of_range` 类型的对象。 否则, 如果*idx*不是 null 指针, 该函数将存储`*_Eptr -  str.c_str()`在`*idx`中并`val`返回。

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

函数`stoi`将*str*中字符的序列转换为类型为**int**的值, 并返回值。 例如，在传递字符序列“10”时，`stoi` 返回的值为整数 10.

当以 `stoi` 方式调用时，`strtol` 的行为方式与针对单字节字符的 `strtol( str.c_str(), _Eptr, idx)` 函数相似，其中，`_Eptr` 是函数的内部对象；而当以类似的方式 `wcstol` 调用时，其行为与针对宽字符的 `wcstol(Str.c_str(), _Eptr, idx)` 相似。 有关详细信息，请参阅 [strtol、wcstol、_strtol_l、_wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)。

如果`str.c_str() == *_Eptr`为`stoi` , 则引发类型`invalid_argument`的对象。 如果此类调用将设置`errno`, 或者如果返回值无法表示为**int**类型的对象, 则它将引发类型`out_of_range`的对象。 否则, 如果*idx*不是 null 指针, 该函数将存储`*_Eptr - str.c_str()`在`*idx`中。

## <a name="stol"></a>  stol

将字符序列转换为**long 类型**。

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

函数将*str*中的元素序列转换为**long**类型的`val`值, 就像调用`strtol( str.c_str(), _Eptr, idx)`一样, 其中`_Eptr` , 是函数的内部对象。 如果 ` str.c_str() == *_Eptr`，它将引发 `invalid_argument` 类型的对象。 如果此类调用将设置 `errno`，它将引发 `out_of_range` 类型的对象。 否则, 如果*idx*不是 null 指针, 该函数将存储`*_Eptr -  str.c_str()`在`*idx`中并`val`返回。

## <a name="stold"></a>  stold

将字符序列转换为**长双精度值**。

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

**长双精度**值。

### <a name="remarks"></a>备注

函数将*str*中的元素序列转换为**long double**类型`val`的值, 就像调用`strtold( str.c_str(), _Eptr)`一样, 其中`_Eptr` , 是函数的内部对象。 如果 ` str.c_str() == *_Eptr`，它将引发 `invalid_argument` 类型的对象。 如果此类调用将设置 `errno`，它将引发 `out_of_range` 类型的对象。 否则, 如果*idx*不是 null 指针, 该函数将存储`*_Eptr -  str.c_str()`在`*idx`中并`val`返回。

## <a name="stoll"></a>  stoll

将字符序列转换为**长**整型。

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

**长整型**值。

### <a name="remarks"></a>备注

函数将*str*中的元素序列转换为**long**类型的`val`值, 就像调用`strtoll( str.c_str(), _Eptr, idx)`一样, 其中`_Eptr` , 是函数的内部对象。 如果 ` str.c_str() == *_Eptr`，它将引发 `invalid_argument` 类型的对象。 如果此类调用将设置 `errno`，它将引发 `out_of_range` 类型的对象。 否则, 如果*idx*不是 null 指针, 该函数将存储`*_Eptr -  str.c_str()`在`*idx`中并`val`返回。

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

函数将*str*中的元素序列转换`val`为类型为**无符号**的值, 就像调用`strtoul( str.c_str(), _Eptr, idx)`一样, 其中`_Eptr` , 是函数的内部对象。 如果 ` str.c_str() == *_Eptr`，它将引发 `invalid_argument` 类型的对象。 如果此类调用将设置 `errno`，它将引发 `out_of_range` 类型的对象。 否则, 如果*idx*不是 null 指针, 该函数将存储`*_Eptr -  str.c_str()`在`*idx`中并`val`返回。

## <a name="stoull"></a>  stoull

将字符序列转换为**无符号长**整数。

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

**无符号长**整型值。

### <a name="remarks"></a>备注

函数将*str*中的元素序列转换`val`为类型为**无符号长**的值, 就像调用`strtoull( str.c_str(), _Eptr, idx)`一样, 其中`_Eptr` , 是函数的内部对象。 如果 ` str.c_str() == *_Eptr`，它将引发 `invalid_argument` 类型的对象。 如果此类调用将设置 `errno`，它将引发 `out_of_range` 类型的对象。 否则, 如果*idx*不是 null 指针, 该函数将存储`*_Eptr -  str.c_str()`在`*idx`中并`val`返回。

## <a name="swap"></a>  swap

交换两个字符串的字符数组。

```cpp
template <class Traits, class Allocator>
void swap(basic_string<CharType, Traits, Allocator>& left, basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>参数

*左中*\
要与另一个字符串交换元素的字符串。

*然后*\
要与第一个字符串交换元素的另一个字符串。

### <a name="remarks"></a>备注

此模板函数会执行*左侧*专用成员函数。[交换](../standard-library/basic-string-class.md#swap)(*右侧*) 对于字符串, 可保证恒定的复杂性。

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
|*初始值*|要转换的值。|

### <a name="return-value"></a>返回值

表示该值的 `string`。

### <a name="remarks"></a>备注

函数将*Val*转换为存储在函数内部数组对象`Buf`中的元素序列, 就像调用`sprintf(Buf, Fmt, Val)`一样, 其中`Fmt`是

- `"%d"`如果`Val`具有**int**类型

- `"%u"`如果`Val`具有类型**无符号 int**

- `"%ld"`如果`Val`类型**长**

- `"%lu"`如果`Val`类型**无符号长**

- `"%lld"`如果`Val`类型**长**长

- `"%llu"`如果`Val`类型**无符号长**长

- `"%f"`如果`Val`类型为**float**或**double**

- `"%Lf"`if `Val`类型为**long double**

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

- `L"%d"`如果`Val`具有**int**类型

- `L"%u"`如果`Val`具有类型**无符号 int**

- `L"%ld"`如果`Val`类型**长**

- `L"%lu"`如果`Val`类型**无符号长**

- `L"%lld"`如果`Val`类型**长**长

- `L"%llu"`如果`Val`类型**无符号长**长

- `L"%f"`如果`Val`类型为**float**或**double**

- `L"%Lf"`if `Val`类型为**long double**

该函数返回 `wstring(Buf)`。

## <a name="see-also"></a>请参阅

[\<string>](../standard-library/string.md)

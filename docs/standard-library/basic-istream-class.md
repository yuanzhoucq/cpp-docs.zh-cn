---
title: basic_istream 类
ms.date: 11/04/2016
f1_keywords:
- istream/std::basic_istream
- istream/std::basic_istream::gcount
- istream/std::basic_istream::get
- istream/std::basic_istream::getline
- 'istream/std::basic_istream::'
- istream/std::basic_istream::peek
- istream/std::basic_istream::putback
- istream/std::basic_istream::read
- istream/std::basic_istream::readsome
- istream/std::basic_istream::seekg
- istream/std::basic_istream::sentry
- istream/std::basic_istream::swap
- istream/std::basic_istream::sync
- istream/std::basic_istream::tellg
- istream/std::basic_istream::unget
helpviewer_keywords:
- std::basic_istream [C++]
- std::basic_istream [C++], gcount
- std::basic_istream [C++], get
- std::basic_istream [C++], getline
- std::basic_istream [C++], OVERWRITE
- std::basic_istream [C++], peek
- std::basic_istream [C++], putback
- std::basic_istream [C++], read
- std::basic_istream [C++], readsome
- std::basic_istream [C++], seekg
- std::basic_istream [C++], sentry
- std::basic_istream [C++], swap
- std::basic_istream [C++], sync
- std::basic_istream [C++], tellg
- std::basic_istream [C++], unget
ms.assetid: c7c27111-de6d-42b4-95a3-a7e65259bf17
ms.openlocfilehash: 03a6e3a65d6dc8c2fa896949855bd23a01578e5a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376828"
---
# <a name="basic_istream-class"></a>basic_istream 类

描述一个对象，它控制从具有类型为 `Char_T` 的元素的流缓冲区提取元素和编码对象的操作，其中该类型也称为 [char_type](../standard-library/basic-ios-class.md#char_type)，其字符特征由类 *Tr*（也称为 [traits_type](../standard-library/basic-ios-class.md#traits_type)）决定。

## <a name="syntax"></a>语法

```cpp
template <class Char_T, class Tr = char_traits<Char_T>>
class basic_istream : virtual public basic_ios<Char_T, Tr>
```

## <a name="remarks"></a>备注

大多数重载 [operator>>](#op_gt_gt) 的成员函数都是格式化的输入函数。 它们遵循以下模式：

```cpp
iostate state = goodbit;
const sentry ok(*this);

if (ok)
{
    try
    {
        /*extract elements and convert
            accumulate flags in state.
            store a successful conversion*/
    }
    catch (...)
    {
        try
        {
            setstate(badbit);

        }
        catch (...)
        {
        }
        if ((exceptions()& badbit) != 0)
            throw;
    }
}
setstate(state);

return (*this);
```

许多其他成员函数是未格式化的输入函数。 它们遵循以下模式：

```cpp
iostate state = goodbit;
count = 0;    // the value returned by gcount
const sentry ok(*this, true);

if (ok)
{
    try
    {
        /* extract elements and deliver
            count extracted elements in count
            accumulate flags in state */
    }
    catch (...)
    {
        try
        {
            setstate(badbit);

        }
        catch (...)
        {
        }
        if ((exceptions()& badbit) != 0)
            throw;
    }
}
setstate(state);
```

如果两组函数在[`setstate`](../standard-library/basic-ios-class.md#setstate)`(eofbit)`提取元素时遇到文件结尾，则调用它们。

类`basic_istream<Char_T, Tr>`存储的对象：

- 类[`basic_ios`](../standard-library/basic-ios-class.md)`<Char_T, Tr>`的虚拟公共基础对象。

- 最后一个未格式化的输入操作（在前一代码中`count`调用）的提取计数。

## <a name="example"></a>示例

请参阅 [basic_ifstream 类](../standard-library/basic-ifstream-class.md)的示例，了解输入流的详细信息。

### <a name="constructors"></a>构造函数

|构造函数|说明|
|-|-|
|[basic_istream](#basic_istream)|构造 `basic_istream` 类型的对象。|

### <a name="member-functions"></a>成员职能

|成员函数|说明|
|-|-|
|[gcount](#gcount)|返回在最后一个未格式化输入期间读取的字符数。|
|[get](#get)|从输入流中读取一个或多个字符。|
|[getline](#getline)|从输入流中读取一行。|
|[忽略](#ignore)|导致从当前读取位置跳过大量元素。|
|[偷看](#peek)|返回要读取的下一字符。|
|[putback](#putback)|将指定的字符放入流。|
|[读](#read)|从流中读取指定数目的字符，并将其存储到数组中。|
|[readsome](#readsome)|仅从缓冲区读取。|
|[seekg](#seekg)|在流中移动读取位置。|
|[sentry](#sentry)|嵌套类描述一个其声明构造了格式化和未格式化的输入函数的对象。|
|[交换](#swap)|将此 `basic_istream` 对象与所提供的 `basic_istream` 对象参数进行交换。|
|[sync](#sync)|将流的关联输入设备与流的缓冲区同步。|
|[tellg](#tellg)|报告流中的当前读取位置。|
|[unget](#unget)|将最近读取的字符放回流中。|

### <a name="operators"></a>运算符

|操作员|说明|
|-|-|
|[运算符>>](#op_gt_gt)|调用输入流上的函数或从输入流中读取格式化数据。|
|[运算符*](#op_eq)|将运算符右侧上的 `basic_istream` 分配给此对象。 这是一个移动分配，涉及不`rvalue`留下副本的引用。|

## <a name="requirements"></a>要求

**标头：** \<istream>

**命名空间:** std

## <a name="basic_istreambasic_istream"></a><a name="basic_istream"></a>basic_istream：basic_istream

构造 `basic_istream` 类型的对象。

```cpp
explicit basic_istream(
    basic_streambuf<Char_T, Tr>* strbuf,
    bool _Isstd = false);

basic_istream(basic_istream&& right);
```

### <a name="parameters"></a>参数

*斯特布夫*\
类型 [basic_streambuf](../standard-library/basic-streambuf-class.md) 的对象。

*_Isstd*\
如果它是标准流，**则为 true;** 否则，**假**。

*对*\
要复制的 `basic_istream` 对象。

### <a name="remarks"></a>备注

第一个构造函数通过调用[`init`](../standard-library/basic-ios-class.md#init)`(strbuf)`初始化基类。 它还在提取计数中存储零。 有关此提取计数的详细信息，请参阅[basic_istream类](../standard-library/basic-istream-class.md)概述的备注部分。

第二个构造函数通过调用 `move(right)` 初始化基类。 它还存储在`right.gcount()`提取计数中，并将零存储在 [右] 的提取计数中。

### <a name="example"></a>示例

请参阅 [basic_ifstream::basic_ifstream](../standard-library/basic-ifstream-class.md#basic_ifstream) 的示例，了解输入流的详细信息。

## <a name="basic_istreamgcount"></a><a name="gcount"></a>basic_istream：克数

返回在最后一个未格式化输入期间读取的字符数。

```cpp
streamsize gcount() const;
```

### <a name="return-value"></a>返回值

提取计数。

### <a name="remarks"></a>备注

使用 [basic_istream::get](#get) 读取未格式化的字符。

### <a name="example"></a>示例

```cpp
// basic_istream_gcount.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   cout << "Type the letter 'a': ";

   ws( cin );
   char c[10];

   cin.get( &c[0],9 );
   cout << c << endl;

   cout << cin.gcount( ) << endl;
}
```

```Input
a
```

```Output
Type the letter 'a': a
1
```

## <a name="basic_istreamget"></a><a name="get"></a>basic_istream：获取

从输入流中读取一个或多个字符。

```cpp
int_type get();

basic_istream<Char_T, Tr>& get(Char_T& Ch);
basic_istream<Char_T, Tr>& get(Char_T* str, streamsize count);
basic_istream<Char_T, Tr>& get(Char_T* str, streamsize count, Char_T delimiter);

basic_istream<Char_T, Tr>& get(basic_streambuf<Char_T, Tr>& strbuf);
basic_istream<Char_T, Tr>& get(basic_streambuf<Char_T, Tr>& strbuf, Char_T delimiter);
```

### <a name="parameters"></a>参数

*计数*\
要从 *strbuf* 读取的字符数。

*分隔符*\
应在*计数*之前遇到应终止读取的字符。

*Str*\
写入的字符串。

*Ch*\
要获取的字符。

*斯特布夫*\
要写入的缓冲区。

### <a name="return-value"></a>返回值

get 的无参数形式返回作为整数或文件结尾读取的元素。 其余形式返回流 (* `this`)。

### <a name="remarks"></a>备注

第一个未格式化的输入函数提取一个元素（如果可能，就像返回`rdbuf->sbumpc`一样）。 否则，它将返回`traits_type::`[`eof`](../standard-library/char-traits-struct.md#eof)。 如果函数不提取任何元素，它将调用[`setstate`](../standard-library/basic-ios-class.md#setstate)`(failbit)`。

第二个函数以相同的方式提取 [int_type](../standard-library/basic-ios-class.md#int_type) 元素 `meta`。 如果`meta`比较等于`traits_type::eof`， 函数调用`setstate(failbit)`。 否则，它存储在`traits_type::`[`to_char_type`](../standard-library/char-traits-struct.md#to_char_type)`(meta)`*Ch*。 函数返回 ___this__。

第三个函数`get(str, count, widen('\n'))`返回 。

第四个函数提取到`count - 1`元素，并将它们存储在从*str*开始的数组中。 在存储任何提取的元素后，它始终存储 `char_type`。 按测试顺序，提取在以下位置停止：

- 在文件结尾。

- 函数提取一个与*分隔符*相等的元素。 在这种情况下，元素将放回受控序列。

- 函数提取`count - 1`元素后。

如果此函数没有提取任何元素，则会调用 `setstate(failbit)`. 在任何情况下，它返回 ___this__。

第五个函数`get(strbuf, widen('\n'))`返回 。

第六个函数提取元素并将它们插入到 *strbuf*。 提取停止在文件结尾或元素上，该元素比较等于*分隔符*，不提取。 如果插入失败或引发异常（可捕获异常但不会再次引发），提取也会在未提取所讨论的元素的情况下停止。 如果此函数没有提取任何元素，则会调用 `setstate(failbit)`. 在任何情况下，函数返回 ___this__。

### <a name="example"></a>示例

```cpp
// basic_istream_get.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   char c[10];

   c[0] = cin.get( );
   cin.get( c[1] );
   cin.get( &c[2],3 );
   cin.get( &c[4], 4, '7' );

   cout << c << endl;
}
```

```Output
1111
```

## <a name="basic_istreamgetline"></a><a name="getline"></a>basic_istream：获取线

从输入流中获取一行。

```cpp
basic_istream<Char_T, Tr>& getline(
    char_type* str,
    streamsize count);

basic_istream<Char_T, Tr>& getline(
    char_type* str,
    streamsize count,
    char_type delimiter);
```

### <a name="parameters"></a>参数

*计数*\
要从 *strbuf* 读取的字符数。

*分隔符*\
应在*计数*之前遇到应终止读取的字符。

*Str*\
写入的字符串。

### <a name="return-value"></a>返回值

流 （__#这个__）.

### <a name="remarks"></a>备注

这些未格式化的输入函数中的第一个`getline(str, count, widen('\n'))`返回 。

第二个函数提取到`count - 1`元素，并将它们存储在从*str*开始的数组中。 在存储任何提取的元素后，它始终存储字符串终止字符。 按测试顺序，提取在以下位置停止：

- 在文件结尾。

- 函数提取一个与*分隔符*相等的元素。 在这种情况下，元素不会放回，也不会追加到受控序列中。

- 函数提取`count - 1`元素后。

如果函数不提取任何元素或`count - 1`元素，它将调用[`setstate`](../standard-library/basic-ios-class.md#setstate)`(failbit)`。 在任何情况下，它返回 ___this__。

### <a name="example"></a>示例

```cpp
// basic_istream_getline.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   char c[10];

   cin.getline( &c[0], 5, '2' );
   cout << c << endl;
}
```

```Output
121
```

## <a name="basic_istreamignore"></a><a name="ignore"></a>basic_istream：忽略

导致从当前读取位置跳过大量元素。

```cpp
basic_istream<Char_T, Tr>& ignore(
    streamsize count = 1,
    int_type delimiter = traits_type::eof());
```

### <a name="parameters"></a>参数

*计数*\
要从当前读取位置跳过的元素数。

*分隔符*\
在计数之前遇到的元素会导致`ignore`返回，并允许在*分隔符*之后读取所有元素。

### <a name="return-value"></a>返回值

流 （__#这个__）.

### <a name="remarks"></a>备注

未格式化的输入函数将提取以对元素*进行计数*并丢弃它们。 但是*count*，如果计数`numeric_limits<int>::max`等于，则视为任意大。 提取在文件末尾`Ch`或元素上早期停止，`traits_type::`[`to_int_type`](../standard-library/char-traits-struct.md#to_int_type)`(Ch)`以便与*分隔符*（也提取）进行比较。 函数返回 ___this__。

### <a name="example"></a>示例

```cpp
// basic_istream_ignore.cpp
// compile with: /EHsc
#include <iostream>
int main( )
{
   using namespace std;
   char chararray[10];
   cout << "Type 'abcdef': ";
   cin.ignore( 5, 'c' );
   cin >> chararray;
   cout << chararray;
}
```

```Output
Type 'abcdef': abcdef
def
```

## <a name="basic_istreamoperator"></a><a name="op_gt_gt"></a>基本\_istream：：操作员>>

调用输入流上的函数或从输入流中读取格式化数据。

```cpp
basic_istream& operator>>(basic_istream& (* Pfn)(basic_istream&));
basic_istream& operator>>(ios_base& (* Pfn)(ios_base&));
basic_istream& operator>>(basic_ios<Char_T, Tr>& (* Pfn)(basic_ios<Char_T, Tr>&));
basic_istream& operator>>(basic_streambuf<Char_T, Tr>* strbuf);
basic_istream& operator>>(bool& val);
basic_istream& operator>>(short& val);
basic_istream& operator>>(unsigned short& val);
basic_istream& operator>>(int& val);
basic_istream& operator>>(unsigned int& val);
basic_istream& operator>>(long& val);
basic_istream& operator>>(unsigned long& val);
basic_istream& operator>>(long long& val);
basic_istream& operator>>(unsigned long long& val);
basic_istream& operator>>(void *& val);
basic_istream& operator>>(float& val);
basic_istream& operator>>(double& val);
basic_istream& operator>>(long double& val);
```

### <a name="parameters"></a>参数

*普芬*\
函数指针。

*斯特布夫*\
一个 `stream_buf` 类型的对象。

*瓦尔*\
要从流中读取的值。

### <a name="return-value"></a>返回值

流 （__#这个__）.

### <a name="remarks"></a>备注

\<istream>标头还定义了多个全局提取运算符。 有关详细信息，请参阅 [operator>> (\<istream>)](../standard-library/istream-operators.md#op_gt_gt)。

第一`istr >> ws`个成员函数确保窗体的表达式调用[`ws`](../standard-library/istream-functions.md#ws)`(istr)`，然后返回 ___this__。 第二个和第三个函数可确保其他操纵器（如[`hex`](../standard-library/ios-functions.md#hex)）的行为类似。 其余函数是格式化的输入函数。

函数：

```cpp
basic_istream& operator>>(
    basic_streambuf<Char_T, Tr>* strbuf);
```

提取元素，如果*strbuf*不是空指针，并在*strbuf*中插入它们。 提取在文件结尾停止。 如果插入失败或引发异常（可捕获异常但不会再次引发），提取也会在未提取所讨论的元素的情况下停止。 如果函数不提取任何元素，它将调用[`setstate`](../standard-library/basic-ios-class.md#setstate)`(failbit)`。 在任何情况下，函数返回 ___this__。

函数：

```cpp
basic_istream& operator>>(bool& val);
```

提取[`use_facet`](../standard-library/basic-filebuf-class.md#open)`< num_get<Char_T, InIt>(`[`getloc`](../standard-library/ios-base-class.md#getloc)`).`[`get`](../standard-library/ios-base-class.md#getloc)字段并通过`( InIt(`调用[`rdbuf`](../standard-library/basic-ios-class.md#rdbuf)将其转换为布尔`), Init(0), *this, getloc, val)`值。 此处定义为`InIt`[`istreambuf_iterator`](../standard-library/istreambuf-iterator-class.md)`<Char_T, Tr>`。 函数返回 ___this__。

每个功能：

```cpp
basic_istream& operator>>(short& val);
basic_istream& operator>>(unsigned short& val);
basic_istream& operator>>(int& val);
basic_istream& operator>>(unsigned int& val);
basic_istream& operator>>(long& val);
basic_istream& operator>>(unsigned long& val);
basic_istream& operator>>(long long& val);
basic_istream& operator>>(unsigned long long& val);
basic_istream& operator>>(void *& val);
```

提取字段，并通过调用`use_facet<num_get<Char_T, InIt>(getloc).`[`get`](#get)`(InIt(rdbuf), Init(0), *this, getloc, val)`将其转换为数值。 此处，`InIt`定义为`istreambuf_iterator<Char_T, Tr>` *，val*具有**长**、**无符号长**或**根据需要 void**<strong>\*</strong>的类型。

如果转换的值不能表示为*val*类型，则函数将调用[`setstate`](../standard-library/basic-ios-class.md#setstate)`(failbit)`。 在任何情况下，函数返回 ___this__。

每个功能：

```cpp
basic_istream& operator>>(float& val);
basic_istream& operator>>(double& val);
basic_istream& operator>>(long double& val);
```

提取字段，并通过调用`use_facet<num_get<Char_T, InIt>(getloc).get(InIt(rdbuf), Init(0), *this, getloc, val)`将其转换为数值。 此处，`InIt`定义为`istreambuf_iterator<Char_T, Tr>` *，val*根据需要具有**双**精度或**长双精度。**

如果转换的值不能表示为*val*类型，则函数将调用`setstate(failbit)`。 在任何情况下，它返回 ___this__。

### <a name="example"></a>示例

```cpp
// istream_basic_istream_op_is.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;

ios_base& hex2( ios_base& ib )
{
   ib.unsetf( ios_base::dec );
   ib.setf( ios_base::hex );
   return ib;
}

basic_istream<char, char_traits<char> >& somefunc(basic_istream<char, char_traits<char> > &i)
{
   if ( i == cin )
   {
      cerr << "i is cin" << endl;
   }
   return i;
}

int main( )
{
   int i = 0;
   cin >> somefunc;
   cin >> i;
   cout << i << endl;
   cin >> hex2;
   cin >> i;
   cout << i << endl;
}
```

## <a name="basic_istreamoperator"></a><a name="op_eq"></a>basic_istream：：操作员*

将运算符右侧上的 `basic_istream` 分配给此对象。 这是一个移动分配，涉及不`rvalue`留下副本的引用。

```cpp
basic_istream& operator=(basic_istream&& right);
```

### <a name="parameters"></a>参数

*对*\
对 `basic_ifstream` 对象的 `rvalue` 引用。

### <a name="return-value"></a>返回值

返回 ___this__。

### <a name="remarks"></a>备注

成员运算符调用`swap(right)`。

## <a name="basic_istreampeek"></a><a name="peek"></a>basic_istream：:p耶克

返回要读取的下一字符。

```cpp
int_type peek();
```

### <a name="return-value"></a>返回值

要读取的下一字符。

### <a name="remarks"></a>备注

如果可能，未格式化的输入函数将提取一个元素，就像返回`rdbuf->`[`sgetc`](../standard-library/basic-streambuf-class.md#sgetc)一样。 否则，它将返回`traits_type::`[`eof`](../standard-library/char-traits-struct.md#eof)。

### <a name="example"></a>示例

```cpp
// basic_istream_peek.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   char c[10], c2;
   cout << "Type 'abcde': ";

   c2 = cin.peek( );
   cin.getline( &c[0], 9 );

   cout << c2 << " " << c << endl;
}
```

```Input
abcde
```

```Output
Type 'abcde': abcde
a abcde
```

## <a name="basic_istreamputback"></a><a name="putback"></a>basic_istream：:p

将指定的字符放入流。

```cpp
basic_istream<Char_T, Tr>& putback(
    char_type Ch);
```

### <a name="parameters"></a>参数

*Ch*\
要放回到流中的字符。

### <a name="return-value"></a>返回值

流 （__#这个__）.

### <a name="remarks"></a>备注

[未格式化的输入函数](../standard-library/basic-istream-class.md)将*Ch（* 如果可能）放回，就像调用[`rdbuf`](../standard-library/basic-ios-class.md#rdbuf)`->`[`sputbackc`](../standard-library/basic-streambuf-class.md#sputbackc)一样。 如果`rdbuf`为空指针，或者`sputbackc`对 的调用返回`traits_type::`[`eof`](../standard-library/char-traits-struct.md#eof)，则函数将[`setstate`](../standard-library/basic-ios-class.md#setstate)`(badbit)`调用 。 在任何情况下，它返回 ___this__。

### <a name="example"></a>示例

```cpp
// basic_istream_putback.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   char c[10], c2, c3;

   c2 = cin.get( );
   c3 = cin.get( );
   cin.putback( c2 );
   cin.getline( &c[0], 9 );
   cout << c << endl;
}
```

```Output
qwq
```

## <a name="basic_istreamread"></a><a name="read"></a>basic_istream：：阅读

从流中读取指定数目的字符，并将其存储到数组中。

此方法可能并不安全，因为它依赖于调用方检查所传递的值是否正确。

```cpp
basic_istream<Char_T, Tr>& read(
    char_type* str,
    streamsize count);
```

### <a name="parameters"></a>参数

*Str*\
要从中读取字符的数组。

*计数*\
要读取的字符数。

### <a name="return-value"></a>返回值

流 ( `*this`)。

### <a name="remarks"></a>备注

未格式化的输入函数提取到*对元素进行计数*，并将它们存储在从*str*开始的数组中。 提取在文件末尾早期停止，在这种情况下函数调用[`setstate`](../standard-library/basic-ios-class.md#setstate)`(failbit)`。 在任何情况下，它返回 ___this__。

### <a name="example"></a>示例

```cpp
// basic_istream_read.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main()
{
    char c[10];
    int count = 5;

    cout << "Type 'abcde': ";

    // Note: cin::read is potentially unsafe, consider
    // using cin::_Read_s instead.
    cin.read(&c[0], count);
    c[count] = 0;

    cout << c << endl;
}
```

```Input
abcde
```

```Output
Type 'abcde': abcde
abcde
```

## <a name="basic_istreamreadsome"></a><a name="readsome"></a>basic_istream：：阅读

读取指定数量的字符值。

此方法可能并不安全，因为它依赖于调用方检查所传递的值是否正确。

```cpp
streamsize readsome(
    char_type* str,
    streamsize count);
```

### <a name="parameters"></a>参数

*Str*\
`readsome` 存储它所读取字符的数组。

*计数*\
要读取的字符数。

### <a name="return-value"></a>返回值

实际读取的字符数[`gcount`](#gcount)。

### <a name="remarks"></a>备注

此未格式化的输入函数提取起来，从输入流*中计算*元素并将其存储在数组*str*中。

此函数不会等待输入。 它会读取任何可用的数据。

### <a name="example"></a>示例

```cpp
// basic_istream_readsome.cpp
// compile with: /EHsc /W3
#include <iostream>
using namespace std;

int main( )
{
   char c[10];
   int count = 5;

   cout << "Type 'abcdefgh': ";

   // cin.read blocks until user types input.
   // Note: cin::read is potentially unsafe, consider
   // using cin::_Read_s instead.
   cin.read(&c[0], 2);

   // Note: cin::readsome is potentially unsafe, consider
   // using cin::_Readsome_s instead.
   int n = cin.readsome(&c[0], count);  // C4996
   c[n] = 0;
   cout << n << " characters read" << endl;
   cout << c << endl;
}
```

## <a name="basic_istreamseekg"></a><a name="seekg"></a>basic_istream：seekg

在流中移动读取位置。

```cpp
basic_istream<Char_T, Tr>& seekg(pos_type pos);

basic_istream<Char_T, Tr>& seekg(off_type off, ios_base::seekdir way);
```

### <a name="parameters"></a>参数

*Pos*\
要将读取指针移动到的绝对位置。

*关闭*\
用于相对于方式移动读取指针*的*偏移量。

*方式*\
其中一个 [ios_base::seekdir](../standard-library/ios-base-class.md#seekdir) 枚举。

### <a name="return-value"></a>返回值

流 （__#这个__）.

### <a name="remarks"></a>备注

第一个成员函数执行绝对查找，第二个成员函数执行相对查找。

> [!NOTE]
> 不要对文本文件使用第二个成员函数，因为标准 C++ 不支持在文本文件中进行相对查找。

如果[`fail`](../standard-library/basic-ios-class.md#fail)为 false，则第一个成员`newpos =`[`rdbuf`](../standard-library/basic-ios-class.md#rdbuf)`->`[`pubseekpos`](../standard-library/basic-streambuf-class.md#pubseekpos)`(pos)`函数将调用`pos_type`，用于`newpos`某些临时对象 。 如果`fail`为 false，则第二`newpos = rdbuf->`[`pubseekoff`](../standard-library/basic-streambuf-class.md#pubseekoff)`( off, way)`个函数调用 。 在这两种情况下，如果`(off_type)newpos == (off_type)(-1)`（定位操作失败），则函数调用`istr.`[`setstate`](../standard-library/basic-ios-class.md#setstate)`(failbit)`。 两个函数返回 ___this__。

如果[`fail`](../standard-library/basic-ios-class.md#fail)为 true，则成员函数不执行任何操作。

### <a name="example"></a>示例

```cpp
// basic_istream_seekg.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main ( )
{
   using namespace std;
   ifstream file;
   char c, c1;

   file.open( "basic_istream_seekg.txt" );
   file.seekg(2);   // seek to position 2
   file >> c;
   cout << c << endl;
}
```

## <a name="basic_istreamsentry"></a><a name="sentry"></a>basic_istream：哨兵

嵌套类描述一个对象，其声明构造了格式化和未格式化的输入函数。

```cpp
class sentry {
   public:
   explicit sentry(
      basic_istream<Char_T, Tr>& _Istr,
      bool _Noskip = false);
   operator bool() const;
   };
```

### <a name="remarks"></a>备注

如果`_Istr.`[`good`](../standard-library/basic-ios-class.md#good)为 true，则构造函数：

- `_Istr.`[`tie`](../standard-library/basic-ios-class.md#tie)`->`[`flush`](../standard-library/basic-ostream-class.md#flush)如果`_Istr.tie`不是空指针，则调用。

- 有效调用[`ws`](../standard-library/istream-functions.md#ws)`(_Istr)`（`_Istr.`[`flags`](../standard-library/ios-base-class.md#flags)`&`如果[`skipws`](../standard-library/ios-functions.md#skipws)为非零）。

如果经过任何此类准备后，`_Istr.good`为 false，则构造函数`_Istr.`[`setstate`](../standard-library/basic-ios-class.md#setstate)`(failbit)`调用 。 在任何情况下，构造函数都存储 在`_Istr.good`中`status`返回的值。 稍后调用以`operator bool`传递此存储值。

## <a name="basic_istreamswap"></a><a name="swap"></a>basic_istream：交换

交换两个 `basic_istream` 对象的内容。

```cpp
void swap(basic_istream& right);
```

### <a name="parameters"></a>参数

*对*\
对 `basic_istream` 对象的左值引用。

### <a name="remarks"></a>备注

成员函数调用[`basic_ios::swap`](../standard-library/basic-ios-class.md#swap)`(right)`。 它还将提取计数与*右*的提取计数交换。

## <a name="basic_istreamsync"></a><a name="sync"></a>basic_istream：同步

将流的关联输入设备与流的缓冲区同步。

```cpp
int sync();
```

### <a name="return-value"></a>返回值

如果[`rdbuf`](../standard-library/basic-ios-class.md#rdbuf)为空指针，则函数返回 -1。 否则，它将调用`rdbuf->`[`pubsync`](../standard-library/basic-streambuf-class.md#pubsync)。 如果该调用返回 -1，则函数[`setstate`](../standard-library/basic-ios-class.md#setstate)`(badbit)`调用并返回 -1。 否则，该函数返回零。

## <a name="basic_istreamtellg"></a><a name="tellg"></a>basic_istream：泰尔格

报告流中的当前读取位置。

```cpp
pos_type tellg();
```

### <a name="return-value"></a>返回值

流中的当前新位置。

### <a name="remarks"></a>备注

如果[`fail`](../standard-library/basic-ios-class.md#fail)为 false，则成员函数[`rdbuf`](../standard-library/basic-ios-class.md#rdbuf)`->`[`pubseekoff`](../standard-library/basic-streambuf-class.md#pubseekoff)`(0, cur, in)`将返回 。 否则，将返回 `pos_type(-1)`。

### <a name="example"></a>示例

```cpp
// basic_istream_tellg.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main()
{
    using namespace std;
    ifstream file;
    char c;
    streamoff i;

    file.open("basic_istream_tellg.txt");
    i = file.tellg();
    file >> c;
    cout << c << " " << i << endl;

    i = file.tellg();
    file >> c;
    cout << c << " " << i << endl;
}
```

## <a name="basic_istreamunget"></a><a name="unget"></a>basic_istream：：不获取

将最近读取的字符放回流中。

```cpp
basic_istream<Char_T, Tr>& unget();
```

### <a name="return-value"></a>返回值

流 （__#这个__）.

### <a name="remarks"></a>备注

如果可能，[未格式化的输入函数](../standard-library/basic-istream-class.md)将流中的上一个元素放回原元素，就像调用`rdbuf->`[`sungetc`](../standard-library/basic-streambuf-class.md#sungetc)一样。 如果[`rdbuf`](../standard-library/basic-ios-class.md#rdbuf)为空指针，或者`sungetc`对 的调用返回`traits_type::`[`eof`](../standard-library/basic-ios-class.md#eof)，则函数将[`setstate`](../standard-library/basic-ios-class.md#setstate)`(badbit)`调用 。 在任何情况下，它返回 ___this__。

有关如何`unget`失败的信息，请参阅[`basic_streambuf::sungetc`](../standard-library/basic-streambuf-class.md#sungetc)。

### <a name="example"></a>示例

```cpp
// basic_istream_unget.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   char c[10], c2;

   cout << "Type 'abc': ";
   c2 = cin.get( );
   cin.unget( );
   cin.getline( &c[0], 9 );
   cout << c << endl;
}
```

```Input
abc
```

```Output
Type 'abc': abc
abc
```

## <a name="see-also"></a>另请参阅

[C++标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[电流编程](../standard-library/iostream-programming.md)\
[iostreams 约定](../standard-library/iostreams-conventions.md)

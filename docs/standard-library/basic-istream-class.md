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
ms.openlocfilehash: da53db594e057449f2d227f57c902d26396000b7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219243"
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

[`setstate`](../standard-library/basic-ios-class.md#setstate) `(eofbit)` 如果在提取元素时遇到文件末尾，两组函数都调用。

类存储的对象 `basic_istream<Char_T, Tr>` ：

- 类的虚拟公共基对象 [`basic_ios`](../standard-library/basic-ios-class.md) `<Char_T, Tr>` 。

- 最后一个未格式化输入操作的提取计数（ `count` 在前面的代码中称为）。

## <a name="example"></a>示例

请参阅 [basic_ifstream 类](../standard-library/basic-ifstream-class.md)的示例，了解输入流的详细信息。

### <a name="constructors"></a>构造函数

|构造函数|描述|
|-|-|
|[basic_istream](#basic_istream)|构造 `basic_istream` 类型的对象。|

### <a name="member-functions"></a>成员函数

|成员函数|说明|
|-|-|
|[gcount](#gcount)|返回在最后一个未格式化输入期间读取的字符数。|
|[get](#get)|从输入流中读取一个或多个字符。|
|[getline](#getline)|从输入流中读取一行。|
|[暂且](#ignore)|导致从当前读取位置跳过大量元素。|
|[预览](#peek)|返回要读取的下一字符。|
|[putback](#putback)|将指定的字符放入流。|
|[读取](#read)|从流中读取指定数目的字符，并将其存储到数组中。|
|[readsome](#readsome)|仅从缓冲区读取。|
|[seekg](#seekg)|在流中移动读取位置。|
|[sentry](#sentry)|嵌套类描述一个其声明构造了格式化和未格式化的输入函数的对象。|
|[swap](#swap)|将此 `basic_istream` 对象与所提供的 `basic_istream` 对象参数进行交换。|
|[同步](#sync)|将流的关联输入设备与流的缓冲区进行同步。|
|[tellg](#tellg)|报告流中的当前读取位置。|
|[unget](#unget)|将最近读取的字符放回流中。|

### <a name="operators"></a>运算符

|操作员|描述|
|-|-|
|[运算符>>](#op_gt_gt)|调用输入流上的函数或从输入流中读取格式化数据。|
|[operator =](#op_eq)|将运算符右侧上的 `basic_istream` 分配给此对象。 这是涉及 `rvalue` 不会留下副本的引用的移动赋值。|

## <a name="requirements"></a>要求

**标头：**\<istream>

**命名空间:** std

## <a name="basic_istreambasic_istream"></a><a name="basic_istream"></a>basic_istream：： basic_istream

构造 `basic_istream` 类型的对象。

```cpp
explicit basic_istream(
    basic_streambuf<Char_T, Tr>* strbuf,
    bool _Isstd = false);

basic_istream(basic_istream&& right);
```

### <a name="parameters"></a>参数

*strbuf*\
类型 [basic_streambuf](../standard-library/basic-streambuf-class.md) 的对象。

*_Isstd*\
**`true`** 如果它是标准流，则为;否则为 **`false`** 。

*然后*\
要复制的 `basic_istream` 对象。

### <a name="remarks"></a>备注

第一个构造函数通过调用来初始化基类 [`init`](../standard-library/basic-ios-class.md#init) `(strbuf)` 。 它还在提取计数中存储零。 有关此提取计数的详细信息，请参阅[Basic_istream 类](../standard-library/basic-istream-class.md)概述的 "备注" 部分。

第二个构造函数通过调用 `move(right)` 初始化基类。 它还在提取计数中存储 `right.gcount()` 零，并在 * right * * 的提取计数中存储零。

### <a name="example"></a>示例

请参阅 [basic_ifstream::basic_ifstream](../standard-library/basic-ifstream-class.md#basic_ifstream) 的示例，了解输入流的详细信息。

## <a name="basic_istreamgcount"></a><a name="gcount"></a>basic_istream：： gcount

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

## <a name="basic_istreamget"></a><a name="get"></a>basic_istream：： get

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

*计*\
要从 *strbuf* 读取的字符数。

*后面*\
在*count*之前应终止读取的字符。

*字符串*\
写入的字符串。

*48*\
要获取的字符。

*strbuf*\
要写入的缓冲区。

### <a name="return-value"></a>返回值

get 的无参数形式返回作为整数或文件结尾读取的元素。 其余窗体返回流（* **`this`** ）。

### <a name="remarks"></a>备注

如果可能，则第一个无格式的输入函数提取元素，就像返回一样 `rdbuf->sbumpc` 。 否则，它将返回 `traits_type::` [`eof`](../standard-library/char-traits-struct.md#eof) 。 如果函数未提取任何元素，则调用 [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)` 。

第二个函数以相同的方式提取 [int_type](../standard-library/basic-ios-class.md#int_type) 元素 `meta`。 如果与 `meta` 相等 `traits_type::eof` ，则函数将调用 `setstate(failbit)` 。 否则，它将存储 `traits_type::` [`to_char_type`](../standard-library/char-traits-struct.md#to_char_type) `(meta)` 在*Ch*中。 该函数返回 __* this__。

第三个函数返回 `get(str, count, widen('\n'))` 。

第四个函数提取 `count - 1` 元素，并将它们存储在从*str*开始的数组中。 在存储任何提取的元素后，它始终存储 `char_type`。 按测试顺序，提取在以下位置停止：

- 在文件结尾。

- 函数提取了比较等于*分隔符*的元素后。 在这种情况下，元素将返回到受控序列。

- 函数提取元素后 `count - 1` 。

如果此函数没有提取任何元素，则会调用 `setstate(failbit)`. 在任何情况下，它都会返回 __* this__。

第五个函数返回 `get(strbuf, widen('\n'))` 。

第六个函数提取元素并将它们插入到 *strbuf*。 提取在文件结尾处或对等于*分隔符*的元素（未提取）停止。 如果插入失败或引发异常（可捕获异常但不会再次引发），提取也会在未提取所讨论的元素的情况下停止。 如果此函数没有提取任何元素，则会调用 `setstate(failbit)`. 在任何情况下，函数均返回 __* this__。

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

## <a name="basic_istreamgetline"></a><a name="getline"></a>basic_istream：： getline

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

*计*\
要从 *strbuf* 读取的字符数。

*后面*\
在*count*之前应终止读取的字符。

*字符串*\
写入的字符串。

### <a name="return-value"></a>返回值

流（__* this__）。

### <a name="remarks"></a>备注

其中第一个未格式化的输入函数返回 `getline(str, count, widen('\n'))` 。

第二个函数提取最多个 `count - 1` 元素，并将它们存储在从*str*开始的数组中。 在存储任何提取的元素后，它始终存储字符串终止字符。 按测试顺序，提取在以下位置停止：

- 在文件结尾。

- 函数提取了比较等于*分隔符*的元素后。 在这种情况下，不会将元素放回，也不会将它追加到受控序列。

- 函数提取元素后 `count - 1` 。

如果该函数未提取任何元素或 `count - 1` 元素，则调用 [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)` 。 在任何情况下，它都会返回 __* this__。

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

## <a name="basic_istreamignore"></a><a name="ignore"></a>basic_istream：： ignore

导致从当前读取位置跳过大量元素。

```cpp
basic_istream<Char_T, Tr>& ignore(
    streamsize count = 1,
    int_type delimiter = traits_type::eof());
```

### <a name="parameters"></a>参数

*计*\
要从当前读取位置跳过的元素数。

*后面*\
如果在 count 之前遇到的元素，则会导致 `ignore` 返回并允许读取*分隔符*后面的所有元素。

### <a name="return-value"></a>返回值

流（__* this__）。

### <a name="remarks"></a>备注

未格式化的输入函数提取多*个元素，并将其*丢弃。 不过，如果*count*等于 `numeric_limits<int>::max` ，则会被视为任意大。 提取在文件结尾或与 `Ch` `traits_type::` [`to_int_type`](../standard-library/char-traits-struct.md#to_int_type) `(Ch)` *分隔符*（也被提取）相等的元素末尾提前停止。 该函数返回 __* this__。

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

## <a name="basic_istreamoperator"></a><a name="op_gt_gt"></a>基本 \_ istream：： operator>>

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

*Pfn*\
函数指针。

*strbuf*\
一个 `stream_buf` 类型的对象。

*初始值*\
要从流中读取的值。

### <a name="return-value"></a>返回值

流（__* this__）。

### <a name="remarks"></a>备注

\<istream> 标头还定义多个全局提取运算符。 有关详细信息，请参阅[operator>>  （ \<istream> ）](../standard-library/istream-operators.md#op_gt_gt)。

第一个成员函数确保窗体的表达式 `istr >> ws` 调用 [`ws`](../standard-library/istream-functions.md#ws) `(istr)` ，然后返回 __* this__。 第二个和第三个函数确保其他操控器（如 [`hex`](../standard-library/ios-functions.md#hex) ）的行为类似。 其余函数是格式化的输入函数。

函数：

```cpp
basic_istream& operator>>(
    basic_streambuf<Char_T, Tr>* strbuf);
```

如果*strbuf*不是空指针，则提取元素，并将其插入*strbuf*中。 提取在文件结尾停止。 如果插入失败或引发异常（可捕获异常但不会再次引发），提取也会在未提取所讨论的元素的情况下停止。 如果函数未提取任何元素，则调用 [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)` 。 在任何情况下，函数均返回 __* this__。

函数：

```cpp
basic_istream& operator>>(bool& val);
```

提取字段，并通过调用将其转换为布尔值 [`use_facet`](../standard-library/basic-filebuf-class.md#open) `< num_get<Char_T, InIt>(` [`getloc`](../standard-library/ios-base-class.md#getloc) `).` [`get`](../standard-library/ios-base-class.md#getloc) `( InIt(` [`rdbuf`](../standard-library/basic-ios-class.md#rdbuf) `), Init(0), *this, getloc, val)` 。 此处， `InIt` 定义为 [`istreambuf_iterator`](../standard-library/istreambuf-iterator-class.md) `<Char_T, Tr>` 。 该函数返回 __* this__。

每个函数：

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

提取字段，并通过调用将其转换为数值 `use_facet<num_get<Char_T, InIt>(getloc).` [`get`](#get) `(InIt(rdbuf), Init(0), *this, getloc, val)` 。 此处， `InIt` 定义为 `istreambuf_iterator<Char_T, Tr>` ，而*val*具有类型 **`long`** 、或（ **`unsigned long`** **`void`** <strong>\*</strong> 根据需要）。

如果转换后的值不能表示为*值的类型，则*函数将调用 [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)` 。 在任何情况下，函数均返回 __* this__。

每个函数：

```cpp
basic_istream& operator>>(float& val);
basic_istream& operator>>(double& val);
basic_istream& operator>>(long double& val);
```

提取字段，并通过调用将其转换为数值 `use_facet<num_get<Char_T, InIt>(getloc).get(InIt(rdbuf), Init(0), *this, getloc, val)` 。 此处， `InIt` 定义为 `istreambuf_iterator<Char_T, Tr>` ， *val*具有类型 **`double`** 或 **`long double`** 所需的类型。

如果转换后的值不能表示为*值的类型，则*函数将调用 `setstate(failbit)` 。 在任何情况下，它都会返回 __* this__。

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

## <a name="basic_istreamoperator"></a><a name="op_eq"></a>basic_istream：： operator =

将运算符右侧上的 `basic_istream` 分配给此对象。 这是涉及 `rvalue` 不会留下副本的引用的移动赋值。

```cpp
basic_istream& operator=(basic_istream&& right);
```

### <a name="parameters"></a>参数

*然后*\
对 `basic_ifstream` 对象的 `rvalue` 引用。

### <a name="return-value"></a>返回值

返回 __* this__。

### <a name="remarks"></a>备注

成员运算符调用 `swap(right)` 。

## <a name="basic_istreampeek"></a><a name="peek"></a>basic_istream：:p eek

返回要读取的下一字符。

```cpp
int_type peek();
```

### <a name="return-value"></a>返回值

要读取的下一字符。

### <a name="remarks"></a>备注

如果可能，未格式化的输入函数提取元素，就像返回一样 `rdbuf->` [`sgetc`](../standard-library/basic-streambuf-class.md#sgetc) 。 否则，它将返回 `traits_type::` [`eof`](../standard-library/char-traits-struct.md#eof) 。

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

## <a name="basic_istreamputback"></a><a name="putback"></a>basic_istream：:p utback

将指定的字符放入流。

```cpp
basic_istream<Char_T, Tr>& putback(
    char_type Ch);
```

### <a name="parameters"></a>参数

*48*\
要放回到流中的字符。

### <a name="return-value"></a>返回值

流（__* this__）。

### <a name="remarks"></a>备注

如果可能，未[格式化的输入函数](../standard-library/basic-istream-class.md)将返回*Ch*，就像调用一样 [`rdbuf`](../standard-library/basic-ios-class.md#rdbuf) `->` [`sputbackc`](../standard-library/basic-streambuf-class.md#sputbackc) 。 如果 `rdbuf` 为 null 指针，或如果对的调用 `sputbackc` 返回 `traits_type::` [`eof`](../standard-library/char-traits-struct.md#eof) ，则该函数将调用 [`setstate`](../standard-library/basic-ios-class.md#setstate) `(badbit)` 。 在任何情况下，它都会返回 __* this__。

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

## <a name="basic_istreamread"></a><a name="read"></a>basic_istream：： read

从流中读取指定数目的字符，并将其存储到数组中。

此方法可能并不安全，因为它依赖于调用方检查所传递的值是否正确。

```cpp
basic_istream<Char_T, Tr>& read(
    char_type* str,
    streamsize count);
```

### <a name="parameters"></a>参数

*字符串*\
要从中读取字符的数组。

*计*\
要读取的字符数。

### <a name="return-value"></a>返回值

流（ **`*this`** ）。

### <a name="remarks"></a>备注

未格式化的输入函数提取最多*个元素，并将它们*存储在从*str*开始的数组中。 提取在文件结尾的初期停止，在这种情况下，函数会调用 [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)` 。 在任何情况下，它都会返回 __* this__。

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

## <a name="basic_istreamreadsome"></a><a name="readsome"></a>basic_istream：： readsome

读取指定数量的字符值。

此方法可能并不安全，因为它依赖于调用方检查所传递的值是否正确。

```cpp
streamsize readsome(
    char_type* str,
    streamsize count);
```

### <a name="parameters"></a>参数

*字符串*\
`readsome` 存储它所读取字符的数组。

*计*\
要读取的字符数。

### <a name="return-value"></a>返回值

实际读取的字符数 [`gcount`](#gcount) 。

### <a name="remarks"></a>备注

此无格式的输入函数提取最多从输入流*计数*元素，并将它们存储在数组*str*中。

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

## <a name="basic_istreamseekg"></a><a name="seekg"></a>basic_istream：： seekg

在流中移动读取位置。

```cpp
basic_istream<Char_T, Tr>& seekg(pos_type pos);

basic_istream<Char_T, Tr>& seekg(off_type off, ios_base::seekdir way);
```

### <a name="parameters"></a>参数

*位置*\
要将读取指针移动到的绝对位置。

*非*\
用于相对于*方式*移动读取指针的偏移量。

*同样*\
其中一个 [ios_base::seekdir](../standard-library/ios-base-class.md#seekdir) 枚举。

### <a name="return-value"></a>返回值

流（__* this__）。

### <a name="remarks"></a>备注

第一个成员函数执行绝对查找，第二个成员函数执行相对查找。

> [!NOTE]
> 不要对文本文件使用第二个成员函数，因为标准 C++ 不支持在文本文件中进行相对查找。

如果 [`fail`](../standard-library/basic-ios-class.md#fail) 为 false，则第一个成员函数将调用 `newpos =` [`rdbuf`](../standard-library/basic-ios-class.md#rdbuf) `->` [`pubseekpos`](../standard-library/basic-streambuf-class.md#pubseekpos) `(pos)` （对于某个 `pos_type` 临时对象） `newpos` 。 如果 `fail` 为 false，则第二个函数调用 `newpos = rdbuf->` [`pubseekoff`](../standard-library/basic-streambuf-class.md#pubseekoff) `( off, way)` 。 在任一情况下，如果 `(off_type)newpos == (off_type)(-1)` （定位操作失败），该函数将调用 `istr.` [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)` 。 这两个函数都返回 __* this__。

如果 [`fail`](../standard-library/basic-ios-class.md#fail) 为 true，则成员函数不执行任何操作。

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

## <a name="basic_istreamsentry"></a><a name="sentry"></a>basic_istream：：卫士

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

如果 `_Istr.` [`good`](../standard-library/basic-ios-class.md#good) 为 true，则构造函数：

- 如果不是 `_Istr.` [`tie`](../standard-library/basic-ios-class.md#tie) `->` [`flush`](../standard-library/basic-ostream-class.md#flush) `_Istr.tie` null 指针，则调用。

- [`ws`](../standard-library/istream-functions.md#ws) `(_Istr)` 如果 `_Istr.` [`flags`](../standard-library/ios-base-class.md#flags) `&` [`skipws`](../standard-library/ios-functions.md#skipws) 为非零，则有效地调用。

如果在进行此类准备后， `_Istr.good` 将为 false，则构造函数会调用 `_Istr.` [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)` 。 在任何情况下，构造函数都会存储中返回的值 `_Istr.good` `status` 。 稍后调用 `operator bool` 传递此存储的值。

## <a name="basic_istreamswap"></a><a name="swap"></a>basic_istream：： swap

交换两个 `basic_istream` 对象的内容。

```cpp
void swap(basic_istream& right);
```

### <a name="parameters"></a>参数

*然后*\
对 `basic_istream` 对象的左值引用。

### <a name="remarks"></a>备注

成员函数调用 [`basic_ios::swap`](../standard-library/basic-ios-class.md#swap) `(right)` 。 它还会将提取计数与*右*提取计数进行交换。

## <a name="basic_istreamsync"></a><a name="sync"></a>basic_istream：： sync

将流的关联输入设备与流的缓冲区进行同步。

```cpp
int sync();
```

### <a name="return-value"></a>返回值

如果 [`rdbuf`](../standard-library/basic-ios-class.md#rdbuf) 为 null 指针，则该函数将返回-1。 否则，它会调用 `rdbuf->` [`pubsync`](../standard-library/basic-streambuf-class.md#pubsync) 。 如果该调用返回-1，则该函数将调用 [`setstate`](../standard-library/basic-ios-class.md#setstate) `(badbit)` 并返回-1。 否则，该函数返回零。

## <a name="basic_istreamtellg"></a><a name="tellg"></a>basic_istream：： tellg

报告流中的当前读取位置。

```cpp
pos_type tellg();
```

### <a name="return-value"></a>返回值

流中的当前新位置。

### <a name="remarks"></a>备注

如果 [`fail`](../standard-library/basic-ios-class.md#fail) 为 false，则成员函数返回 [`rdbuf`](../standard-library/basic-ios-class.md#rdbuf) `->` [`pubseekoff`](../standard-library/basic-streambuf-class.md#pubseekoff) `(0, cur, in)` 。 否则，将返回 `pos_type(-1)`。

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

## <a name="basic_istreamunget"></a><a name="unget"></a>basic_istream：： unget

将最近读取的字符放回流中。

```cpp
basic_istream<Char_T, Tr>& unget();
```

### <a name="return-value"></a>返回值

流（__* this__）。

### <a name="remarks"></a>备注

未[格式化的输入函数](../standard-library/basic-istream-class.md)将返回流中的上一个元素（如果可能），就像调用一样 `rdbuf->` [`sungetc`](../standard-library/basic-streambuf-class.md#sungetc) 。 如果 [`rdbuf`](../standard-library/basic-ios-class.md#rdbuf) 为 null 指针，或如果对的调用 `sungetc` 返回 `traits_type::` [`eof`](../standard-library/basic-ios-class.md#eof) ，则该函数将调用 [`setstate`](../standard-library/basic-ios-class.md#setstate) `(badbit)` 。 在任何情况下，它都会返回 __* this__。

有关可能失败的详细信息 `unget` ，请参阅 [`basic_streambuf::sungetc`](../standard-library/basic-streambuf-class.md#sungetc) 。

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

[C + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 编程](../standard-library/iostream-programming.md)\
[iostreams 约定](../standard-library/iostreams-conventions.md)

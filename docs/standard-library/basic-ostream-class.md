---
title: basic_ostream 类
ms.date: 03/27/2019
f1_keywords:
- ostream/std::basic_ostream
- ostream/std::basic_ostream::flush
- ostream/std::basic_ostream::put
- ostream/std::basic_ostream::seekp
- ostream/std::basic_ostream::sentry
- ostream/std::basic_ostream::swap
- ostream/std::basic_ostream::tellp
- ostream/std::basic_ostream::write
helpviewer_keywords:
- std::basic_ostream [C++]
- std::basic_ostream [C++], flush
- std::basic_ostream [C++], put
- std::basic_ostream [C++], seekp
- std::basic_ostream [C++], sentry
- std::basic_ostream [C++], swap
- std::basic_ostream [C++], tellp
- std::basic_ostream [C++], write
ms.assetid: 5baadc65-b662-4fab-8c9f-94457c58cda1
ms.openlocfilehash: 9025d595e79eed9f81aff77b931a2585359a8c3a
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79427241"
---
# <a name="basic_ostream-class"></a>basic_ostream 类

此类模板描述了一个对象，该对象可控制将元素和编码对象插入流缓冲区中的 `Elem`元素，并将其字符特征由类 `Tr`确定，也称为[char_type](../standard-library/basic-ios-class.md#char_type)，其字符特征由类确定，也称为[traits_type](../standard-library/basic-ios-class.md#traits_type)。

## <a name="syntax"></a>语法

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_ostream : virtual public basic_ios<Elem, Tr>
```

### <a name="parameters"></a>parameters

*Elem*\
一个 `char_type`。

*Tr*\
字符 `traits_type`。

## <a name="remarks"></a>备注

重载 [operator<<](#basic_ostream_operator_lt_lt) 的大部分成员函数是格式化的输出函数。 它们遵循以下模式：

```cpp
iostate state = goodbit;
const sentry ok(*this);

if (ok)
{try
{<convert and insert elements
    accumulate flags in state> }
    catch (...)
{try
{setstate(badbit);

}
    catch (...)
{}
    if ((exceptions()& badbit) != 0)
    throw; }}
width(0);
// Except for operator<<(Elem)
setstate(state);

return (*this);
```

两个其他成员函数是未格式化的输出函数。 它们遵循以下模式：

```cpp
iostate state = goodbit;
const sentry ok(*this);

if (!ok)
    state |= badbit;
else
{try
{<obtain and insert elements
    accumulate flags in state> }
    catch (...)
{try
{setstate(badbit);

}
    catch (...)
{}
    if ((exceptions()& badbit) != 0)
    throw; }}
setstate(state);

return (*this);
```

如果两组函数在插入元素时遇到失败，则会调用[setstate](../standard-library/basic-ios-class.md#setstate)（**badbit**）。

类的对象 basic_istream\< **Elem**， **tr**> 只存储类[basic_ios](../standard-library/basic-ios-class.md) **\<Elem**， **tr >** 的虚拟公共基对象。

## <a name="example"></a>示例

请参阅 [basic_ofstream 类](../standard-library/basic-ofstream-class.md)的示例，了解有关输出流的详细信息。

### <a name="constructors"></a>构造函数

|构造函数|说明|
|-|-|
|[basic_ostream](#basic_ostream)|构造 `basic_ostream` 对象。|

### <a name="member-functions"></a>成员函数

|成员函数|说明|
|-|-|
|[flush](#flush)|刷新缓冲区。|
|[put](#put)|将字符放入流中。|
|[seekp](#seekp)|重置在输出流中的位置。|
|[sentry](#sentry)|嵌套的类描述一个对象，该对象的声明构造格式化的输出函数和未格式化的输出函数。|
|[swap](#swap)|将此 `basic_ostream` 对象的值与提供的 `basic_ostream` 对象的值进行交换。|
|[tellp](#tellp)|报告在输出流中的位置。|
|[write](#write)|将字符放入流中。|

### <a name="operators"></a>运算符

|操作员|说明|
|-|-|
|[operator=](#op_eq)|将提供的 `basic_ostream` 对象参数的值赋给此对象。|
|[operator<<](#basic_ostream_operator_lt_lt)|写入流。|

## <a name="requirements"></a>要求

**标头：** \<ostream >

**命名空间：** std

## <a name="basic_ostream"></a>  basic_ostream::basic_ostream

构造 `basic_ostream` 对象。

```cpp
explicit basic_ostream(
    basic_streambuf<Elem, Tr>* strbuf,
    bool _Isstd = false);

basic_ostream(basic_ostream&& right);
```

### <a name="parameters"></a>parameters

*strbuf*\
类型 [basic_streambuf](../standard-library/basic-streambuf-class.md) 的对象。

*_Isstd*\
如果这是标准流，**则为 true** ;否则**为 false**。

*right*\
对 `basic_ostream` 类型的对象的右值引用。

### <a name="remarks"></a>备注

第一个构造函数通过调用 [init](../standard-library/basic-ios-class.md#init)(`strbuf`) 初始化基类。 第二个构造函数通过调用 [basic_ios::move](../standard-library/basic-ios-class.md#move)`(right)` 初始化基类。

### <a name="example"></a>示例

请参阅 [basic_ofstream::basic_ofstream](../standard-library/basic-ofstream-class.md#basic_ofstream) 的示例，了解有关输出流的详细信息。

## <a name="flush"></a>  basic_ostream::flush

刷新缓冲区。

```cpp
basic_ostream<Elem, Tr>& flush();
```

### <a name="return-value"></a>返回值

对 Basic_ostream 对象的引用。

### <a name="remarks"></a>备注

如果 [rdbuf](../standard-library/basic-ios-class.md#rdbuf) 不是空指针，则函数将调用 **rdbuf->** [pubsync](../standard-library/basic-streambuf-class.md#pubsync)。 如果返回 -1，则该函数将调用 [setstate](../standard-library/basic-ios-class.md#setstate)(**badbit**)。 它将返回 **\*this**。

### <a name="example"></a>示例

```cpp
// basic_ostream_flush.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   cout << "test";
   cout.flush();
}
```

```Output
test
```

## <a name="basic_ostream_operator_lt_lt"></a>basic_ostream::operator&lt;&lt;

写入流。

```cpp
basic_ostream<Elem, Tr>& operator<<(
    basic_ostream<Elem, Tr>& (* Pfn)(basic_ostream<Elem, Tr>&));

basic_ostream<Elem, Tr>& operator<<(
    ios_base& (* Pfn)(ios_base&));

basic_ostream<Elem, Tr>& operator<<(
    basic_ios<Elem, Tr>& (* Pfn)(basic_ios<Elem, Tr>&));

basic_ostream<Elem, Tr>& operator<<(basic_streambuf<Elem, Tr>* strbuf);
basic_ostream<Elem, Tr>& operator<<(bool val);
basic_ostream<Elem, Tr>& operator<<(short val);
basic_ostream<Elem, Tr>& operator<<(unsigned short val);
basic_ostream<Elem, Tr>& operator<<(int __w64  val);
basic_ostream<Elem, Tr>& operator<<(unsigned int __w64  val);
basic_ostream<Elem, Tr>& operator<<(long val);
basic_ostream<Elem, Tr>& operator<<(unsigned long __w64  val);
basic_ostream<Elem, Tr>& operator<<(long long val);
basic_ostream<Elem, Tr>& operator<<(unsigned long long val);
basic_ostream<Elem, Tr>& operator<<(float val);
basic_ostream<Elem, Tr>& operator<<(double val);
basic_ostream<Elem, Tr>& operator<<(long double val);
basic_ostream<Elem, Tr>& operator<<(const void* val);
```

### <a name="parameters"></a>parameters

*Pfn*\
函数指针。

*strbuf*\
一个指向 `stream_buf` 对象的指针。

*val*\
要写入到流的元素。

### <a name="return-value"></a>返回值

对 Basic_ostream 对象的引用。

### <a name="remarks"></a>备注

\<ostream > 标头还定义了多个全局插入运算符。 有关详细信息，请参阅[operator < <](../standard-library/ostream-operators.md#op_lt_lt)。

第一个成员函数确保 `ostr << endl` 形式的表达式调用[endl](../standard-library/ostream-functions.md#endl) **（ostr）** ，然后返回 **\*this**。 第二个和第三个函数确保其他操控器（如 [hex ](../standard-library/ios-functions.md#hex)）表现相似。 其余函数均是格式化的输出函数。

函数

```cpp
basic_ostream<Elem, Tr>& operator<<(basic_streambuf<Elem, Tr>* strbuf);
```

如果*strbuf*不是 null 指针，则从*strbuf*中提取元素并插入它们。 提取会在文件结尾停止，或者如果提取引发异常（为重新引发的异常），则提取也会停止。 如果插入失败，则也会在尚未提取所讨论元素的情况下导致提取停止。 如果该函数没有插入任何元素，或者如果提取引发异常，则函数调用 [setstate](../standard-library/basic-ios-class.md#setstate)(**failbit**)。 不管怎样，该函数均将返回 **\*this**。

函数

```cpp
basic_ostream<Elem, Tr>& operator<<(bool val);
```

将 `_Val` 转换为布尔字段，并通过调用[use_facet](../standard-library/basic-filebuf-class.md#open) **< num_put\<Elem，OutIt >** `(`[getloc](../standard-library/ios-base-class.md#getloc)）来插入该字段。 [put](#put)(**OutIt**([rdbuf](../standard-library/basic-ios-class.md#rdbuf)), **\*this**, `getloc`, **val**) 插入它。 此处，`OutIt` 定义为[ostreambuf_iterator](../standard-library/ostreambuf-iterator-class.md) **\<Elem、Tr >** 。 该函数返回 **\*this**。

函数

```cpp
basic_ostream<Elem, Tr>& operator<<(short val);
basic_ostream<Elem, Tr>& operator<<(unsigned short val);
basic_ostream<Elem, Tr>& operator<<(int val);
basic_ostream<Elem, Tr>& operator<<(unsigned int __w64  val);
basic_ostream<Elem, Tr>& operator<<(long val);
basic_ostream<Elem, Tr>& operator<<(unsigned long val);
basic_ostream<Elem, Tr>& operator<<(long long val);
basic_ostream<Elem, Tr>& operator<<(unsigned long long val);
basic_ostream<Elem, Tr>& operator<<(const void* val);
```

每个将*val*转换为数值字段，并通过调用**use_facet < num_put\<Elem，OutIt >** （`getloc`）来插入。 **put**(**OutIt**(`rdbuf`), **\*this**, `getloc`, **val**) 插入它。 此处，将 **OutIt** 定义为 **ostreambuf_iterator\<Elem, Tr>** 。 该函数返回 **\*this**。

函数

```cpp
basic_ostream<Elem, Tr>& operator<<(float val);
basic_ostream<Elem, Tr>& operator<<(double val);
basic_ostream<Elem, Tr>& operator<<(long double val);
```

每**val**个将*val*转换为数值字段，并通过调用**use_facet < num_put\<Elem，OutIt >** （`getloc`） **，** 将其**OutIt**插入。 **\*this**`rdbuf``getloc` 此处，将 **OutIt** 定义为 **ostreambuf_iterator\<Elem, Tr>** 。 该函数返回 **\*this**。

### <a name="example"></a>示例

```cpp
// basic_ostream_op_write.cpp
// compile with: /EHsc
#include <iostream>
#include <string.h>

using namespace std;

ios_base& hex2( ios_base& ib )
{
   ib.unsetf( ios_base::dec );
   ib.setf( ios_base::hex );
   return ib;
}

basic_ostream<char, char_traits<char> >& somefunc(basic_ostream<char, char_traits<char> > &i)
{
    if (i == cout)
    {
        i << "i is cout" << endl;
    }
    return i;
}

class CTxtStreambuf : public basic_streambuf< char, char_traits< char > >
{
public:
    CTxtStreambuf(char *_pszText)
    {
        pszText = _pszText;
        setg(pszText, pszText, pszText + strlen(pszText));
    };
    char *pszText;
};

int main()
{
    cout << somefunc;
    cout << 21 << endl;

    hex2(cout);
    cout << 21 << endl;

    CTxtStreambuf f("text in streambuf");
    cout << &f << endl;
}
```

## <a name="op_eq"></a>  basic_ostream::operator=

将提供的 `basic_ostream` 对象参数的值赋给此对象。

```cpp
basic_ostream& operator=(basic_ostream&& right);
```

### <a name="parameters"></a>parameters

*right*\
对 `rvalue` 对象的 `basic_ostream` 引用。

### <a name="remarks"></a>备注

成员运算符调用 swap `(right)`。

## <a name="put"></a>  basic_ostream::put

将字符放入流中。

```cpp
basic_ostream<Elem, Tr>& put(char_type _Ch);
```

### <a name="parameters"></a>parameters

*_Ch*\
一个字符。

### <a name="return-value"></a>返回值

对 Basic_ostream 对象的引用。

### <a name="remarks"></a>备注

未格式化的输出函数将 *_Ch*中插入元素。 它将返回 **\*this**。

### <a name="example"></a>示例

```cpp
// basic_ostream_put.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   cout.put( 'v' );
   cout << endl;
   wcout.put( L'l' );
}
```

```Output
v
l
```

## <a name="seekp"></a>  basic_ostream::seekp

重置输出流中的位置。

```cpp
basic_ostream<Elem, Tr>& seekp(pos_type _Pos);

basic_ostream<Elem, Tr>& seekp(off_type _Off, ios_base::seekdir _Way);
```

### <a name="parameters"></a>parameters

*_Pos*\
流中的位置。

*_Off*\
相对于 *_Way*的偏移量。

*_Way*\
其中一个 [ios_base::seekdir](../standard-library/ios-base-class.md#seekdir) 枚举。

### <a name="return-value"></a>返回值

对 Basic_ostream 对象的引用。

### <a name="remarks"></a>备注

如果[fail](../standard-library/basic-ios-class.md#fail)为**false**，则第一个成员函数将调用**newpos =** [rdbuf](../standard-library/basic-ios-class.md#rdbuf) **->** [pubseekpos](../standard-library/basic-streambuf-class.md#pubseekpos)（ *_Pos*），`pos_type` 临时对象 `newpos`。 如果 `fail` 为 false，则第二个函数调用**newpos = > rdbuf** [pubseekoff](../standard-library/basic-streambuf-class.md#pubseekoff)（ *_Off，_Way*）。 在任一情况下，如果 (`off_type`)**newpos ==** (`off_type`)(-1)（定位操作失败），则函数调用 **istr.** [setstate](../standard-library/basic-ios-class.md#setstate)(**failbit**)。 两个函数均返回 **\*this**。

### <a name="example"></a>示例

```cpp
// basic_ostream_seekp.cpp
// compile with: /EHsc
#include <fstream>
#include <iostream>

int main()
{
    using namespace std;
    ofstream x("basic_ostream_seekp.txt");
    streamoff i = x.tellp();
    cout << i << endl;
    x << "testing";
    i = x.tellp();
    cout << i << endl;
    x.seekp(2);   // Put char in third char position in file
    x << " ";

    x.seekp(2, ios::end);   // Put char two after end of file
    x << "z";
}
```

```Output
0
7
```

## <a name="sentry"></a>  basic_ostream::sentry

嵌套的类描述一个对象，该对象的声明构造格式化的输出函数和未格式化的输出函数。

类卫士 {public： explicit 卫士（basic_ostream\<Elem，Tr > & _Ostr）; operator bool （） const; ~ 卫士（）;};

### <a name="remarks"></a>备注

嵌套的类描述一个对象，该对象的声明构造格式化的输出函数和未格式化的输出函数。 如果 **ostr.** [good](../standard-library/basic-ios-class.md#good) 为 **true** 且 **ostr.** [tie](../standard-library/basic-ios-class.md#tie) 不是空指针，则构造函数调用 **ostr.tie->** [flush](#flush)。 然后，构造函数将 `ostr.good` 返回的值存储在 `status`中。 稍后对 `operator bool` 的调用会传递此存储的值。

如果 `uncaught_exception` 返回**false** ，并且[标志](../standard-library/ios-base-class.md#flags) **&** [unitbuf](../standard-library/ios-functions.md#unitbuf)为非零，则析构函数调用[flush](#flush)。

## <a name="swap"></a>  basic_ostream::swap

将此 `basic_ostream` 对象的值与提供的 `basic_ostream` 的值进行交换。

```cpp
void swap(basic_ostream& right);
```

### <a name="parameters"></a>parameters

*right*\
对 `basic_ostream` 对象的引用。

### <a name="remarks"></a>备注

成员函数调用[basic_ios：： swap](../standard-library/basic-ios-class.md#swap)`(right)` 将此对象的内容与*右侧*的内容交换。

## <a name="tellp"></a>  basic_ostream::tellp

报告输出流中的位置。

```cpp
pos_type tellp();
```

### <a name="return-value"></a>返回值

输出流中的位置。

### <a name="remarks"></a>备注

如果[fail](../standard-library/basic-ios-class.md#fail)为**false**，则成员函数将返回[rdbuf](../standard-library/basic-ios-class.md#rdbuf) **->** [pubseekoff](../standard-library/basic-streambuf-class.md#pubseekoff)（0，`cur`，**在中**）。 否则，将返回 `pos_type`(-1)。

### <a name="example"></a>示例

有关使用 [ 的示例，请参阅 ](#seekp)seekp`tellp`。

## <a name="write"></a>  basic_ostream::write

将字符放入流中。

```cpp
basic_ostream<Elem, Tr>& write(const char_type* str, streamsize count);
```

### <a name="parameters"></a>parameters

*计数*\
要放入流中的字符计数。

*str*\
要放入流中的字符。

### <a name="return-value"></a>返回值

对 Basic_ostream 对象的引用。

### <a name="remarks"></a>备注

未[格式化的输出函数](../standard-library/basic-ostream-class.md)插入从*str*开始的*计数*元素的序列。

### <a name="example"></a>示例

有关使用 [ 的示例，请参阅 ](../standard-library/ios-typedefs.md#streamsize)streamsize`write`。

## <a name="see-also"></a>另请参阅

[C++ 标准库中的线程安全性](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 编程](../standard-library/iostream-programming.md)\
[iostreams 约定](../standard-library/iostreams-conventions.md)

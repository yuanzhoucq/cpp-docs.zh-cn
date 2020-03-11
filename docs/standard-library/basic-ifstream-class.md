---
title: basic_ifstream 类
ms.date: 11/04/2016
f1_keywords:
- fstream/std::basic_ifstream
- fstream/std::basic_ifstream::close
- fstream/std::basic_ifstream::is_open
- fstream/std::basic_ifstream::open
- fstream/std::basic_ifstream::rdbuf
- fstream/std::basic_ifstream::swap
helpviewer_keywords:
- std::basic_ifstream [C++]
- std::basic_ifstream [C++], close
- std::basic_ifstream [C++], is_open
- std::basic_ifstream [C++], open
- std::basic_ifstream [C++], rdbuf
- std::basic_ifstream [C++], swap
ms.assetid: 366cd9a7-efc4-4b7f-ba10-c8271e47ffcf
ms.openlocfilehash: 1e5e22c837ca2d6389591cec6d2cdd256ca50b1a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865856"
---
# <a name="basic_ifstream-class"></a>basic_ifstream 类

描述一个对象，该对象可控制从 [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`> 类的流缓冲区提取元素和编码对象，其中 `Elem` 类型的元素的字符特征由 `Tr` 类确定。

## <a name="syntax"></a>语法

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_ifstream : public basic_istream<Elem, Tr>
```

### <a name="parameters"></a>参数

*Elem*\
文件缓冲区的基本元素。

*Tr*\
文件缓冲区的基本元素的特征（通常是 `char_traits`< `Elem`>）。

## <a name="remarks"></a>备注

该对象存储 `basic_filebuf`< `Elem`, `Tr`> 类的对象。

## <a name="example"></a>示例

下面的示例说明了如何读取文件中的文本。

```cpp
// basic_ifstream_class.cpp
// compile with: /EHsc

#include <fstream>
#include <iostream>

using namespace std;

int main(int argc, char **argv)
{
    ifstream ifs("basic_ifstream_class.txt");
    if (!ifs.bad())
    {
        // Dump the contents of the file to cout.
        cout << ifs.rdbuf();
        ifs.close();
    }
}
```

## <a name="input-basic_ifstream_classtxt"></a>Input: basic_ifstream_class.txt

```cpp
This is the contents of basic_ifstream_class.txt.
```

## <a name="output"></a>输出

```cpp
This is the contents of basic_ifstream_class.txt.
```

### <a name="constructors"></a>构造函数

|构造函数|描述|
|-|-|
|[basic_ifstream](#basic_ifstream)|初始化 `basic_ifstream` 对象的新实例。|

### <a name="member-functions"></a>成员函数

|成员函数|描述|
|-|-|
|[close](#close)|关闭文件。|
|[is_open](#is_open)|确定文件是否打开。|
|[open](#open)|打开文件。|
|[rdbuf](#rdbuf)|返回存储的流缓冲区的地址。|
|[swap](#swap)|为所提供 `basic_ifstream` 的内容交换此 `basic_ifstream` 的内容。|

### <a name="operators"></a>运算符

|Operator|描述|
|-|-|
|[operator=](#op_eq)|分配此流对象的内容。 这是一种移动赋值，所涉及的 `rvalue` 不会留下副本。|

## <a name="requirements"></a>要求

**标头：** \<m >

**命名空间：** std

## <a name="basic_ifstream"></a>  basic_ifstream::basic_ifstream

构造 `basic_ifstream` 类型的对象。

```cpp
basic_ifstream();

explicit basic_ifstream(
    const char* _Filename,
    ios_base::openmode _Mode = ios_base::in,
    int _Prot = (int)ios_base::_Openprot);

explicit basic_ifstream(
    const wchar_t* _Filename,
    ios_base::openmode _Mode = ios_base::in,
    int _Prot = (int)ios_base::_Openprot);

basic_ifstream(basic_ifstream&& right);
```

### <a name="parameters"></a>参数

*_Filename*\
要打开的文件的名称。

*_Mode*\
[ios_base::openmode](../standard-library/ios-base-class.md#openmode) 中的枚举之一。

*_Prot*\
默认文件打开保护，等同于 [_fsopen、_wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md) 中的 `shflag` 参数。

### <a name="remarks"></a>备注

第一个构造函数通过调用 [basic_istream](../standard-library/basic-istream-class.md)(`sb`) 初始化基类，其中 `sb` 是 [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`> 类的存储对象。 通过调用 `basic_filebuf`< `Elem`, `Tr`>，它还可以初始化 `sb`。

通过调用 `basic_istream`(`sb`)，第二个和第三个构造函数可初始化基类。 通过调用 [basic_filebuf](../standard-library/basic-filebuf-class.md#basic_filebuf)< `Elem`, `Tr`>，然后调用 `sb`，它还可以初始化 `sb`。 [open](../standard-library/basic-filebuf-class.md#open)( `_Filename`, `_Mode` &#124; `ios_base::in`)。 如果后一个函数返回一个空指针，构造函数将调用 **setstate**( `failbit`)。

第四个构造函数初始化具有 `right` 的内容的对象，将其视为右值引用。

### <a name="example"></a>示例

下面的示例说明了如何读取文件中的文本。 若要创建文件，请参阅 [basic_ofstream:: basic_ofstream](../standard-library/basic-ofstream-class.md#basic_ofstream) 的示例。

```cpp
// basic_ifstream_ctor.cpp
// compile with: /EHsc

#include <fstream>
#include <iostream>

using namespace std;

int main(int argc, char **argv)
{
    ifstream ifs("basic_ifstream_ctor.txt");
    if (!ifs.bad())
    {
        // Dump the contents of the file to cout.
        cout << ifs.rdbuf();
        ifs.close();
    }
}
```

## <a name="close"></a>  basic_ifstream::close

关闭文件。

```cpp
void close();
```

### <a name="remarks"></a>备注

此成员函数调用[rdbuf](#rdbuf) **->** [close](../standard-library/basic-filebuf-class.md#close)。

### <a name="example"></a>示例

有关如何使用 `close` 的示例，请参阅 [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close)。

## <a name="is_open"></a>  basic_ifstream::is_open

确定文件是否打开。

```cpp
bool is_open() const;
```

### <a name="return-value"></a>返回值

如果文件处于打开状态，则为 **true**，否则为 **false**。

### <a name="remarks"></a>备注

此成员函数返回[rdbuf](#rdbuf) **->** [is_open](../standard-library/basic-filebuf-class.md#is_open)。

### <a name="example"></a>示例

有关如何使用 `is_open` 的示例，请参阅 [basic_filebuf::is_open](../standard-library/basic-filebuf-class.md#is_open)。

## <a name="open"></a>  basic_ifstream::open

打开文件。

```cpp
void open(
    const char* _Filename,
    ios_base::openmode _Mode = ios_base::in,
    int _Prot = (int)ios_base::_Openprot);

void open(
    const char* _Filename,
    ios_base::openmode _Mode);

void open(
    const wchar_t* _Filename,
    ios_base::openmode _Mode = ios_base::in,
    int _Prot = (int)ios_base::_Openprot);

void open(
    const wchar_t* _Filename,
    ios_base::openmode _Mode);
```

### <a name="parameters"></a>参数

*_Filename*\
要打开的文件的名称。

*_Mode*\
[ios_base::openmode](../standard-library/ios-base-class.md#openmode) 中的枚举之一。

*_Prot*\
默认文件打开保护，等同于 [_fsopen、_wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md) 中的 `shflag` 参数。

### <a name="remarks"></a>备注

此成员函数调用[rdbuf](#rdbuf) **->** [open](../standard-library/basic-filebuf-class.md#open)（_ *Filename*，`_Mode` &#124; **ios_base：： in**）。 如果打开失败，该函数将调用 [setstate](../standard-library/basic-ios-class.md#setstate)（`failbit`），这可能会引发 ios_base：：失败异常。

### <a name="example"></a>示例

有关使用 `open`的示例，请参阅[basic_filebuf：： open](../standard-library/basic-filebuf-class.md#open) 。

## <a name="op_eq"></a>  basic_ifstream::operator=

分配此流对象的内容。 这是一种移动赋值，所涉右值不会留下副本。

```cpp
basic_ifstream& operator=(basic_ifstream&& right);
```

### <a name="parameters"></a>参数

*right*\
对 `basic_ifstream` 对象的右值引用。

### <a name="return-value"></a>返回值

返回 `*this`。

### <a name="remarks"></a>备注

成员运算符使用*right*的内容替换对象的内容，并将其视为右值引用。 有关详细信息，请参阅[左值和右值](../cpp/lvalues-and-rvalues-visual-cpp.md)。

## <a name="rdbuf"></a>  basic_ifstream::rdbuf

返回存储的流缓冲区的地址。

```cpp
basic_filebuf<Elem, Tr> *rdbuf() const
```

### <a name="return-value"></a>返回值

指向表示已存储的流缓冲区的 [basic_filebuf](../standard-library/basic-filebuf-class.md) 对象的指针。

### <a name="example"></a>示例

有关如何使用 `rdbuf` 的示例，请参阅 [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close)。

## <a name="swap"></a>  basic_ifstream::swap

交换两个 `basic_ifstream` 对象的内容。

```cpp
void swap(basic_ifstream& right);
```

### <a name="parameters"></a>参数

*right*\
对另一个流缓冲区的引用。

### <a name="remarks"></a>备注

该成员函数将此对象的内容与*右侧*的内容进行交换。

## <a name="see-also"></a>请参阅

[C++ 标准库中的线程安全性](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 编程](../standard-library/iostream-programming.md)\
[iostreams 约定](../standard-library/iostreams-conventions.md)

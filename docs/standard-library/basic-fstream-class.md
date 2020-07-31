---
title: basic_fstream 类
ms.date: 11/04/2016
f1_keywords:
- fstream/std::basic_fstream
- fstream/std::basic_fstream::close
- fstream/std::basic_fstream::is_open
- fstream/std::basic_fstream::open
- fstream/std::basic_fstream::rdbuf
- fstream/std::basic_fstream::swap
helpviewer_keywords:
- std::basic_fstream [C++]
- std::basic_fstream [C++], close
- std::basic_fstream [C++], is_open
- std::basic_fstream [C++], open
- std::basic_fstream [C++], rdbuf
- std::basic_fstream [C++], swap
ms.assetid: 8473817e-42a4-430b-82b8-b476c86bcf8a
ms.openlocfilehash: a2b62b85953a5f4ec829053c8af93582eec76618
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219295"
---
# <a name="basic_fstream-class"></a>basic_fstream 类

描述一个对象，该对象使用类[basic_filebuf](../standard-library/basic-filebuf-class.md)> 的流缓冲区控制元素和编码对象的插入和提取，该流缓冲区 <  `Elem` `Tr` 具有类型的元素 `Elem` ，其字符特征由类确定 `Tr` 。

## <a name="syntax"></a>语法

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_fstream : public basic_iostream<Elem, Tr>
```

### <a name="parameters"></a>参数

*Elem*\
文件缓冲区的基本元素。

*Tr*\
文件缓冲区的基本元素的特征（通常是 `char_traits`< `Elem`>）。

## <a name="remarks"></a>备注

该对象存储 `basic_filebuf`< `Elem`, `Tr`> 类的对象。

> [!NOTE]
> fstream 对象的 get 指针和 put 指针**不**相互独立。 如果 get 指针移动，put 指针也将移动。

## <a name="example"></a>示例

下面的示例演示如何创建能够对其进行读取和写入的 `basic_fstream` 对象。

```cpp
// basic_fstream_class.cpp
// compile with: /EHsc

#include <fstream>
#include <iostream>

using namespace std;

int main(int argc, char **argv)
{
    fstream fs("fstream.txt", ios::in | ios::out | ios::trunc);
    if (!fs.bad())
    {
        // Write to the file.
        fs << "Writing to a basic_fstream object..." << endl;
        fs.close();

        // Dump the contents of the file to cout.
        fs.open("fstream.txt", ios::in);
        cout << fs.rdbuf();
        fs.close();
    }
}
```

```Output
Writing to a basic_fstream object...
```

### <a name="constructors"></a>构造函数

|构造函数|描述|
|-|-|
|[basic_fstream](#basic_fstream)|构造 `basic_fstream` 类型的对象。|

### <a name="member-functions"></a>成员函数

|成员函数|说明|
|-|-|
|[封闭](#close)|关闭文件。|
|[is_open](#is_open)|确定文件是否打开。|
|[open](#open)|打开文件。|
|[rdbuf](#rdbuf)|返回存储流缓冲区的地址，该地址为指向[basic_filebuf](../standard-library/basic-filebuf-class.md)的类型指针 <  `Elem` `Tr`>。|
|[swap](#swap)|将此对象的内容与另一个 `basic_fstream` 对象的内容进行交换。|

## <a name="requirements"></a>要求

**标头：**\<fstream>

**命名空间:** std

## <a name="basic_fstreambasic_fstream"></a><a name="basic_fstream"></a>basic_fstream：： basic_fstream

构造 `basic_fstream` 类型的对象。

```cpp
basic_fstream();

explicit basic_fstream(
    const char* _Filename,
    ios_base::openmode _Mode = ios_base::in | ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

explicit basic_fstream(
    const wchar_t* _Filename,
    ios_base::openmode _Mode = ios_base::in | ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

basic_fstream(basic_fstream&& right);
```

### <a name="parameters"></a>参数

*_Filename*\
要打开的文件的名称。

*_Mode*\
[ios_base::openmode](../standard-library/ios-base-class.md#openmode) 中的枚举之一。

*_Prot*\
默认的文件打开保护，等效于[_fsopen _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)中的*shflag*参数。

### <a name="remarks"></a>备注

第一个构造函数通过调用[basic_iostream](../standard-library/basic-iostream-class.md)（）初始化基类 `sb` ，其中 `sb` 是[basic_filebuf](../standard-library/basic-filebuf-class.md)类的存储对象 \< **Elem**, **Tr**> 。 它还 `sb` 通过调用来进行初始化 `basic_filebuf` \< **Elem**, **Tr**> 。

通过调用 `basic_iostream`( **sb**)，第二个和第三个构造函数可初始化基类。 它还 `sb` 通过调用 `basic_filebuf` \< **Elem**, **Tr**> （_ *Filename*， **sb.**[open](../standard-library/basic-filebuf-class.md#open)）来进行初始化 `_Mode` 。 如果后一个函数返回一个空指针，则构造函数将调用[setstate](../standard-library/basic-ios-class.md#setstate)（ `failbit` ）。

第四个构造函数初始化具有 `right` 的内容的对象，将其视为右值引用。

### <a name="example"></a>示例

有关使用 `basic_fstream` 的示例，请参阅 [streampos](../standard-library/ios-typedefs.md#streampos)。

## <a name="basic_fstreamclose"></a><a name="close"></a>basic_fstream：： close

关闭文件。

```cpp
void close();
```

### <a name="remarks"></a>备注

此成员函数调用[rdbuf](#rdbuf) **->** [close](../standard-library/basic-filebuf-class.md#close)。

### <a name="example"></a>示例

有关如何使用 `close` 的示例，请参阅 [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close)。

## <a name="basic_fstreamis_open"></a><a name="is_open"></a>basic_fstream：： is_open

确定文件是否打开。

```cpp
bool is_open() const;
```

### <a name="return-value"></a>返回值

**`true`** 如果文件已打开，则 **`false`** 为; 否则为。

### <a name="remarks"></a>备注

此成员函数返回[rdbuf](#rdbuf) **->** [is_open](../standard-library/basic-filebuf-class.md#is_open)。

### <a name="example"></a>示例

有关如何使用 `is_open` 的示例，请参阅 [basic_filebuf:: is_open](../standard-library/basic-filebuf-class.md#is_open)。

## <a name="basic_fstreamopen"></a><a name="open"></a>basic_fstream：： open

打开文件。

```cpp
void open(
    const char* _Filename,
    ios_base::openmode _Mode = ios_base::in | ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

void open(
    const char* _Filename,
    ios_base::openmode _Mode);

void open(
    const wchar_t* _Filename,
    ios_base::openmode _Mode = ios_base::in | ios_base::out,
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
默认的文件打开保护，等效于[_fsopen _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)中的*shflag*参数。

### <a name="remarks"></a>备注

此成员函数调用[rdbuf](#rdbuf) **->** [open](../standard-library/basic-filebuf-class.md#open)（_ *Filename*， `_Mode` ）。 如果该函数返回 null 指针，该函数将调用[setstate](../standard-library/basic-ios-class.md#setstate)（ `failbit` ）。

### <a name="example"></a>示例

有关如何使用的示例，请参阅[basic_filebuf：： open](../standard-library/basic-filebuf-class.md#open) `open` 。

## <a name="basic_fstreamoperator"></a><a name="op_eq"></a>basic_fstream：： operator =

从指定的流对象向该对象分配内容。 这是涉及不会留下副本的右值的移动赋值运算符。

```cpp
basic_fstream& operator=(basic_fstream&& right);
```

### <a name="parameters"></a>参数

*然后*\
对 `basic_fstream` 对象的左值引用。

### <a name="return-value"></a>返回值

返回 **`*this`** 。

### <a name="remarks"></a>备注

成员运算符使用*right*的内容替换对象的内容，并将其视为右值引用。

## <a name="basic_fstreamrdbuf"></a><a name="rdbuf"></a>basic_fstream：： rdbuf

返回存储的流缓冲区的地址，其类型指针指向[basic_filebuf](../standard-library/basic-filebuf-class.md) \< **Elem**, **Tr**> 。

```cpp
basic_filebuf<Elem, Tr> *rdbuf() const
```

### <a name="return-value"></a>返回值

已存储流缓冲区的地址。

### <a name="example"></a>示例

有关如何使用 `rdbuf` 的示例，请参阅 [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close)。

## <a name="basic_fstreamswap"></a><a name="swap"></a>basic_fstream：： swap

交换两个 `basic_fstream` 对象的内容。

```cpp
void swap(basic_fstream& right);
```

### <a name="parameters"></a>参数

*然后*\
对 `basic_fstream` 对象的 `lvalue` 引用。

### <a name="remarks"></a>备注

该成员函数将交换此对象的内容和*右侧*的内容。

## <a name="see-also"></a>另请参阅

[C + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 编程](../standard-library/iostream-programming.md)\
[iostreams 约定](../standard-library/iostreams-conventions.md)

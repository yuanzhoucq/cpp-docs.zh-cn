---
title: basic_fstream 类 | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- fstream/std::basic_fstream
- fstream/std::basic_fstream::close
- fstream/std::basic_fstream::is_open
- fstream/std::basic_fstream::open
- fstream/std::basic_fstream::rdbuf
- fstream/std::basic_fstream::swap
dev_langs:
- C++
helpviewer_keywords:
- std::basic_fstream [C++]
- std::basic_fstream [C++], close
- std::basic_fstream [C++], is_open
- std::basic_fstream [C++], open
- std::basic_fstream [C++], rdbuf
- std::basic_fstream [C++], swap
ms.assetid: 8473817e-42a4-430b-82b8-b476c86bcf8a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 832a7b8f864dc21214d3b2428f83fd0c68330ff9
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2018
ms.locfileid: "38959886"
---
# <a name="basicfstream-class"></a>basic_fstream 类

描述一个对象，该对象使用类 [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`> 的流缓冲区来控制元素和编码对象的插入和提取，该流缓冲区具有 `Elem` 类型的元素，其字符特征由类 `Tr` 确定。

## <a name="syntax"></a>语法

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_fstream : public basic_iostream<Elem, Tr>
```

### <a name="parameters"></a>参数

*Elem*文件缓冲区的基本元素。

*Tr*文件缓冲区的基本元素的特征 (通常`char_traits` <  `Elem`>)。

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

|成员函数|描述|
|-|-|
|[close](#close)|关闭文件。|
|[is_open](#is_open)|确定文件是否打开。|
|[open](#open)|打开文件。|
|[rdbuf](#rdbuf)|将指针类型的已存储流缓冲区的地址返回到 [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`>。|
|[swap](#swap)|将此对象的内容与另一个 `basic_fstream` 对象的内容进行交换。|

## <a name="requirements"></a>要求

**标头：**\<fstream>

**命名空间：** std

## <a name="basic_fstream"></a>  basic_fstream::basic_fstream

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

*_Filename*要打开的文件的名称。

*模式 （_m)* 中枚举之一[ios_base:: openmode](../standard-library/ios-base-class.md#openmode)。

*_Prot*默认文件打开保护，等同于*shflag*中的参数[_fsopen、 _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)。

### <a name="remarks"></a>备注

第一个构造函数通过调用来初始化基类[basic_iostream](../standard-library/basic-iostream-class.md)(`sb`)，其中`sb`是类的存储的对象[basic_filebuf](../standard-library/basic-filebuf-class.md) \< **Elem**， **Tr**>。 它还可以初始化`sb`通过调用`basic_filebuf` \< **Elem**， **Tr**>。

通过调用 `basic_iostream`( **sb**)，第二个和第三个构造函数可初始化基类。 它还可以初始化`sb`通过调用`basic_filebuf` \< **Elem**， **Tr**>，然后**sb.**[打开](../standard-library/basic-filebuf-class.md#open)(_*文件名*， `_Mode`)。 如果后一个函数返回一个 null 指针，该构造函数将调用[setstate](../standard-library/basic-ios-class.md#setstate)(`failbit`)。

第四个构造函数初始化具有 `right` 的内容的对象，将其视为右值引用。

### <a name="example"></a>示例

有关使用 `basic_fstream` 的示例，请参阅 [streampos](../standard-library/ios-typedefs.md#streampos)。

## <a name="close"></a>  basic_fstream::close

关闭文件。

```cpp
void close();
```

### <a name="remarks"></a>备注

此成员函数调用 [rdbuf](#rdbuf)**->** [close](../standard-library/basic-filebuf-class.md#close)。

### <a name="example"></a>示例

有关如何使用 `close` 的示例，请参阅 [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close)。

## <a name="is_open"></a>  basic_fstream::is_open

确定文件是否打开。

```cpp
bool is_open() const;
```

### <a name="return-value"></a>返回值

如果文件处于打开状态，则为 **true**，否则为 **false**。

### <a name="remarks"></a>备注

此成员函数返回 [rdbuf](#rdbuf)**->**[is_open](../standard-library/basic-filebuf-class.md#is_open)。

### <a name="example"></a>示例

有关如何使用 `is_open` 的示例，请参阅 [basic_filebuf:: is_open](../standard-library/basic-filebuf-class.md#is_open)。

## <a name="open"></a>  basic_fstream::open

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

*_Filename*要打开的文件的名称。

*模式 （_m)* 中枚举之一[ios_base:: openmode](../standard-library/ios-base-class.md#openmode)。

*_Prot*默认文件打开保护，等同于*shflag*中的参数[_fsopen、 _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)。

### <a name="remarks"></a>备注

此成员函数调用 [rdbuf](#rdbuf) **->** [open](../standard-library/basic-filebuf-class.md#open)(_ *Filename*, `_Mode`)。 如果该函数返回一个 null 指针，该函数将调用[setstate](../standard-library/basic-ios-class.md#setstate)( `failbit`)。

### <a name="example"></a>示例

请参阅[basic_filebuf:: open](../standard-library/basic-filebuf-class.md#open)以举例说明如何使用`open`。

## <a name="op_eq"></a>  basic_fstream::operator=

从指定的流对象向该对象分配内容。 这是涉及不会留下副本的右值的移动赋值运算符。

```cpp
basic_fstream& operator=(basic_fstream&& right);
```

### <a name="parameters"></a>参数

*右*左值引用到`basic_fstream`对象。

### <a name="return-value"></a>返回值

返回 `*this`。

### <a name="remarks"></a>备注

成员运算符使用的内容替换该对象的内容*右*，视为右值引用。

## <a name="rdbuf"></a>  basic_fstream::rdbuf

返回指向 [basic_filebuf](../standard-library/basic-filebuf-class.md)\< **Elem**, **Tr**> 的指针类型的已存储流缓冲区的地址。

```cpp
basic_filebuf<Elem, Tr> *rdbuf() const
```

### <a name="return-value"></a>返回值

已存储流缓冲区的地址。

### <a name="example"></a>示例

有关如何使用 `rdbuf` 的示例，请参阅 [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close)。

## <a name="swap"></a>  basic_fstream::swap

交换两个 `basic_fstream` 对象的内容。

```cpp
void swap(basic_fstream& right);
```

### <a name="parameters"></a>参数

*右*`lvalue`引用`basic_fstream`对象。

### <a name="remarks"></a>备注

成员函数将交换此对象的内容和内容*右*。

## <a name="see-also"></a>请参阅

[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream 编程](../standard-library/iostream-programming.md)<br/>
[iostreams 约定](../standard-library/iostreams-conventions.md)<br/>

---
title: basic_stringstream 类
ms.date: 11/04/2016
f1_keywords:
- sstream/std::basic_stringstream
- sstream/std::basic_stringstream::allocator_type
- sstream/std::basic_stringstream::rdbuf
- sstream/std::basic_stringstream::str
helpviewer_keywords:
- std::basic_stringstream [C++]
- std::basic_stringstream [C++], allocator_type
- std::basic_stringstream [C++], rdbuf
- std::basic_stringstream [C++], str
ms.assetid: 49629814-ca37-45c5-931b-4ff894e6ebd2
ms.openlocfilehash: 7e39d5dabf27ffbe15e519c006592935076a45c6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62414108"
---
# <a name="basicstringstream-class"></a>basic_stringstream 类

描述了一个对象，该对象可通过使用 [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`> 类的流缓冲区控制元素和编码对象的插入和提取。

## <a name="syntax"></a>语法

```cpp
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>
class basic_stringstream : public basic_iostream<Elem, Tr>
```

### <a name="parameters"></a>参数

*Alloc*<br/>
allocator 类。

*Elem*<br/>
字符串的基本元素的类型。

*Tr*<br/>
字符串的基本元素上专用的字符特征。

## <a name="remarks"></a>备注

此模板类描述控制元素的插入和提取的对象和编码的对象使用类的流缓冲区[basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**， **Tr**， `Alloc`>，类型的元素`Elem`，其字符特征由类`Tr`，并且其元素由类的分配器`Alloc`。 该对象存储 basic_stringbuf< **Elem**, **Tr**, `Alloc`> 类的对象。

### <a name="constructors"></a>构造函数

|构造函数|描述|
|-|-|
|[basic_stringstream](#basic_stringstream)|构造 `basic_stringstream` 类型的对象。|

### <a name="typedefs"></a>Typedef

|类型名称|描述|
|-|-|
|[allocator_type](#allocator_type)|该类型是模板参数 `Alloc` 的同义词。|

### <a name="member-functions"></a>成员函数

|成员函数|描述|
|-|-|
|[rdbuf](#rdbuf)|向 [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`, `Alloc`> 返回 `pointer` 类型的已存储流缓冲区的地址。|
|[str](#str)|设置或获取字符串缓冲区中的文本，而无需更改写入位置。|

## <a name="requirements"></a>要求

**标头：** \<sstream>

**命名空间：** std

## <a name="allocator_type"></a>  basic_stringstream::allocator_type

该类型是模板参数 `Alloc` 的同义词。

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_stringstream"></a>  basic_stringstream::basic_stringstream

构造 `basic_stringstream` 类型的对象。

```cpp
explicit basic_stringstream(ios_base::openmode _Mode = ios_base::in | ios_base::out);

explicit basic_stringstream(const basic_string<Elem, Tr, Alloc>& str, ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>参数

*_Mode*<br/>
[ios_base::openmode](../standard-library/ios-base-class.md#openmode) 中的枚举之一。

*str*<br/>
一个 `basic_string` 类型的对象。

### <a name="remarks"></a>备注

第一个构造函数通过调用来初始化基类[basic_iostream](../standard-library/basic-iostream-class.md)( **sb**)，其中`sb`是类的存储的对象[basic_stringbuf](../standard-library/basic-stringbuf-class.md) < **Elem**， **Tr**， `Alloc`>。 它还可以初始化`sb`通过调用 basic_stringbuf < **Elem**， **Tr**， `Alloc`> ( `_Mode`)。

第二个构造函数通过调用 basic_iostream( **sb**) 初始化基类。 它还可以初始化`sb`通过调用 basic_stringbuf < **Elem**， **Tr**， `Alloc`> (_ *Str*， `_Mode`)。

## <a name="rdbuf"></a>  basic_stringstream::rdbuf

将**指针**类型的已存储流缓冲区的地址返回到 [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>。

```cpp
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```

### <a name="return-value"></a>返回值

类型的存储的流缓冲区的地址`pointer`basic_stringbuf 到 < **Elem**， **Tr**， `Alloc`>。

### <a name="example"></a>示例

有关如何使用 `rdbuf` 的示例，请参阅 [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close)。

## <a name="str"></a>  basic_stringstream::str

设置或获取字符串缓冲区中的文本，而无需更改写入位置。

```cpp
basic_string<Elem, Tr, Alloc> str() const;

void str(
    const basic_string<Elem, Tr, Alloc>& _Newstr);
```

### <a name="parameters"></a>参数

*_Newstr*<br/>
新字符串。

### <a name="return-value"></a>返回值

返回 [basic_string](../standard-library/basic-string-class.md)< **Elem**, **Tr**, `Alloc`> 类的对象，它的受控序列是 **\*this** 控制的序列副本。

### <a name="remarks"></a>备注

第一个成员函数返回 [rdbuf](#rdbuf) -> [str](../standard-library/basic-stringbuf-class.md#str)。 第二个成员函数调用 `rdbuf` -> **str**( `_Newstr`)。

### <a name="example"></a>示例

请参阅[basic_stringbuf:: str](../standard-library/basic-stringbuf-class.md#str)有关的示例，使用`str`。

## <a name="see-also"></a>请参阅

[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream 编程](../standard-library/iostream-programming.md)<br/>
[iostreams 约定](../standard-library/iostreams-conventions.md)<br/>

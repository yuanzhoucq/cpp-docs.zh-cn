---
title: basic_ostringstream 类 | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- sstream/std::basic_ostringstream
- sstream/std::basic_ostringstream::allocator_type
- sstream/std::basic_ostringstream::rdbuf
- sstream/std::basic_ostringstream::str
dev_langs:
- C++
helpviewer_keywords:
- std::basic_ostringstream [C++]
- std::basic_ostringstream [C++], allocator_type
- std::basic_ostringstream [C++], rdbuf
- std::basic_ostringstream [C++], str
ms.assetid: aea699f7-350f-432a-acca-adbae7b483fb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1fb0027ba6afbceed8cc5f1daafef8cb183759ce
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2018
ms.locfileid: "38955229"
---
# <a name="basicostringstream-class"></a>basic_ostringstream 类

描述了控制元素和编码对象插入 [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`> 类的流缓冲区的对象。

## <a name="syntax"></a>语法

```cpp
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>
class basic_ostringstream : public basic_ostream<Elem, Tr>
```

### <a name="parameters"></a>参数

*分配*的分配器类。

*Elem*字符串的基本元素的类型。

*Tr*字符串的基本元素上专用的字符特征。

## <a name="remarks"></a>备注

此类的流缓冲区，类型的元素描述一个对象，控制插入的元素和编码的对象`Elem`，其字符特征由类`Tr`，和它的元素分配器的分配类`Alloc`。 该对象存储 basic_stringbuf< **Elem**, **Tr**, `Alloc`> 类的对象。

### <a name="constructors"></a>构造函数

|构造函数|描述|
|-|-|
|[basic_ostringstream](#basic_ostringstream)|构造 `basic_ostringstream` 类型的对象。|

### <a name="typedefs"></a>Typedef

|类型名称|描述|
|-|-|
|[allocator_type](#allocator_type)|该类型是模板参数的同义词*Alloc*。|

### <a name="member-functions"></a>成员函数

|成员函数|描述|
|-|-|
|[rdbuf](#rdbuf)|向 [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`, `Alloc`> 返回 `pointer` 类型的已存储流缓冲区的地址。|
|[str](#str)|设置或获取字符串缓冲区中的文本，而无需更改写入位置。|

## <a name="requirements"></a>要求

**标头：** \<sstream>

**命名空间：** std

## <a name="allocator_type"></a>  basic_ostringstream::allocator_type

该类型是模板参数的同义词*Alloc*。

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_ostringstream"></a>  basic_ostringstream::basic_ostringstream

构造 basic_ostringstream 类型的对象。

```cpp
explicit basic_ostringstream(ios_base::openmode _Mode = ios_base::out);

explicit basic_ostringstream(const basic_string<Elem, Tr, Alloc>& str, ios_base::openmode _Mode = ios_base::out);
```

### <a name="parameters"></a>参数

*模式 （_m)* 中枚举之一[ios_base:: openmode](../standard-library/ios-base-class.md#openmode)。

*str*类型的对象`basic_string`。

### <a name="remarks"></a>备注

第一个构造函数通过调用来初始化基类[basic_ostream](../standard-library/basic-ostream-class.md)( **sb**)，其中`sb`是类的存储的对象[basic_stringbuf](../standard-library/basic-stringbuf-class.md) < **Elem**， **Tr**， `Alloc`>。 通过调用 basic_stringbuf< **Elem**, **Tr**, `Alloc`>( `_Mode` &#124; `ios_base::out`)，它还可以初始化 **sb**。

第二个构造函数通过调用 basic_ostream( **sb**) 初始化基类。 它还可以初始化`sb`通过调用 basic_stringbuf < **Elem**， **Tr**， `Alloc`> (_ *Str*， `_Mode` &#124; `ios_base::out`).

## <a name="rdbuf"></a>  basic_ostringstream::rdbuf

返回类型的存储的流缓冲区的地址`pointer`到[basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**， **Tr**， `Alloc`>。

```cpp
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```

### <a name="return-value"></a>返回值

类型的已存储的流缓冲区的地址`pointer`basic_stringbuf 到 < **Elem**， **Tr**， `Alloc`>。

### <a name="remarks"></a>备注

此成员函数返回类型的存储的流缓冲区的地址`pointer`basic_stringbuf 到 < **Elem**， **Tr**， `Alloc`>。

### <a name="example"></a>示例

有关如何使用 `rdbuf` 的示例，请参阅 [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close)。

## <a name="str"></a>  basic_ostringstream::str

设置或获取字符串缓冲区中的文本，而无需更改写入位置。

```cpp
basic_string<Elem, Tr, Alloc> str() const;


void str(
    const basic_string<Elem, Tr, Alloc>& _Newstr);
```

### <a name="parameters"></a>参数

*_Newstr*新字符串。

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

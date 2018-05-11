---
title: basic_istringstream 类 | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- sstream/std::basic_istringstream
- sstream/std::basic_istringstream::allocator_type
- sstream/std::basic_istringstream::rdbuf
- sstream/std::basic_istringstream::str
- sstream/std::basic_istringstream::swap
dev_langs:
- C++
helpviewer_keywords:
- std::basic_istringstream [C++]
- std::basic_istringstream [C++], allocator_type
- std::basic_istringstream [C++], rdbuf
- std::basic_istringstream [C++], str
- std::basic_istringstream [C++], swap
ms.assetid: 1d5bb4b5-793d-4833-98e5-14676c451915
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0754ba9dc63f77793ced17e7950c7fc3ea3290d7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="basicistringstream-class"></a>basic_istringstream 类

描述了一个对象，该对象控制从 [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`> 类的流缓冲区中提取元素和编码对象的操作。

## <a name="syntax"></a>语法

```cpp
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>
class basic_istringstream : public basic_istream<Elem, Tr>
```

### <a name="parameters"></a>参数

`Alloc` 分配器类中。

`Elem` 字符串的基本元素的类型。

*Tr*字符串的基本元素上专用的字符特征。

## <a name="remarks"></a>备注

该模板类描述一个对象，该对象控制从 [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`> 类的流缓冲区中提取元素和编码对象的操作，该类具有 **Elem** 类型的元素，元素的字符特征由 **Tr** 类决定，并且其元素由 `Alloc` 类的分配器进行分配。 该对象存储 basic_stringbuf< **Elem**, **Tr**, `Alloc`> 类的对象。

### <a name="constructors"></a>构造函数

|构造函数|描述|
|-|-|
|[basic_istringstream](#basic_istringstream)|构造 `basic_istringstream` 类型的对象。|

### <a name="typedefs"></a>Typedef

|类型名称|描述|
|-|-|
|[allocator_type](#allocator_type)|该类型是模板参数 `Alloc` 的同义词。|

### <a name="member-functions"></a>成员函数

|成员函数|描述|
|-|-|
|[rdbuf](#rdbuf)|向 [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`, `Alloc`> 返回 `pointer` 类型的已存储流缓冲区的地址。|
|[str](#str)|设置或获取字符串缓冲区中的文本，而无需更改写入位置。|
|[swap](#swap)|将此 `basic_istringstream` 对象中的值与所提供对象的值进行交换。|

### <a name="operators"></a>运算符

|运算符|描述|
|-|-|
|[operator=](#op_eq)|将值从对象参数赋给此 `basic_istringstream` 对象。|

## <a name="requirements"></a>要求

**标头：** \<sstream>

**命名空间：** std

## <a name="allocator_type"></a>  basic_istringstream::allocator_type

该类型是模板参数 `Alloc` 的同义词。

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_istringstream"></a>  basic_istringstream::basic_istringstream

构造 `basic_istringstream` 类型的对象。

```cpp
explicit basic_istringstream(
    ios_base::openmode _Mode = ios_base::in);

explicit basic_istringstream(
    const basic_string<Elem, Tr, Alloc>& str,
    ios_base::openmode _Mode = ios_base::in);

basic_istringstream(
    basic_istringstream&& right);
```

### <a name="parameters"></a>参数

`_Mode` 中的枚举之一[ios_base:: openmode](../standard-library/ios-base-class.md#openmode)。

`str` 类型的对象`basic_string`。

`right` 右值引用的`basic_istringstream`对象。

### <a name="remarks"></a>备注

第一个构造函数通过调用 [basic_istream](../standard-library/basic-istream-class.md)(`sb`) 初始化基类，其中 `sb` 是 [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`, `Alloc`> 类的存储对象。 通过调用 `basic_stringbuf`< `Elem`, `Tr`, `Alloc`>( `_Mode` &#124; `ios_base::in`)，它还可以初始化 `sb`。

第二个构造函数通过调用 `basic_istream(sb)` 初始化基类。 通过调用 `basic_stringbuf`< `Elem`, `Tr`, `Alloc`>( `str`, `_Mode` &#124; `ios_base::in`)，它还可以初始化 `sb`。

第三个构造函数初始化具有 `right` 的内容的对象，将其视为右值引用。

## <a name="op_eq"></a>  basic_istringstream::operator=

将值从对象参数赋给此 `basic_istringstream` 对象。

```cpp
basic_istringstream& operator=(basic_istringstream&& right);
```

### <a name="parameters"></a>参数

`right` 对的右值引用`basic_istringstream`对象。

### <a name="remarks"></a>备注

成员运算符将对象的内容替换为 `right` 的内容，被视为右值引用移动赋值。

## <a name="rdbuf"></a>  basic_istringstream::rdbuf

将**指针**类型的已存储流缓冲区的地址返回到 [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>。

```cpp
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```

### <a name="return-value"></a>返回值

返回到 basic_stringbuf< **Elem**, **Tr**, `Alloc`> 的**指针**类型的已存储流缓冲区的地址。

### <a name="example"></a>示例

有关如何使用 `rdbuf` 的示例，请参阅 [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close)。

## <a name="str"></a>  basic_istringstream::str

设置或获取字符串缓冲区中的文本，而无需更改写入位置。

```cpp
basic_string<Elem, Tr, Alloc> str() const;


void str(
    const basic_string<Elem, Tr, Alloc>& _Newstr);
```

### <a name="parameters"></a>参数

`_Newstr` 新的字符串。

### <a name="return-value"></a>返回值

返回 [basic_string](../standard-library/basic-string-class.md)< **Elem**, **Tr**, `Alloc`> 类的对象，它的受控序列是 **\*this** 控制的序列副本。

### <a name="remarks"></a>备注

第一个成员函数返回 [rdbuf](#rdbuf) -> [str](../standard-library/basic-stringbuf-class.md#str)。 第二个成员函数调用 `rdbuf` -> **str**( `_Newstr`)。

### <a name="example"></a>示例

请参阅 [basic_stringbuf::str](../standard-library/basic-stringbuf-class.md#str)，了解使用 **str** 的示例。

## <a name="swap"></a>  basic_istringstream::swap

交换两个 `basic_istringstream` 对象的值。

```cpp
void swap(basic_istringstream& right);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|`right`|对 `basic_istringstream` 对象的 `lvalue` 引用。|

### <a name="remarks"></a>备注

成员函数将交换此对象的值和 `right` 的值。

## <a name="see-also"></a>请参阅

[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream 编程](../standard-library/iostream-programming.md)<br/>
[iostreams 约定](../standard-library/iostreams-conventions.md)<br/>

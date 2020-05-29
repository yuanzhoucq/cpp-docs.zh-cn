---
title: basic_ostringstream 类
ms.date: 11/04/2016
f1_keywords:
- sstream/std::basic_ostringstream
- sstream/std::basic_ostringstream::allocator_type
- sstream/std::basic_ostringstream::rdbuf
- sstream/std::basic_ostringstream::str
helpviewer_keywords:
- std::basic_ostringstream [C++]
- std::basic_ostringstream [C++], allocator_type
- std::basic_ostringstream [C++], rdbuf
- std::basic_ostringstream [C++], str
ms.assetid: aea699f7-350f-432a-acca-adbae7b483fb
ms.openlocfilehash: 9e10474d3e4fb2a37e8ab52f77495758c37e8a5b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376780"
---
# <a name="basic_ostringstream-class"></a>basic_ostringstream 类

描述一个对象，它控制将元素和编码的对象插入**elem、Tr** **Tr** `Alloc` [>basic_stringbuf类](../standard-library/basic-stringbuf-class.md)< 的流缓冲区中。

## <a name="syntax"></a>语法

```cpp
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>
class basic_ostringstream : public basic_ostream<Elem, Tr>
```

### <a name="parameters"></a>参数

*Alloc*\
allocator 类。

*埃莱姆*\
字符串的基本元素的类型。

*Tr*\
字符串的基本元素上专用的字符特征。

## <a name="remarks"></a>备注

类描述一个对象，该对象控制将元素和编码对象插入到流缓冲区中，其元素的类型`Elem`由 类`Tr`确定，其元素由类`Alloc`的分配器分配。 该对象存储 basic_stringbuf< **Elem**, **Tr**, `Alloc`> 类的对象。

### <a name="constructors"></a>构造函数

|构造函数|说明|
|-|-|
|[basic_ostringstream](#basic_ostringstream)|构造 `basic_ostringstream` 类型的对象。|

### <a name="typedefs"></a>Typedef

|类型名称|说明|
|-|-|
|[allocator_type](#allocator_type)|该类型是模板参数*Alloc*的同义词。|

### <a name="member-functions"></a>成员职能

|成员函数|说明|
|-|-|
|[rdbuf](#rdbuf)|`pointer`将类型的存储流缓冲区的地址返回[到basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`，>。 `Tr` `Alloc`|
|[Str](#str)|设置或获取字符串缓冲区中的文本，而无需更改写入位置。|

## <a name="requirements"></a>要求

**标头：** \<sstream>

**命名空间:** std

## <a name="basic_ostringstreamallocator_type"></a><a name="allocator_type"></a>basic_ostringstream：allocator_type

该类型是模板参数*Alloc*的同义词。

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_ostringstreambasic_ostringstream"></a><a name="basic_ostringstream"></a>basic_ostringstream：：basic_ostringstream

构造 basic_ostringstream 类型的对象。

```cpp
explicit basic_ostringstream(ios_base::openmode _Mode = ios_base::out);

explicit basic_ostringstream(const basic_string<Elem, Tr, Alloc>& str, ios_base::openmode _Mode = ios_base::out);
```

### <a name="parameters"></a>参数

*_Mode*\
[ios_base::openmode](../standard-library/ios-base-class.md#openmode) 中的枚举之一。

*Str*\
一个 `basic_string` 类型的对象。

### <a name="remarks"></a>备注

第一个构造函数通过调用[basic_ostream](../standard-library/basic-ostream-class.md) **（sb**） 初始化基`sb`类，其中basic_stringbuf< Elem、Tr、>basic_stringbuf`Alloc`[类的](../standard-library/basic-stringbuf-class.md)存储对象。**Elem** **Tr** 通过调用 basic_stringbuf< **Elem**, **Tr**, `Alloc`>( `_Mode` &#124; `ios_base::out`)，它还可以初始化 **sb**。

第二个构造函数通过调用 basic_ostream( **sb**) 初始化基类。 `sb`它还通过调用basic_stringbuf<**埃莱姆****，Tr，>（*** `Alloc` *斯特*，&#124;）。 `_Mode` `ios_base::out`

## <a name="basic_ostringstreamrdbuf"></a><a name="rdbuf"></a>basic_ostringstream：：rdbuf

`pointer`将存储的流缓冲区的地址返回elem、Tr、>basic_stringbuf。 **Tr** `Alloc` [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**

```cpp
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```

### <a name="return-value"></a>返回值

存储的`pointer`流缓冲区的地址，类型为basic_stringbuf< **Elem、Tr、>。** **Tr** `Alloc`

### <a name="remarks"></a>备注

成员`pointer`函数将存储的流缓冲区的地址返回到basic_stringbuf< **Elem、Tr、>。** **Tr** `Alloc`

### <a name="example"></a>示例

有关如何使用 `rdbuf` 的示例，请参阅 [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close)。

## <a name="basic_ostringstreamstr"></a><a name="str"></a>basic_ostringstream：斯特

设置或获取字符串缓冲区中的文本，而无需更改写入位置。

```cpp
basic_string<Elem, Tr, Alloc> str() const;

void str(
    const basic_string<Elem, Tr, Alloc>& _Newstr);
```

### <a name="parameters"></a>参数

*_Newstr*\
新字符串。

### <a name="return-value"></a>返回值

返回类的对象[basic_string](../standard-library/basic-string-class.md)< **Elem、** **Tr、>，**`Alloc`其受控序列是**\*受此**控制序列的副本。

### <a name="remarks"></a>备注

第一个成员函数返回[rdbuf](#rdbuf) -> [str](../standard-library/basic-stringbuf-class.md#str)。 第二个成员函数调用`rdbuf` -> **str**str `_Newstr`（ 。

### <a name="example"></a>示例

有关 使用`str`的示例，请参阅[basic_stringbuf：：str。](../standard-library/basic-stringbuf-class.md#str)

## <a name="see-also"></a>另请参阅

[C++标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[电流编程](../standard-library/iostream-programming.md)\
[iostreams 约定](../standard-library/iostreams-conventions.md)

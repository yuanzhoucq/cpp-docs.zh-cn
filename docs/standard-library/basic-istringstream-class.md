---
title: basic_istringstream 类
ms.date: 11/04/2016
f1_keywords:
- sstream/std::basic_istringstream
- sstream/std::basic_istringstream::allocator_type
- sstream/std::basic_istringstream::rdbuf
- sstream/std::basic_istringstream::str
- sstream/std::basic_istringstream::swap
helpviewer_keywords:
- std::basic_istringstream [C++]
- std::basic_istringstream [C++], allocator_type
- std::basic_istringstream [C++], rdbuf
- std::basic_istringstream [C++], str
- std::basic_istringstream [C++], swap
ms.assetid: 1d5bb4b5-793d-4833-98e5-14676c451915
ms.openlocfilehash: 6a8ead5f1014e7f750e01988241ab020431312da
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376806"
---
# <a name="basic_istringstream-class"></a>basic_istringstream 类

描述一个对象，它控制从类[basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem、Tr**>**Tr**`Alloc`的流缓冲区提取元素和编码对象。

## <a name="syntax"></a>语法

```cpp
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>
class basic_istringstream : public basic_istream<Elem, Tr>
```

### <a name="parameters"></a>参数

*Alloc*\
allocator 类。

*埃莱姆*\
字符串的基本元素的类型。

*Tr*\
字符串的基本元素上专用的字符特征。

## <a name="remarks"></a>备注

类模板描述一个对象，该对象控制从类[basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem、Tr、>**`Alloc`的流缓冲区中提取**Tr**元素和编码对象，该对象具有*Elem*类型的元素，其字符特征由类*Tr*确定，其元素由类*Alloc*的分配器分配。 该对象存储 basic_stringbuf< **Elem**, **Tr**, `Alloc`> 类的对象。

### <a name="constructors"></a>构造函数

|构造函数|说明|
|-|-|
|[basic_istringstream](#basic_istringstream)|构造 `basic_istringstream` 类型的对象。|

### <a name="typedefs"></a>Typedef

|类型名称|说明|
|-|-|
|[allocator_type](#allocator_type)|类型是模板参数 `Alloc` 的同义词。|

### <a name="member-functions"></a>成员职能

|成员函数|说明|
|-|-|
|[rdbuf](#rdbuf)|`pointer`将类型的存储流缓冲区的地址返回[到basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`，>。 `Tr` `Alloc`|
|[Str](#str)|设置或获取字符串缓冲区中的文本，而无需更改写入位置。|
|[交换](#swap)|将此 `basic_istringstream` 对象中的值与所提供对象的值进行交换。|

### <a name="operators"></a>运算符

|操作员|说明|
|-|-|
|[运算符*](#op_eq)|将值从对象参数赋给此 `basic_istringstream` 对象。|

## <a name="requirements"></a>要求

**标头：** \<sstream>

**命名空间:** std

## <a name="basic_istringstreamallocator_type"></a><a name="allocator_type"></a>basic_istringstream：allocator_type

类型是模板参数 `Alloc` 的同义词。

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_istringstreambasic_istringstream"></a><a name="basic_istringstream"></a>basic_istringstream：basic_istringstream

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

*_Mode*\
[ios_base::openmode](../standard-library/ios-base-class.md#openmode) 中的枚举之一。

*Str*\
一个 `basic_string` 类型的对象。

*对*\
`basic_istringstream` 对象的右值引用。

### <a name="remarks"></a>备注

第一个构造函数通过调用[basic_istream](../standard-library/basic-istream-class.md)`sb`（） 初始化基`sb`类，其中类[basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`的存储对象`Tr` `Alloc`>。 通过调用 `basic_stringbuf`< `Elem`, `Tr`, `Alloc`>( `_Mode` &#124; `ios_base::in`)，它还可以初始化 `sb`。

第二个构造函数通过调用 `basic_istream(sb)` 初始化基类。 通过调用 `basic_stringbuf`< `Elem`, `Tr`, `Alloc`>( `str`, `_Mode` &#124; `ios_base::in`)，它还可以初始化 `sb`。

第三个构造函数用*右侧*的内容初始化对象，作为 rvalue 引用处理。

## <a name="basic_istringstreamoperator"></a><a name="op_eq"></a>basic_istringstream：：操作员*

将值从对象参数赋给此 `basic_istringstream` 对象。

```cpp
basic_istringstream& operator=(basic_istringstream&& right);
```

### <a name="parameters"></a>参数

*对*\
对 `basic_istringstream` 对象的右值引用。

### <a name="remarks"></a>备注

成员运算符将对象的内容替换为*右侧*的内容，视为 rvalue 引用移动赋值。

## <a name="basic_istringstreamrdbuf"></a><a name="rdbuf"></a>basic_istringstream：：rdbuf

`pointer`将存储的流缓冲区的地址返回elem、Tr、>basic_stringbuf。 **Tr** `Alloc` [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**

```cpp
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```

### <a name="return-value"></a>返回值

`pointer`存储的流缓冲区的地址，< **Elem**<，tr **Tr**>basic_stringbuf。 `Alloc`

### <a name="example"></a>示例

有关如何使用 `rdbuf` 的示例，请参阅 [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close)。

## <a name="basic_istringstreamstr"></a><a name="str"></a>basic_istringstream：斯特

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

## <a name="basic_istringstreamswap"></a><a name="swap"></a>basic_istringstream：：交换

交换两个 `basic_istringstream` 对象的值。

```cpp
void swap(basic_istringstream& right);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*对*|对 `basic_istringstream` 对象的 `lvalue` 引用。|

### <a name="remarks"></a>备注

成员函数交换此对象的值和*右*的值。

## <a name="see-also"></a>另请参阅

[C++标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[电流编程](../standard-library/iostream-programming.md)\
[iostreams 约定](../standard-library/iostreams-conventions.md)

---
title: '&lt;sstream&gt;'
ms.date: 11/04/2016
f1_keywords:
- <sstream>
helpviewer_keywords:
- sstream header
ms.assetid: 56f55bc5-549d-4e7f-aaad-99e0ffa49c9e
ms.openlocfilehash: cc08fb426df289b3478ad9d29b03f9a6dd5d3978
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412470"
---
# <a name="ltsstreamgt"></a>&lt;sstream&gt;

定义几个模板类，这些类支持存储于分配数组对象序列上的 iostreams 操作。 此类序列可以轻松转换为模板类 [basic_string](../standard-library/basic-string-class.md) 的对象或从其中进行转换。

## <a name="syntax"></a>语法

```cpp
namespace std {
template <class CharType, class Traits = char_traits<CharType>, class Allocator = allocator<CharType>>
class basic_stringbuf;
typedef basic_stringbuf<char>
stringbuf;
typedef basic_stringbuf<wchar_t> wstringbuf;

template <class CharType, class Traits = char_traits<CharType>, class Allocator = allocator<CharType>>
class basic_istringstream;
typedef basic_istringstream<char>
istringstream;
typedef basic_istringstream<wchar_t> wistringstream;

template <class CharType, class Traits = char_traits<CharType>, class Allocator = allocator<CharType>>
class basic_ostringstream;
typedef basic_ostringstream<char>
ostringstream;
typedef basic_ostringstream<wchar_t> wostringstream;

template <class CharType, class Traits = char_traits<CharType>, class Allocator = allocator<CharType>>
class basic_stringstream;
typedef basic_stringstream<char>
stringstream;
typedef basic_stringstream<wchar_t> wstringstream;
// TEMPLATE FUNCTIONS
template <class CharType, class Traits, class Allocator>
void swap(
    basic_stringbuf<CharType, Traits, Allocator>& left,
    basic_stringbuf<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
void swap(
    basic_istringstream<CharType, Traits, Allocator>& left,
    basic_istringstream<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
void swap(
    basic_ostringstream<CharType, Traits, Allocator>& left,
    basic_ostringstream<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
void swap (
    basic_stringstream<CharType, Traits, Allocator>& left,
    basic_stringstream<CharType, Traits, Allocator>& right);

}  // namespace std
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*left*|引用 `sstream` 对象。|
|*right*|引用 `sstream` 对象。|

## <a name="remarks"></a>备注

类型为 `char *` 的对象可使用 [\<strstream >](../standard-library/strstream.md) 中的功能进行流式处理。 但是， \<strstream > 已弃用以及如何使用\<sstream > 建议。

### <a name="typedefs"></a>Typedef

|类型名称|描述|
|-|-|
|[istringstream](../standard-library/sstream-typedefs.md#istringstream)|创建类型`basic_istringstream`专用于**char**模板参数。|
|[ostringstream](../standard-library/sstream-typedefs.md#ostringstream)|创建类型`basic_ostringstream`专用于**char**模板参数。|
|[stringbuf](../standard-library/sstream-typedefs.md#stringbuf)|创建类型`basic_stringbuf`专用于**char**模板参数。|
|[stringstream](../standard-library/sstream-typedefs.md#stringstream)|创建类型`basic_stringstream`专用于**char**模板参数。|
|[wistringstream](../standard-library/sstream-typedefs.md#wistringstream)|创建类型`basic_istringstream`专用于**wchar_t**模板参数。|
|[wostringstream](../standard-library/sstream-typedefs.md#wostringstream)|创建类型`basic_ostringstream`专用于**wchar_t**模板参数。|
|[wstringbuf](../standard-library/sstream-typedefs.md#wstringbuf)|创建类型`basic_stringbuf`专用于**wchar_t**模板参数。|
|[wstringstream](../standard-library/sstream-typedefs.md#wstringstream)|创建类型`basic_stringstream`专用于**wchar_t**模板参数。|

### <a name="manipulators"></a>操控器

|||
|-|-|
|[swap](../standard-library/sstream-functions.md#sstream_swap)|交换两个 `sstream` 对象间的值。|

### <a name="classes"></a>类

|类|描述|
|-|-|
|[basic_stringbuf](../standard-library/basic-stringbuf-class.md)|描述对 `Elem` 类型的元素（其字符特征由类 `Tr` 确定）与数组对象中存储的元素序列之间的来回传输进行控制的流缓冲区。|
|[basic_istringstream](../standard-library/basic-istringstream-class.md)|描述一个对象，用于控制提取元素和编码的对象类的流缓冲区[basic_stringbuf](../standard-library/basic-stringbuf-class.md)<**Elem**， **Tr**， `Alloc`>，类型的元素`Elem`，其字符特征由类`Tr`，并且其元素由类的分配器`Alloc`。|
|[basic_ostringstream](../standard-library/basic-ostringstream-class.md)|描述类的流缓冲区控制元素插入的对象和编码的对象[basic_stringbuf](../standard-library/basic-stringbuf-class.md)<**Elem**， **Tr**， `Alloc`>，类型的元素`Elem`，其字符特征由类`Tr`，并且其元素由类的分配器`Alloc`。|
|[basic_stringstream](../standard-library/basic-stringstream-class.md)|描述控制元素的插入和提取的对象和编码的对象使用类的流缓冲区[basic_stringbuf](../standard-library/basic-stringbuf-class.md)<**Elem**， **Tr**， `Alloc`>，类型的元素`Elem`，其字符特征由类`Tr`，并且其元素由类的分配器`Alloc`。|

## <a name="requirements"></a>要求

- **标头：** \<sstream>

- **命名空间：** std

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream 编程](../standard-library/iostream-programming.md)<br/>
[iostreams 约定](../standard-library/iostreams-conventions.md)<br/>

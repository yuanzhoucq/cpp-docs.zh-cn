---
title: '&lt;sstream&gt;'
ms.date: 11/04/2016
f1_keywords:
- <sstream>
helpviewer_keywords:
- sstream header
ms.assetid: 56f55bc5-549d-4e7f-aaad-99e0ffa49c9e
ms.openlocfilehash: 6ab2164e4969a2320f67d479062808b33b0869f9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212132"
---
# <a name="ltsstreamgt"></a>&lt;sstream&gt;

定义多个类模板，这些模板支持对存储在已分配的数组对象中的序列进行 iostreams 操作。 此类序列可轻松地与类模板[basic_string](../standard-library/basic-string-class.md)的对象相互转换。

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
|*左中*|引用 `sstream` 对象。|
|*然后*|引用 `sstream` 对象。|

## <a name="remarks"></a>备注

类型的对象 `char *` 可使用中的功能 [\<strstream>](../standard-library/strstream.md) 进行流式处理。 但是，已弃用 \<strstream>，建议使用 \<sstream>。

### <a name="typedefs"></a>Typedef

|类型名称|描述|
|-|-|
|[istringstream](../standard-library/sstream-typedefs.md#istringstream)|创建 `basic_istringstream` 专用于 **`char`** 模板参数的类型。|
|[ostringstream](../standard-library/sstream-typedefs.md#ostringstream)|创建 `basic_ostringstream` 专用于 **`char`** 模板参数的类型。|
|[stringbuf](../standard-library/sstream-typedefs.md#stringbuf)|创建 `basic_stringbuf` 专用于 **`char`** 模板参数的类型。|
|[stringstream](../standard-library/sstream-typedefs.md#stringstream)|创建 `basic_stringstream` 专用于 **`char`** 模板参数的类型。|
|[wistringstream](../standard-library/sstream-typedefs.md#wistringstream)|创建 `basic_istringstream` 专用于 **`wchar_t`** 模板参数的类型。|
|[wostringstream](../standard-library/sstream-typedefs.md#wostringstream)|创建 `basic_ostringstream` 专用于 **`wchar_t`** 模板参数的类型。|
|[wstringbuf](../standard-library/sstream-typedefs.md#wstringbuf)|创建 `basic_stringbuf` 专用于 **`wchar_t`** 模板参数的类型。|
|[wstringstream](../standard-library/sstream-typedefs.md#wstringstream)|创建 `basic_stringstream` 专用于 **`wchar_t`** 模板参数的类型。|

### <a name="manipulators"></a>操控器

|||
|-|-|
|[swap](../standard-library/sstream-functions.md#sstream_swap)|交换两个 `sstream` 对象间的值。|

### <a name="classes"></a>类

|类|说明|
|-|-|
|[basic_stringbuf](../standard-library/basic-stringbuf-class.md)|描述对 `Elem` 类型的元素（其字符特征由类 `Tr` 确定）与数组对象中存储的元素序列之间的来回传输进行控制的流缓冲区。|
|[basic_istringstream](../standard-library/basic-istringstream-class.md)|描述一个对象，该对象控制从类[basic_stringbuf](../standard-library/basic-stringbuf-class.md)Elem、Tr、> 的流缓冲区提取元素和编码对象， < **Elem** **Tr** `Alloc` `Elem` 其字符特征由类确定 `Tr` ，并且其元素由类的分配器进行分配 `Alloc` 。|
|[basic_ostringstream](../standard-library/basic-ostringstream-class.md)|描述一个对象，该对象控制将元素和编码对象插入到类[basic_stringbuf](../standard-library/basic-stringbuf-class.md) < **Elem**， **Tr**，> 的流缓冲区中， `Alloc` `Elem` 其字符特征由类确定 `Tr` ，并且其元素由类的分配器进行分配 `Alloc` 。|
|[basic_stringstream](../standard-library/basic-stringstream-class.md)|描述一个对象，该对象使用类[basic_stringbuf](../standard-library/basic-stringbuf-class.md)Elem，Tr，> 的流缓冲区控制元素和编码对象的插入和提取， < **Elem** **Tr** `Alloc` `Elem` 其字符特征由类确定 `Tr` ，并且其元素由类的分配器进行分配 `Alloc` 。|

## <a name="requirements"></a>要求

- **标头：**\<sstream>

- **命名空间:** std

## <a name="see-also"></a>另请参阅

[标头文件引用](../standard-library/cpp-standard-library-header-files.md)\
[C + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 编程](../standard-library/iostream-programming.md)\
[iostreams 约定](../standard-library/iostreams-conventions.md)

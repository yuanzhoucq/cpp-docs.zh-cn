---
title: '&lt;sstream&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <sstream>
dev_langs:
- C++
helpviewer_keywords:
- sstream header
ms.assetid: 56f55bc5-549d-4e7f-aaad-99e0ffa49c9e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0ee9beb54dd241c6987b79db238f033f3d169497
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33861670"
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
|`left`|引用 `sstream` 对象。|
|`right`|引用 `sstream` 对象。|

## <a name="remarks"></a>备注

类型为 `char *` 的对象可使用 [\<strstream >](../standard-library/strstream.md) 中的功能进行流式处理。 但是， \<strstream > 已弃用以及如何使用\<sstream > 建议。

### <a name="typedefs"></a>Typedef

|类型名称|描述|
|-|-|
|[istringstream](../standard-library/sstream-typedefs.md#istringstream)|创建专用于 `char` 模板参数的类型 `basic_istringstream`。|
|[ostringstream](../standard-library/sstream-typedefs.md#ostringstream)|创建专用于 `char` 模板参数的类型 `basic_ostringstream`。|
|[stringbuf](../standard-library/sstream-typedefs.md#stringbuf)|创建专用于 `char` 模板参数的类型 `basic_stringbuf`。|
|[stringstream](../standard-library/sstream-typedefs.md#stringstream)|创建专用于 `char` 模板参数的类型 `basic_stringstream`。|
|[wistringstream](../standard-library/sstream-typedefs.md#wistringstream)|创建专用于 `wchar_t` 模板参数的类型 `basic_istringstream`。|
|[wostringstream](../standard-library/sstream-typedefs.md#wostringstream)|创建专用于 `wchar_t` 模板参数的类型 `basic_ostringstream`。|
|[wstringbuf](../standard-library/sstream-typedefs.md#wstringbuf)|创建专用于 `wchar_t` 模板参数的类型 `basic_stringbuf`。|
|[wstringstream](../standard-library/sstream-typedefs.md#wstringstream)|创建专用于 `wchar_t` 模板参数的类型 `basic_stringstream`。|

### <a name="manipulators"></a>操控器

|||
|-|-|
|[swap](../standard-library/sstream-functions.md#sstream_swap)|交换两个 `sstream` 对象间的值。|

### <a name="classes"></a>类

|类|描述|
|-|-|
|[basic_stringbuf](../standard-library/basic-stringbuf-class.md)|描述对 **Elem** 类型的元素（其字符特征由类 **Tr** 确定）与数组对象中存储的元素序列之间的来回传输进行控制的流缓冲区。|
|[basic_istringstream](../standard-library/basic-istringstream-class.md)|描述一个对象，该对象控制从 [basic_stringbuf](../standard-library/basic-stringbuf-class.md)<**Elem**, **Tr**, `Alloc`> 类的流缓冲区中提取元素和编码对象的操作，该类具有 **Elem** 类型的元素，元素的字符特征由 **Tr** 类确定，并且其元素由 `Alloc` 类的分配器进行分配。|
|[basic_ostringstream](../standard-library/basic-ostringstream-class.md)|描述一个对象，该对象控制在 [basic_stringbuf](../standard-library/basic-stringbuf-class.md)<**Elem**, **Tr**, `Alloc`> 类的流缓冲区中插入元素和编码对象的操作，该类具有 **Elem** 类型的元素，元素的字符特征由 **Tr** 类确定，并且其元素由 `Alloc` 类的分配器进行分配。|
|[basic_stringstream](../standard-library/basic-stringstream-class.md)|描述一个对象，该对象使用 [basic_stringbuf](../standard-library/basic-stringbuf-class.md)<**Elem**, **Tr**, `Alloc`> 类的流缓冲区，控制插入和提取元素和编码对象的操作，该类具有 **Elem** 类型的元素，元素的字符特征由 **Tr** 类确定，并且其元素由 `Alloc` 类的分配器进行分配。|

## <a name="requirements"></a>要求

- **标头：** \<sstream>

- **命名空间：** std

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream 编程](../standard-library/iostream-programming.md)<br/>
[iostreams 约定](../standard-library/iostreams-conventions.md)<br/>

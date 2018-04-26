---
title: basic_stringbuf 类 | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- sstream/std::basic_stringbuf
- sstream/std::basic_stringbuf::allocator_type
- sstream/std::basic_stringbuf::char_type
- sstream/std::basic_stringbuf::int_type
- sstream/std::basic_stringbuf::off_type
- sstream/std::basic_stringbuf::pos_type
- sstream/std::basic_stringbuf::traits_type
- sstream/std::basic_stringbuf::overflow
- sstream/std::basic_stringbuf::pbackfail
- sstream/std::basic_stringbuf::seekoff
- sstream/std::basic_stringbuf::seekpos
- sstream/std::basic_stringbuf::str
- sstream/std::basic_stringbuf::underflow
dev_langs:
- C++
helpviewer_keywords:
- std::basic_stringbuf [C++]
- std::basic_stringbuf [C++], allocator_type
- std::basic_stringbuf [C++], char_type
- std::basic_stringbuf [C++], int_type
- std::basic_stringbuf [C++], off_type
- std::basic_stringbuf [C++], pos_type
- std::basic_stringbuf [C++], traits_type
- std::basic_stringbuf [C++], overflow
- std::basic_stringbuf [C++], pbackfail
- std::basic_stringbuf [C++], seekoff
- std::basic_stringbuf [C++], seekpos
- std::basic_stringbuf [C++], str
- std::basic_stringbuf [C++], underflow
ms.assetid: 40c85f9e-42a5-4a65-af5c-23c8e3bf8113
caps.latest.revision: 28
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a02c98dad5597bc1a3f2e48a2b2ba2952c6f06c9
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="basicstringbuf-class"></a>basic_stringbuf 类

描述对 `Elem` 类型的元素（其字符特征由类 `Tr` 确定）与数组对象中存储的元素序列之间的来回传输进行控制的流缓冲区。

## <a name="syntax"></a>语法

```cpp
template <class Elem, class Tr = char_traits<Elem>,
    class Alloc = allocator<Elem>>
class basic_stringbuf : public basic_streambuf<Elem, Tr>
```

### <a name="parameters"></a>参数

`Alloc` 分配器类中。

`Elem` 字符串的基本元素的类型。

`Tr` 字符串的基本元素上专用的字符特征。

## <a name="remarks"></a>备注

对象根据需要进行分配、扩展和释放以适应序列中的更改。

类 basic_stringbuf< `Elem`, `Tr`, `Alloc`> 的对象将来自其构造函数的 `ios_base::`[openmode](../standard-library/ios-base-class.md#openmode) 自变量的副本作为其 `stringbuf` 模式 **mode** 进行存储：

- 如果 `mode & ios_base::in` 不是零，则输入缓冲区可以访问。 有关详细信息，请参阅 [basic_streambuf 类](../standard-library/basic-streambuf-class.md)。

- 如果 `mode & ios_base::out` 不是零，则输出缓冲区可以访问。

### <a name="constructors"></a>构造函数

|构造函数|描述|
|-|-|
|[basic_stringbuf](#basic_stringbuf)|构造 `basic_stringbuf` 类型的对象。|

### <a name="typedefs"></a>Typedef

|类型名称|描述|
|-|-|
|[allocator_type](#allocator_type)|该类型是模板参数 `Alloc` 的同义词。|
|[char_type](#char_type)|将类型名与 `Elem` 模板参数关联。|
|[int_type](#int_type)|使 `basic_filebuf` 范围中的此类型等效于 `Tr` 范围中具有相同名称的类型。|
|[off_type](#off_type)|使 `basic_filebuf` 范围中的此类型等效于 `Tr` 范围中具有相同名称的类型。|
|[pos_type](#pos_type)|使 `basic_filebuf` 范围中的此类型等效于 `Tr` 范围中具有相同名称的类型。|
|[traits_type](#traits_type)|将类型名与 `Tr` 模板参数关联。|

### <a name="member-functions"></a>成员函数

|成员函数|描述|
|-|-|
|[overflow](#overflow)|将新字符插入到已满缓冲区时可以调用的受保护虚函数。|
|[pbackfail](#pbackfail)|受保护虚拟成员函数尝试将元素放回到输入缓冲区中，随后使它成为当前元素（由下一个指针指向）。|
|[seekoff](#seekoff)|受保护虚拟成员函数尝试更改受控制流的当前位置。|
|[seekpos](#seekpos)|受保护虚拟成员函数尝试更改受控制流的当前位置。|
|[str](#str)|设置或获取字符串缓冲区中的文本，而无需更改写入位置。|
|swap||
|[underflow](#underflow)|从输入流中提取当前元素的受保护虚拟成员函数。|

## <a name="requirements"></a>要求

**标头：** \<sstream>

**命名空间：** std

## <a name="allocator_type"></a>  basic_stringbuf::allocator_type

该类型是模板参数 `Alloc` 的同义词。

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_stringbuf"></a>  basic_stringbuf::basic_stringbuf

构造 `basic_stringbuf` 类型的对象。

```cpp
basic_stringbuf(
    ios_base::openmode _Mode = ios_base::in | ios_base::out);

basic_stringbuf(
    const basic_string<Elem, Tr, Alloc>& str,
    ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>参数

`_Mode` 中的枚举之一[ios_base:: openmode](../standard-library/ios-base-class.md#openmode)。

`str` 类型的对象[basic_string](../standard-library/basic-string-class.md)。

### <a name="remarks"></a>备注

第一个构造函数将 null 指针存储在控制输入缓冲区和输出缓冲区的所有指针中。 有关详细信息，请参阅 [basic_streambuf 类](../standard-library/basic-streambuf-class.md)的备注部分。 它还将 `_Mode` 存储为 stringbuf 模式。 有关详细信息，请参阅 [basic_stringbuf 类](../standard-library/basic-stringbuf-class.md)的备注部分。

第二个构造函数分配字符串对象 `str` 控制的序列副本。 如果 `_Mode & ios_base::in` 是非零值，则其将输入缓冲区设置为在序列的开头开始读取。 如果 `_Mode & ios_base::out` 是非零值，则其将输出缓冲区设置为在序列的开头开始写入。 它还将 `_Mode` 存储为 stringbuf 模式。 有关详细信息，请参阅 [basic_stringbuf 类](../standard-library/basic-stringbuf-class.md)的备注部分。

## <a name="char_type"></a>  basic_stringbuf::char_type

将类型名与 **Elem** 模板参数关联。

```cpp
typedef Elem char_type;
```

## <a name="int_type"></a>  basic_stringbuf::int_type

使 basic_filebuf 范围中的此类型等效于 **Tr** 范围中具有相同名称的类型。

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="off_type"></a>  basic_stringbuf::off_type

使 basic_filebuf 范围中的此类型等效于 **Tr** 范围中具有相同名称的类型。

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="overflow"></a>  basic_stringbuf::overflow

将新字符插入到已满缓冲区时可以调用的受保护虚函数。

```cpp
virtual int_type overflow(int_type _Meta = traits_type::eof());
```

### <a name="parameters"></a>参数

`_Meta` 要插入到缓冲区中的字符或**traits_type::eof**。

### <a name="return-value"></a>返回值

如果该函数不成功，它将返回 **traits_type::eof**。 否则，它将返回 **traits_type::**[not_eof](../standard-library/char-traits-struct.md#not_eof)(_ *Meta*)。

### <a name="remarks"></a>备注

如果 _ *Meta* 不等于 **traits_type::**[eof](../standard-library/char-traits-struct.md#eof)，则受保护虚拟成员函数尝试将元素 **traits_type::**[to_char_type](../standard-library/char-traits-struct.md#to_char_type)(\_ *Meta*) 插入输出缓冲区。 它可以用多种方法执行此操作：

- 如果写入位置可用，它可将元素存储到写入位置并递增输出缓冲区的下一个指针。

- 它可以通过为输出缓冲区分配新的或额外的存储空间，提供写入位置。 以这种方式扩展输出缓冲区还会扩展任何关联的输入缓冲区。

## <a name="pbackfail"></a>  basic_stringbuf::pbackfail

受保护虚拟成员函数尝试将元素放回输入缓冲区，随后使它成为当前元素（由下一个指针指向）。

```cpp
virtual int_type pbackfail(int_type _Meta = traits_type::eof());
```

### <a name="parameters"></a>参数

`_Meta` 要插入到缓冲区中的字符或**traits_type::eof**。

### <a name="return-value"></a>返回值

如果该函数不成功，它将返回 **traits_type::eof**。 否则，它将返回 **traits_type::**[not_eof](../standard-library/char-traits-struct.md#not_eof)(_ *Meta*)。

### <a name="remarks"></a>备注

如果 `_Meta` 等于 **traits_type::**[eof](../standard-library/char-traits-struct.md#eof)，要推送回的元素在当前元素之前实际上已是流中的一个元素了。 否则，则由 **byte** = **traits_type::**[to_char_type](../standard-library/char-traits-struct.md#to_char_type)(_ *Meta*) 替换该元素。 该函数可以用多种方法放回元素：

- 如果放回的位置可用，且存储在该位置的元素等于 byte，它可以递减输入缓冲区中的下一个指针。

- 如果放回的位置可用且 stringbuf 模式允许更改序列（**mode & ios_base::out** 是非零值），则该函数可以将 byte 存储到放回位置并递减输入缓冲区中的下一个指针。

## <a name="pos_type"></a>  basic_stringbuf::pos_type

使 basic_filebuf 范围中的此类型等效于 **Tr** 范围中具有相同名称的类型。

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="seekoff"></a>  basic_stringbuf::seekoff

受保护虚拟成员函数尝试更改受控制流的当前位置。

```cpp
virtual pos_type seekoff(
    off_type _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>参数

`_Off` 要查找有关相对于位置`_Way`。 有关详细信息，请参阅 [basic_stringbuf::off_type](#off_type)。

`_Way` 偏移操作起点。 请参阅 [ios_base::seekdir](../standard-library/ios-base-class.md#seekdir)，查看可能的值。

`_Mode` 指定指针位置的模式。 默认允许修改读取和写入位置。 有关详细信息，请参阅 [ios_base::openmode](../standard-library/ios-base-class.md#openmode)。

### <a name="return-value"></a>返回值

返回新位置或无效的流位置。

### <a name="remarks"></a>备注

对于 `basic_stringbuf<Elem, Tr, Alloc>` 类的对象，流位置仅包含流偏移量。 如果偏移量为零，将指定受控序列的第一个元素。

确定新位置，如下所示：

- 如果 `_Way` == `ios_base::beg`，新的位置是流开头加上 `_Off`。

- 如果 `_Way` == `ios_base::cur`，新的位置是当前流位置加上 `_Off`。

- 如果 `_Way` == `ios_base::end`，新的位置是当前流结尾位置加上 `_Off`。

如果 `_Mode & ios_base::in` 是非零值，则函数更改下一个位置以在输入缓冲区中读取。 如果 `_Mode & ios_base::out` 是非零值，则函数更改下一个位置以在输出缓冲区中写入。 要使流受影响，其必须存在缓冲区。 若要成功执行定位操作，则结果流的位置必须位于受控序列内。 如果函数影响两个流位置，则 `_Way` 必须是 `ios_base::beg` 或 `ios_base::end`，且将两个流定位在同一个元素中。 否则（或者如果两个位置均不受影响），定位操作失败。

如果此函数成功更改任何一个流位置或两个流位置，则返回结果流位置。 否则，如果失败将返回一个无效的流位置。

## <a name="seekpos"></a>  basic_stringbuf::seekpos

受保护虚拟成员函数尝试更改受控制流的当前位置。

```cpp
virtual pos_type seekpos(pos_type _Sp, ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>参数

`_Sp` 要搜寻的位置。

`_Mode` 指定指针位置的模式。 默认允许修改读取和写入位置。

### <a name="return-value"></a>返回值

如果此函数成功更改任何一个流位置或两个流位置，则返回结果流位置。 否则，如果失败将返回一个无效的流位置。 若要确定流位置是否有效，请比较返回值和 `pos_type(off_type(-1))`。

### <a name="remarks"></a>备注

对于 basic_stringbuf< **Elem**, **Tr**, `Alloc`> 类的对象，流位置只包含流偏移量。 如果偏移量为零，将指定受控序列的第一个元素。 新位置由 _ *Sp* 确定。

如果 **mode & ios_base::in** 是非零值，则函数更改下一个位置以在输入缓冲区中读取。 如果 **mode & ios_base::out** 是非零值，则函数更改下一个位置以在输出缓冲区中写入。 要使流受影响，其必须存在缓冲区。 若要成功执行定位操作，则结果流的位置必须位于受控序列内。 否则（或者如果两个位置均不受影响），定位操作失败。

## <a name="str"></a>  basic_stringbuf::str

设置或获取字符串缓冲区中的文本，而无需更改写入位置。

```cpp
basic_string<Elem, Tr, Alloc> str() const;
void str(
    const basic_string<Elem, Tr, Alloc>& _Newstr);
```

### <a name="parameters"></a>参数

`_Newstr` 新的字符串。

### <a name="return-value"></a>返回值

返回 [basic_string](../standard-library/basic-string-class.md)\< **Elem**, **Tr**, Alloc **>,** 类的对象，它的受控序列是 **\*this** 控制的序列副本。

### <a name="remarks"></a>备注

第一个成员函数返回 basic_string< **Elem**, **Tr**, `Alloc`> 类的对象，其受控序列是 **\*this** 控制的序列副本。 复制的序列取决于存储的 stringbuf 模式：

- 如果 **mode & ios_base::out** 是非零值且存在输出缓冲区，则序列是整个输出缓冲区（以 `pbase` 开头的 [epptr](../standard-library/basic-streambuf-class.md#epptr) - [pbase](../standard-library/basic-streambuf-class.md#pbase) 元素）。

- 如果 **mode & ios_base::in** 是非零值且存在输入缓冲区，则序列是整个输入缓冲区（以 `eback` 开头的 [egptr](../standard-library/basic-streambuf-class.md#egptr) - [eback](../standard-library/basic-streambuf-class.md#eback) 元素）。

- 否则，复制的序列为空。

第二个成员函数释放当前由 **\*this** 控制的任何序列。 然后它分配由 `_Newstr` 控制的序列副本。 如果 **mode & ios_base::in** 是非零值，则其将输入缓冲区设置为在序列的开头开始读取。 如果 **mode & ios_base::out** 是非零值，则其将输出缓冲区设置为在序列的开头开始写入。

### <a name="example"></a>示例

```cpp
// basic_stringbuf_str.cpp
// compile with: /EHsc
#include <iostream>
#include <sstream>

using namespace std;

int main( )
{
   basic_string<char> i( "test" );
   stringstream ss;

   ss.rdbuf( )->str( i );
   cout << ss.str( ) << endl;

   ss << "z";
   cout << ss.str( ) << endl;

   ss.rdbuf( )->str( "be" );
   cout << ss.str( ) << endl;
}
```

```Output
test
zest
be
```

## <a name="traits_type"></a>  basic_stringbuf::traits_type

将类型名与 **Tr** 模板参数关联。

```cpp
typedef Tr traits_type;
```

### <a name="remarks"></a>备注

该类型是模板参数 **Tr** 的同义词。

## <a name="underflow"></a>  basic_stringbuf::underflow

受保护虚函数从输入流中提取当前元素。

```cpp
virtual int_type underflow();
```

### <a name="return-value"></a>返回值

如果该函数不成功，它将返回 **traits_type::**[eof](../standard-library/char-traits-struct.md#eof)。 否则，它返回输入流中的已转换的当前元素。

### <a name="remarks"></a>备注

受保护的虚拟成员函数尝试从输入缓冲区提取当前元素 **byte**，提出当前流位置，并返回元素作为 **traits_type::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( **byte**)。 它可以一种方式进行此操作：如果读取位置可用，它采用 **byte** 作为存储在读取位置中的元素，并提出输入缓冲区的下一个指针。

## <a name="swap"></a>  basic_streambuf::swap

将此字符串缓冲区与另一个字符串缓冲区的内容交换。

```cpp
void basic_stringbuf<T>::swap(basic_stringbuf& other)
```

### <a name="parameters"></a>参数

`other` 与此 basic_stringbuf basic_stringbuf 将切换其内容。

### <a name="remarks"></a>备注

## <a name="op_eq"></a>  basic_stringbuf::operator=

将运算符右侧的 basic_stringbuf 内容赋予左侧的 basic_stringbuf。

```cpp
basic_stringbuf& basic_stringbuf:: operator=(const basic_stringbuf& other)
```

### <a name="parameters"></a>参数

`other` 其内容，包括区域设置特征，将分配给该运算符左侧的 stringbuf basic_stringbuf。

### <a name="remarks"></a>备注

## <a name="see-also"></a>请参阅

[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream 编程](../standard-library/iostream-programming.md)<br/>
[iostreams 约定](../standard-library/iostreams-conventions.md)<br/>

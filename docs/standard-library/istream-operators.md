---
title: '&lt;istream&gt; 运算符'
ms.date: 11/04/2016
f1_keywords:
- istream/std::operator&gt;&gt;
ms.assetid: 7174da41-f301-4a34-b631-0ab918b188d2
ms.openlocfilehash: c10692194c80051b10ecbe776c7d23a03860d508
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447789"
---
# <a name="ltistreamgt-operators"></a>&lt;istream&gt; 运算符

## <a name="op_gt_gt"></a>  operator&gt;&gt;

从流中提取字符和字符串。

```cpp
template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr,
    Elem* str);

template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr,
    Elem& Ch);

template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr,
    signed char* str);

template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr,
    signed char& Ch);

template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr,
    unsigned char* str);

template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr,
    unsigned char& Ch);

template <class Elem, class Tr, class Type>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<char, Tr>&& Istr,
    Type& val);
```

### <a name="parameters"></a>参数

*48*\
一个字符。

*Istr*\
一个流。

*字符串*\
一个字符串。

*初始值*\
一种类型。

### <a name="return-value"></a>返回值

流

### <a name="remarks"></a>备注

`basic_istream` 类还定义多个提取运算符。 有关详细信息，请参阅 [basic_istream::operator>>](../standard-library/basic-istream-class.md#op_gt_gt)。

模板函数：

```cpp
template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr, Elem* str);
```

提取多达 *N* - 1 个元素，并将其存储在以 _ *Str* 开始的数组中。 如果 `Istr`. [width](../standard-library/ios-base-class.md#width) 大于 0，则 *N* 为 `Istr`. **width**;否则, 它是可声明`Elem`的最大数组的大小。 函数始终将值`Elem()`存储在它存储的任何提取的元素之后。 遇到文件末尾、值为 **Elem**(0) 的字符（不会被提取）或会被 [ws](../standard-library/istream-functions.md#ws) 放弃的任何元素（不会被提取）时，提取会提前结束。 如果此函数没有提取任何元素，则会调用 `Istr`. [setstate](../standard-library/basic-ios-class.md#setstate)(**failbit**)。 在任何情况下，它调用 `Istr`. **宽度**(0) 并返回*Istr*。

**安全说明**要从输入流中提取的以 null 结尾的字符串不得超过目标缓冲区*str*的大小。 有关详细信息，请参阅 [避免缓冲区溢出](/windows/desktop/SecBP/avoiding-buffer-overruns)。

模板函数：

```cpp
template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr, Elem& Ch);
```

如果可能, 则提取一个元素, 并将其存储在*Ch*中。 否则，会调用 **is**. [setstate](../standard-library/basic-ios-class.md#setstate)( **failbit**)。 在任何情况下, 它都将返回*Istr*。

模板函数：

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, signed char* str);
```

返回 `Istr >> ( char * ) str`。

模板函数：

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, signed char& Ch);
```

返回 `Istr >> ( char& ) Ch`。

模板函数：

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, unsigned char* str);
```

返回 `Istr >> ( char * ) str`。

模板函数：

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, unsigned char& Ch);
```

返回 `Istr >> ( char& ) Ch`。

模板函数：

```cpp
template <class Elem, class Tr, class Type>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<char, Tr>&& Istr,
    Type& val);
```

返回`Istr >> val` (并将右值`Istr`引用转换为进程中的左值)。

### <a name="example"></a>示例

```cpp
// istream_op_extract.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   ws( cin );
   char c[10];

   cin.width( 9 );
   cin >> c;
   cout << c << endl;
}
```

## <a name="see-also"></a>请参阅

[\<istream>](../standard-library/istream.md)

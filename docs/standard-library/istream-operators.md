---
title: '&lt;istream&gt; 运算符'
ms.date: 11/04/2016
f1_keywords:
- istream/std::operator&gt;&gt;
ms.assetid: 7174da41-f301-4a34-b631-0ab918b188d2
ms.openlocfilehash: 3b9521fde1b5a03389bfc1ad3e35fa407d9d6ac0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363041"
---
# <a name="ltistreamgt-operators"></a>&lt;istream&gt; 运算符

## <a name="operatorgtgt"></a><a name="op_gt_gt"></a>算子&gt;&gt;

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

*Ch*\
一个字符。

*Istr*\
一个流。

*Str*\
一个字符串。

*瓦尔*\
一种类型。

### <a name="return-value"></a>返回值

流

### <a name="remarks"></a>备注

`basic_istream` 类还定义多个提取运算符。 有关详细信息，请参阅 [basic_istream::operator>>](../standard-library/basic-istream-class.md#op_gt_gt)。

函数模板：

```cpp
template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr, Elem* str);
```

提取到`N - 1`元素，并将它们存储在数组中，从*str*开始。 如果`Istr.`[宽度](../standard-library/ios-base-class.md#width)大于零，则*N* `Istr.width`是 ;否则，它是可以声明的最大`Elem`数组的大小。 该函数始终在它存储`Elem()`的任何提取元素后存储该值。 提取在文件末尾的早期停止，在值`Elem(0)`（未提取）的字符上，或 ws 将丢弃的任何元素（未提取） 上停止。 [ws](../standard-library/istream-functions.md#ws) 如果函数不提取任何元素，它将调用`Istr.`[`setstate`](../standard-library/basic-ios-class.md#setstate)`(failbit)`。 在任何情况下，它调用`Istr.width(0)`并返回*Istr*。

**安全说明**从输入流中提取的 null 端接字符串不得超过目标缓冲区*str*的大小。 有关详细信息，请参阅 [避免缓冲区溢出](/windows/win32/SecBP/avoiding-buffer-overruns)。

函数模板：

```cpp
template <class Elem, class Tr>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr, Elem& Ch);
```

提取元素（如果可能）并将其存储在*Ch*中。 否则，它将调用`is.`[`setstate`](../standard-library/basic-ios-class.md#setstate)`(failbit)`。 在任何情况下，它返回*Istr*。

函数模板：

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, signed char* str);
```

返回 `Istr >> ( char * ) str`。

函数模板：

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, signed char& Ch);
```

返回 `Istr >> ( char& ) Ch`。

函数模板：

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, unsigned char* str);
```

返回 `Istr >> ( char * ) str`。

函数模板：

```cpp
template <class Tr>
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, unsigned char& Ch);
```

返回 `Istr >> ( char& ) Ch`。

函数模板：

```cpp
template <class Elem, class Tr, class Type>
basic_istream<Elem, Tr>& operator>>(
    basic_istream<char, Tr>&& Istr,
    Type& val);
```

返回`Istr >> val`（并将 rvalue 引用`Istr`转换为进程中的 lvalue）。

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

## <a name="see-also"></a>另请参阅

[\<istream>](../standard-library/istream.md)

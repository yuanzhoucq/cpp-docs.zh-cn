---
title: '&lt;ostream&gt; 函数'
ms.date: 11/04/2016
f1_keywords:
- ostream/std::swap
- ostream/std::endl
- ostream/std::ends
- ostream/std::flush
ms.assetid: d6e56cc0-c8df-4dbe-be10-98e14c35ed3a
helpviewer_keywords:
- std::swap [C++]
- std::endl [C++]
- std::ends [C++]
- std::flush [C++]
ms.openlocfilehash: 8d93e46b0323058d93c6d0bd8c1ee566998aef61
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78874786"
---
# <a name="ltostreamgt-functions"></a>&lt;ostream&gt; 函数

这些是 &lt;ostream&gt;中定义的全局模板函数。 有关成员函数的详细说明，请参阅[Basic_ostream 类](basic-ostream-class.md)文档。

||||
|-|-|-|
|[endl](#endl)|[ends](#ends)|[flush](#flush)|
|[swap](#swap)|

## <a name="endl"></a>endl

终止行并刷新缓冲区。

```cpp
template class<Elem, Tr>
basic_ostream<Elem, Tr>& endl(
   basic_ostream<Elem, Tr>& Ostr);
```

### <a name="parameters"></a>参数

*Elem*\
元素类型。

*Ostr*\
**Basic_ostream**类型的对象。

*Tr*\
字符特征。

### <a name="return-value"></a>返回值

**Basic_ostream**类型的对象。

### <a name="remarks"></a>备注

操控器调用*Ostr*。[put](../standard-library/basic-ostream-class.md#put)（*Ostr*。[加宽](../standard-library/basic-ios-class.md#widen)（' \n '）），然后调用*Ostr*。[flush](../standard-library/basic-ostream-class.md#flush)。 它将返回*Ostr*。

### <a name="example"></a>示例

```cpp
// ostream_endl.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   cout << "testing" << endl;
}
```

```Output
testing
```

## <a name="ends"></a>结尾

终止字符串。

```cpp
template class<Elem, Tr>
basic_ostream<Elem, Tr>& ends(
   basic_ostream<Elem, Tr>& Ostr);
```

### <a name="parameters"></a>参数

*Elem*\
元素类型。

*Ostr*\
一个 `basic_ostream` 类型的对象。

*Tr*\
字符特征。

### <a name="return-value"></a>返回值

一个 `basic_ostream` 类型的对象。

### <a name="remarks"></a>备注

操控器调用*Ostr*。[put](../standard-library/basic-ostream-class.md#put)（*Elem*（' \ 0 '））。 它将返回*Ostr*。

### <a name="example"></a>示例

```cpp
// ostream_ends.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   cout << "a";
   cout << "b" << ends;
   cout << "c" << endl;
}
```

```Output
ab c
```

## <a name="flush"></a>flush

刷新缓冲区。

```cpp
template class<Elem, Tr>
basic_ostream<Elem, Tr>& flush(
   basic_ostream<Elem, Tr>& Ostr);
```

### <a name="parameters"></a>参数

*Elem*\
元素类型。

*Ostr*\
一个 `basic_ostream` 类型的对象。

*Tr*\
字符特征。

### <a name="return-value"></a>返回值

一个 `basic_ostream` 类型的对象。

### <a name="remarks"></a>备注

操控器调用*Ostr*。[flush](../standard-library/basic-ostream-class.md#flush)。 它将返回*Ostr*。

### <a name="example"></a>示例

```cpp
// ostream_flush.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   cout << "testing" << flush;
}
```

```Output
testing
```

## <a name="swap"></a>交换

交换两个 `basic_ostream` 对象的值。

```cpp
template <class Elem, class Tr>
void swap(
   basic_ostream<Elem, Tr>& left,
   basic_ostream<Elem, Tr>& right);
```

### <a name="parameters"></a>参数

*Elem*\
元素类型。

*Tr*\
字符特征。

*左*\
对 `basic_ostream` 对象的左值引用。

*right*\
对 `basic_ostream` 对象的左值引用。

### <a name="remarks"></a>备注

模板函数 `swap` 执行 `left.swap(right)`。

## <a name="see-also"></a>另请参阅

[\<ostream>](../standard-library/ostream.md)

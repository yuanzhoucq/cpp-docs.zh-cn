---
title: istreambuf_iterator 类
ms.date: 11/04/2016
f1_keywords:
- streambuf/std::istreambuf_iterator
- iterator/std::istreambuf_iterator::char_type
- iterator/std::istreambuf_iterator::int_type
- iterator/std::istreambuf_iterator::istream_type
- iterator/std::istreambuf_iterator::streambuf_type
- iterator/std::istreambuf_iterator::traits_type
- iterator/std::istreambuf_iterator::equal
helpviewer_keywords:
- std::istreambuf_iterator [C++]
- std::istreambuf_iterator [C++], char_type
- std::istreambuf_iterator [C++], int_type
- std::istreambuf_iterator [C++], istream_type
- std::istreambuf_iterator [C++], streambuf_type
- std::istreambuf_iterator [C++], traits_type
- std::istreambuf_iterator [C++], equal
ms.assetid: 39002da2-61a6-48a5-9d0c-5df8271f6038
ms.openlocfilehash: 3b839126b7b5541c3a9dd033fcbbc8221bde7c22
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689463"
---
# <a name="istreambuf_iterator-class"></a>istreambuf_iterator 类

类模板 istreambuf_iterator 描述一个输入迭代器对象，该对象可从输入流缓冲区（通过它存储的对象访问）提取字符元素、指向 `basic_streambuf` \< **CharType**、**特征**>.

## <a name="syntax"></a>语法

```cpp
template <class CharType class Traits = char_traits <CharType>>
class istreambuf_iterator
: public iterator<input_iterator_tag, CharType, typename Traits ::off_type, CharType*, CharType&>
```

### <a name="parameters"></a>参数

*CharType* \
一种类型，此类型表示 istreambuf_iterator 的字符类型。

*特征*\
一种类型，此类型表示 istreambuf_iterator 的字符类型。 此自变量是可选自变量，默认值为 `char_traits`\<*CharType>。*

## <a name="remarks"></a>备注

istreambuf_iterator 类必须满足输入迭代器的需求。

构造或递增带有非 null 存储指针的 istreambuf_iterator 类对象后，此对象将有效尝试从关联的输入流提取和存储 *CharType* 类型的对象。 不过，提取可能会延迟到实际取消引用对象或复制对象后进行。 如果提取失败，对象将使用 null 指针有效替换存储指针，从而设置序列末尾指示符。

### <a name="constructors"></a>构造函数

|构造函数|描述|
|-|-|
|[istreambuf_iterator](#istreambuf_iterator)|构造初始化为从输入流读取字符的 `istreambuf_iterator`。|

### <a name="typedefs"></a>Typedef

|类型名称|描述|
|-|-|
|[char_type](#char_type)|为 `ostreambuf_iterator` 的字符类型提供的类型。|
|[int_type](#int_type)|为 `istreambuf_iterator` 提供整数类型的类型。|
|[istream_type](#istream_type)|为 `istream_iterator` 的流类型提供的类型。|
|[streambuf_type](#streambuf_type)|为 `istreambuf_iterator` 的流类型提供的类型。|
|[traits_type](../standard-library/istream-iterator-class.md#traits_type)|为 `istream_iterator` 的字符特征类型提供的类型。|

### <a name="member-functions"></a>成员函数

|成员函数|描述|
|-|-|
|[equal](#equal)|对于两个输入流缓冲区迭代器是否相等的测试。|

### <a name="operators"></a>运算符

|运算符|描述|
|-|-|
|[operator*](#op_star)|取消引用运算符将返回流中的下一字符。|
|[operator++](#op_add_add)|返回输入流中的下一字符或者在递增对象前复制对象并返回副本。|
|[operator->](#op_arrow)|返回成员的值（如果有）。|

## <a name="requirements"></a>要求

**标头：** \<iterator>

**命名空间:** std

## <a name="char_type"></a>istreambuf_iterator::char_type

为 `ostreambuf_iterator` 的字符类型提供的类型。

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>备注

该类型是模板参数 *CharType* 的同义词。

### <a name="example"></a>示例

```cpp
// istreambuf_iterator_char_type.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>
#include <algorithm>

int main( )
{
   using namespace std;

   typedef istreambuf_iterator<char>::char_type CHT1;
   typedef istreambuf_iterator<char>::traits_type CHTR1;

   cout << "(Try the example: 'So many dots to be done'\n"
        << " then an Enter key to insert into the output,\n"
        << " & use a ctrl-Z Enter key combination to exit): ";

   // istreambuf_iterator for input stream
   istreambuf_iterator< CHT1, CHTR1> charInBuf ( cin );
   ostreambuf_iterator<char> charOut ( cout );

   // Used in conjunction with replace_copy algorithm
   // to insert into output stream and replace spaces
   // with dot-separators
   replace_copy ( charInBuf , istreambuf_iterator<char>( ),
        charOut , ' ' , '.' );
}
```

## <a name="equal"></a>istreambuf_iterator::equal

测试：两个输入流缓冲区迭代器是否相等。

```cpp
bool equal(const istreambuf_iterator<CharType, Traits>& right) const;
```

### <a name="parameters"></a>参数

*right* \
要针对其检查相等性的迭代器。

### <a name="return-value"></a>返回值

如果两个 `istreambuf_iterator` 都是流末尾迭代器或都不是流末尾迭代器，则为 **true**；否则为 **false**。

### <a name="remarks"></a>备注

范围由 `istreambuf_iterator` 定义到当前位置和流末尾迭代器，但由于所有非结束流迭代器都等效于 `equal` 成员函数，因此不能使用 `istreambuf_iterator`s 定义任何子范围。 `==` 和 `!=` 运算符具有相同的语义。

### <a name="example"></a>示例

```cpp
// istreambuf_iterator_equal.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

int main( )
{
   using namespace std;

   cout << "(Try the example: 'Hello world!'\n"
        << " then an Enter key to insert into the output,\n"
        << " & use a ctrl-Z Enter key combination to exit): ";

   istreambuf_iterator<char> charReadIn1 ( cin );
   istreambuf_iterator<char> charReadIn2 ( cin );

   bool b1 = charReadIn1.equal ( charReadIn2 );

   if (b1)
      cout << "The iterators are equal." << endl;
   else
      cout << "The iterators are not equal." << endl;
}
```

## <a name="int_type"></a>istreambuf_iterator::int_type

为 `istreambuf_iterator` 提供整数类型的类型。

```cpp
typedef typename traits_type::int_type int_type;
```

### <a name="remarks"></a>备注

该类型是 `Traits::int_type`的同义词。

### <a name="example"></a>示例

```cpp
// istreambuf_iterator_int_type.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

int main( )
{
   using namespace std;
   istreambuf_iterator<char>::int_type inttype1 = 100;
   cout << "The inttype1 = " << inttype1 << "." << endl;
}
/* Output:
The inttype1 = 100.
*/
```

## <a name="istream_type"></a>istreambuf_iterator::istream_type

为 `istreambuf_iterator` 的流类型提供的类型。

```cpp
typedef basic_istream<CharType, Traits> istream_type;
```

### <a name="remarks"></a>备注

该类型是 `basic_istream`\< **CharType**, **Traits**> 的同义词。

### <a name="example"></a>示例

有关如何声明和使用 `istream_type` 的示例，请参阅 [istreambuf_iterator](#istreambuf_iterator)。

## <a name="istreambuf_iterator"></a>istreambuf_iterator::istreambuf_iterator

构造一个 istreambuf_iterator，会将其初始化以从输入流读取字符。

```cpp
istreambuf_iterator(streambuf_type* strbuf = 0) throw();
istreambuf_iterator(istream_type& _Istr) throw();
```

### <a name="parameters"></a>参数

*strbuf* \
`istreambuf_iterator` 要附加到的输入流缓冲区。

*_Istr* \
`istreambuf_iterator` 要附加到的输入流。

### <a name="remarks"></a>备注

第一个构造函数通过*strbuf*初始化输入流缓冲区指针。 第二个构造函数通过 *_Istr*初始化输入流缓冲区指针。 `rdbuf`，最终会尝试提取并存储 `CharType` 类型的对象。

### <a name="example"></a>示例

```cpp
// istreambuf_iterator_istreambuf_iterator.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <algorithm>
#include <iostream>

int main( )
{
   using namespace std;

   // Following declarations will not compile:
   istreambuf_iterator<char>::istream_type &istrm = cin;
   istreambuf_iterator<char>::streambuf_type *strmbf = cin.rdbuf( );

   cout << "(Try the example: 'Oh what a world!'\n"
      << " then an Enter key to insert into the output,\n"
      << " & use a ctrl-Z Enter key combination to exit): ";
   istreambuf_iterator<char> charReadIn ( cin );
   ostreambuf_iterator<char> charOut ( cout );

   // Used in conjunction with replace_copy algorithm
   // to insert into output stream and replace spaces
   // with hyphen-separators
   replace_copy ( charReadIn , istreambuf_iterator<char>( ),
      charOut , ' ' , '-' );
}
```

## <a name="op_star"></a>istreambuf_iterator::operator*

取消引用运算符将返回流中的下一字符。

```cpp
CharType operator*() const;
```

### <a name="return-value"></a>返回值

流中的下一个字符。

### <a name="example"></a>示例

```cpp
// istreambuf_iterator_operator_deref.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

int main( )
{
   using namespace std;

   cout << "Type string of characters & enter to output it,\n"
      << " with stream buffer iterators,(try: 'I'll be back.')\n"
      << " repeat as many times as desired,\n"
      << " then keystroke ctrl-Z Enter to exit program: ";
   istreambuf_iterator<char> inpos ( cin );
   istreambuf_iterator<char> endpos;
   ostreambuf_iterator<char> outpos ( cout );
   while ( inpos != endpos )
   {
*outpos = *inpos;   //Put value of outpos equal to inpos
      ++inpos;
      ++outpos;
   }
}
```

## <a name="op_add_add"></a>istreambuf_iterator::operator++

返回输入流中的下一字符或者在递增对象前复制对象并返回副本。

```cpp
istreambuf_iterator<CharType, Traits>& operator++();
istreambuf_iterator<CharType, Traits> operator++(int);
```

### <a name="return-value"></a>返回值

`istreambuf_iterator` 或对 `istreambuf_iterator` 的引用。

### <a name="remarks"></a>备注

第一个运算符最终尝试从关联的输入流提取和存储类型 `CharType` 的对象。 第二个运算符生成对象的副本，递增对象，然后返回副本。

### <a name="example"></a>示例

```cpp
// istreambuf_iterator_operator_incr.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

int main( )
{
   using namespace std;

   cout << "Type string of characters & enter to output it,\n"
      << " with stream buffer iterators,(try: 'I'll be back.')\n"
      << " repeat as many times as desired,\n"
      << " then keystroke ctrl-Z Enter to exit program: ";
   istreambuf_iterator<char> inpos ( cin );
   istreambuf_iterator<char> endpos;
   ostreambuf_iterator<char> outpos ( cout );
   while ( inpos != endpos )
   {
*outpos = *inpos;
      ++inpos;   //Increment istreambuf_iterator
      ++outpos;
   }
}
```

## <a name="op_arrow"></a>istreambuf_iterator::operator-&gt;

返回成员的值（如果有）。

```cpp
const Elem* operator->() const;
```

### <a name="return-value"></a>返回值

运算符返回 **&\*\*this**。

## <a name="streambuf_type"></a>istreambuf_iterator::streambuf_type

为 istreambuf_iterator 的流类型提供的类型。

```cpp
typedef basic_streambuf<CharType, Traits> streambuf_type;
```

### <a name="remarks"></a>备注

该类型是 `basic_streambuf`\< **CharType**, **Traits**> 的同义词。

### <a name="example"></a>示例

有关如何声明和使用 `istreambuf_type` 的示例，请参阅 [istreambuf_iterator](#istreambuf_iterator)。

## <a name="traits_type"></a>istreambuf_iterator::traits_type

为 `istream_iterator` 的字符特征类型提供的类型。

```cpp
typedef Traits traits_type;
```

### <a name="remarks"></a>备注

该类型是模板参数 *Traits* 的同义词。

### <a name="example"></a>示例

```cpp
// istreambuf_iterator_traits_type.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>
#include <algorithm>

int main( )
{
   using namespace std;

   typedef istreambuf_iterator<char>::char_type CHT1;
   typedef istreambuf_iterator<char>::traits_type CHTR1;

   cout << "(Try the example: 'So many dots to be done'\n"
        << " then an Enter key to insert into the output,\n"
        << " & use a ctrl-Z Enter key combination to exit): ";

   // istreambuf_iterator for input stream
   istreambuf_iterator< CHT1, CHTR1> charInBuf ( cin );
   ostreambuf_iterator<char> charOut ( cout );

   // Used in conjunction with replace_copy algorithm
   // to insert into output stream and replace spaces
   // with dot-separators
   replace_copy ( charInBuf , istreambuf_iterator<char>( ),
        charOut , ' ' , '.' );
}
```

## <a name="see-also"></a>请参阅

[iterator 结构](../standard-library/iterator-struct.md)\
[\<iterator>](../standard-library/iterator.md)\
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)

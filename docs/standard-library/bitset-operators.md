---
title: '&lt;bitset&gt; 运算符'
ms.date: 11/04/2016
f1_keywords:
- bitset/std::operator&amp;
- bitset/std::operator&gt;&gt;
- bitset/std::operator&lt;&lt;
- bitset/std::operator^
- bitset/std::operator|
ms.assetid: 84fe6a13-6f6e-4cdc-bf8f-6f65ab1134d4
helpviewer_keywords:
- std::operator&amp; (bitset)
- std::operator&gt;&gt; (bitset)
- std::operator&lt;&lt; (bitset)
ms.openlocfilehash: c51bc5ecf2bc3a74b25a06320f0ca8fd64749f5d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50531139"
---
# <a name="ltbitsetgt-operators"></a>&lt;bitset&gt; 运算符

||||
|-|-|-|
|[operator&amp;](#op_amp)|[operator&gt;&gt;](#op_gt_gt)|[operator&lt;&lt;](#op_lt_lt)|
|[operator^](#op_xor)|[operator|](#op_or)|

## <a name="op_amp"></a>operator&amp;

执行两个位组间的按位 `AND`。

```cpp
template <size_t size>
bitset<size>
operator&(
    const bitset<size>& left,
    const bitset<size>& right);
```

### <a name="parameters"></a>参数

*left*<br/>
要将其各自的元素使用按位 `AND` 组合的两个位组中的第一个。

*right*<br/>
要将其各自的元素使用按位 `AND` 组合的两个 valarray 中的第二个。

### <a name="return-value"></a>返回值

其元素是执行的结果的位`AND`操作的相应元素*左*并*右*。

### <a name="example"></a>示例

```cpp
// bitset_and.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>
#include <string>

using namespace std;

int main()
{
   bitset<4> b1 ( string("0101") );
   bitset<4> b2 ( string("0011") );
   bitset<4> b3 = b1 & b2;
   cout << "bitset 1: " << b1 << endl;
   cout << "bitset 2: " << b2 << endl;
   cout << "bitset 3: " << b3 << endl;
}
```

```Output
bitset 1: 0101
bitset 2: 0011
bitset 3: 0001
```

## <a name="op_lt_lt"></a>  operator&lt;&lt;

将位序列的文本表示形式插入到输出流中。

```

template <class CharType, class Traits, size_t N>
basic_ostream<CharType, Traits>& operator<<(
    basic_ostream<CharType, Traits>& ostr,
    const bitset<N>& right);
```

### <a name="parameters"></a>参数

*right*<br/>
要作为字符串插入到输出流的 **bitset\<N>** 类型的对象。

### <a name="return-value"></a>返回值

将位序列中的文本表示形式`ostr`。

### <a name="remarks"></a>备注

模板函数重载`operator<<`，允许将位组不必先转换为字符串即可写出。 该模板函数有效执行以下操作：

**ostr** << _ *Right*. [to_string](bitset-class.md) < **CharType**, **Traits**, **allocator**\< **CharType**> > ( )

### <a name="example"></a>示例

```cpp
// bitset_op_insert.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 9 );

   // bitset inserted into output stream directly
   cout << "The ordered set of bits in the bitset<5> b1(9)"
        << "\n can be output with the overloaded << as: ( "
        << b1 << " )" << endl;

   // Compare converting bitset to a string before
   // inserting it into the output steam
   string s1;
   s1 =  b1.template to_string<char,
      char_traits<char>, allocator<char> >( );
   cout << "The string returned from the bitset b1"
        << "\n by the member function to_string( ) is: "
        << s1 << "." << endl;
}
```

## <a name="op_gt_gt"></a>  operator&gt;&gt;

将位字符的字符串读入位组。

```

template <class CharType, class Traits, size_t Bits>
basic_istream<CharType, Traits>& operator>> (
    basic_istream<CharType, Traits>&
_Istr,
    bitset<N>&
    right);
```

### <a name="parameters"></a>参数

*_Istr*<br/>
输入到输入流以插入位组的字符串。

*right*<br/>
正在从输入流接收位的位组。

### <a name="return-value"></a>返回值

模板函数返回字符串 *_Istr*。

### <a name="remarks"></a>备注

模板函数重载`operator>>`将存储在位组 _*右*值 bitset (`str`)，其中`str`是类型的对象[basic_string](basic-string-class.md)  < **CharType**，**特征**，**分配器**\< **CharType**>>  **&** 从提取 *_Istr*。

模板函数没有提取中的元素 *_Istr*并将其插入位组，直至：

- 已从输入流提取所有的位元素并将其存储在位组中。

- 此位组由输入流中的位填充。

- 遇到非 0 也非 1 的输入元素。

### <a name="example"></a>示例

```cpp
#include <bitset>
#include <iostream>
#include <string>

using namespace std;
int main()
{

   bitset<5> b1;
   cout << "Enter string of (0 or 1) bits for input into bitset<5>.\n"
        << "Try bit string of length less than or equal to 5,\n"
        << " (for example: 10110): ";
   cin >>  b1;

   cout << "The ordered set of bits entered from the "
        << "keyboard\n has been input into bitset<5> b1 as: ( "
        << b1 << " )" << endl;

   // Truncation due to longer string of bits than length of bitset
   bitset<2> b3;
   cout << "Enter string of bits (0 or 1) for input into bitset<2>.\n"
        << " Try bit string of length greater than 2,\n"
        << " (for example: 1011): ";
   cin >>  b3;

   cout << "The ordered set of bits entered from the "
        << "keyboard\n has been input into bitset<2> b3 as: ( "
        << b3 << " )" << endl;

   // Flushing the input stream
   char buf[100];
   cin.getline(&buf[0], 99);

   // Truncation with non-bit value
   bitset<5> b2;
   cout << "Enter a string for input into  bitset<5>.\n"
        << " that contains a character than is NOT a 0 or a 1,\n "
        << " (for example: 10k01): ";
   cin >>  b2;

   cout << "The string entered from the keyboard\n"
        << " has been input into bitset<5> b2 as: ( "
        << b2 << " )" << endl;
}
```

## <a name="op_xor"></a>operator^

执行两个位组间的按位 `EXCLUSIVE-OR`。

```cpp
template <size_t size>
bitset<size>
operator^(
    const bitset<size>& left,
    const bitset<size>& right);
```

### <a name="parameters"></a>参数

*left*<br/>
要将其各自的元素使用按位 `EXCLUSIVE-OR` 组合的两个位组中的第一个。

*right*<br/>
要将其各自的元素使用按位 `EXCLUSIVE-OR` 组合的两个 valarray 中的第二个。

### <a name="return-value"></a>返回值

其元素是执行的结果的位`EXCLUSIVE-OR`操作的相应元素*左*并*右*。

### <a name="example"></a>示例

```cpp
// bitset_xor.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>
#include <string>

using namespace std;

int main()
{
   bitset<4> b1 ( string("0101") );
   bitset<4> b2 ( string("0011") );
   bitset<4> b3 = b1 ^ b2;
   cout << "bitset 1: " << b1 << endl;
   cout << "bitset 2: " << b2 << endl;
   cout << "bitset 3: " << b3 << endl;
}
```

```Output
bitset 1: 0101
bitset 2: 0011
bitset 3: 0110
```

## <a name="op_or"></a>  运算符 |

执行两个位组间的按位 `OR`。

```cpp
template <size_t size>
bitset<size>
operator|(
    const bitset<size>& left,
    const bitset<size>& right);
```

### <a name="parameters"></a>参数

*left*<br/>
要将其各自的元素使用按位 `OR` 组合的两个位组中的第一个。

*right*<br/>
要将其各自的元素使用按位 `OR` 组合的两个 valarray 中的第二个。

### <a name="return-value"></a>返回值

其元素是执行的结果的位`OR`操作的相应元素*左*并*右*。

### <a name="example"></a>示例

```cpp
// bitset_or.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>
#include <string>

using namespace std;

int main()
{
   bitset<4> b1 ( string("0101") );
   bitset<4> b2 ( string("0011") );
   bitset<4> b3 = b1 | b2;
   cout << "bitset 1: " << b1 << endl;
   cout << "bitset 2: " << b2 << endl;
   cout << "bitset 3: " << b3 << endl;
}
```

```Output
bitset 1: 0101
bitset 2: 0011
bitset 3: 0111
```

## <a name="see-also"></a>请参阅

[\<bitset>](../standard-library/bitset.md)<br/>

---
title: "bitset 类 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- bitset/std::bitset
- bitset
- bitset/std::bitset::element_type
- bitset/std::bitset::all
- bitset/std::bitset::any
- bitset/std::bitset::count
- bitset/std::bitset::flip
- bitset/std::bitset::none
- bitset/std::bitset::reset
- bitset/std::bitset::set
- bitset/std::bitset::size
- bitset/std::bitset::test
- bitset/std::bitset::to_string
- bitset/std::bitset::to_ullong
- bitset/std::bitset::to_ulong
- bitset/std::bitset::reference
dev_langs:
- C++
helpviewer_keywords:
- bitset class
ms.assetid: 28b86964-87b4-429c-8124-b6c251b6c50b
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: 8e3518fb40cdd3e8bdd14b5ed64f4cc6dbcb1058
ms.contentlocale: zh-cn
ms.lasthandoff: 04/29/2017

---
# <a name="bitset-class"></a>bitset 类
介绍一种类型的对象，该对象存储由固定数量的位构成的序列，这些位提供一种紧凑方式来保留一组项或条件的标志。 bitset 类支持对 bitset 类型的对象执行操作，此类对象包含位集合并提供对每一个位的定时访问。  
  
## <a name="syntax"></a>语法  
  
```  
template <size_t N>  
class bitset  
```  
  
#### <a name="parameters"></a>参数  
 *N*  
 使用在编译时必须为已知的 **size_t** 类型的非零整数指定 bitset 对象中的位数。  
  
## <a name="remarks"></a>备注  
 与类似的 [vector\<bool> 类](../standard-library/vector-bool-class.md)不同，bitset 类没有迭代器，并且不是 C++ 标准库容器。 它与 vector\<bool> 的不同之处还在于它有某个特定大小，该大小在编译时根据声明 **bitset\<N\>** 时由模板参数 **N** 指定的大小确定并固定。  
  
 如果某个位的值为 1，则该位已设置；如果其值为 0，则该位已重置。 翻转或反转某个位就是将其值从 1 更改到 0 或从 0 到 1。 bitset 中的 **N** 个位由从 0 到 **N** - 1 的整数值索引，其中 0 索引第一个位的位置，**N** - 1 索引最后一个位的位置。  
  
### <a name="constructors"></a>构造函数  
  
|||  
|-|-|  
|[bitset](#bitset)|构造 `bitset\<N>` 类的对象并将位初始化为零、某个指定值或从字符串中的字符获取的值。|  
  
### <a name="typedefs"></a>Typedef  
  
|||  
|-|-|  
|[element_type](#element_type)|一个类型，它是 `bool` 数据类型的同义词且可用于引用 `bitset` 中的元素位。|  
  
### <a name="member-functions"></a>成员函数  
  
|||  
|-|-|  
|[all](#all)|测试此 `bitset` 中的所有位以确定它们是否都设置为 `true`。|  
|[any](#any)|成员函数测试序列中是否有任何位设置为 1。|  
|[count](#count)|成员函数返回位序列中设置的位数。|  
|[flip](#flip)|反转 `bitset` 中的所有位的值或反转位于指定位置的单个位。|  
|[none](#none)|测试 `bitset` 对象中是否不存在任何已设置为 1 的位。|  
|[reset](#reset)|将 `bitset` 中的所有位重置为 0 或将位于指定位置的位重置为 0。|  
|[set](#set)|将 `bitset` 中的所有位设置为 1 或将位于指定位置的位设置为 1。|  
|[size](#size)|返回 `bitset` 对象中的位数。|  
|[test](#test)|测试 `bitset` 中指定位置处的位是否设置为 1。|  
|[to_string](#to_string)|将 `bitset` 对象转换为字符串表示形式。|  
|[to_ullong](#to_ullong)|将 `bitset` 中的位值的总和作为 `unsigned long long` 返回。|  
|[to_ulong](#to_ulong)|将 `bitset` 对象转换为 `unsigned long`，如果将后者用于初始化 `bitset`，则会产生包含的位的序列。|  
  
### <a name="member-classes"></a>成员类  
  
|||  
|-|-|  
|[reference](#reference)|一个代理类，它提供对 `bitset`（用于将单个位作为 `bitset` 类的 `operator[]` 的帮助程序类进行访问和操作）中包含的位的引用。|  
  
### <a name="operators"></a>运算符  
  
|||  
|-|-|  
|[operator!=](#op_neq)|测试目标 `bitset` 是否与指定的 `bitset` 不相等。|  
|[operator&=](#op_and_eq)|使用逻辑 `AND` 操作执行位组的按位组合。|  
|[operator<<](#op_lshift)|将 `bitset` 中的位移动到左侧指定数目的位置并将结果返回到新的 `bitset`。|  
|[operator<<=](#op_lshift_eq)|将 `bitset` 中的位移动到左侧指定数目的位置并将结果返回到目标 `bitset`。|  
|[operator==](#op_eq_eq)|测试目标 `bitset` 是否与指定的 `bitset` 相等。|  
|[operator>>](#op_rshift)|将 `bitset` 中的位移动到右侧指定数目的位置并将结果返回到新 `bitset`。|  
|[operator>>=](#op_rshift_eq)|将 `bitset` 中的位移动到右侧指定数目的位置并将结果返回到目标 `bitset`。|  
|[operator&#91;&#93;](#op_at)|如果 `bitset` 可修改，则返回对 `bitset` 中指定位置处的位的引用；否则返回该位置处的位值。|  
|[operator^=](#op_xor_eq)|使用独占 `OR` 操作执行位组的按位组合。|  
|[operator&#124;=](#op_or_eq')|使用非独占 `OR` 操作执行位组的按位组合。|  
|[operator~](#op_dtor)|反转目标 `bitset` 中的所有位并返回结果。|  
  
## <a name="requirements"></a>要求  
 **标头：**\<bitset>  
  
 **命名空间：** std  
  
##  <a name="all"></a>  bitset::all  
 测试此位组中的所有位以确定它们是否都设置为 true。  
  
```  
bool all() const;
```  
  
### <a name="return-value"></a>返回值  
 如果此集中的所有位都为 true，则返回 true。 如果一个或多个位为 false，则返回 **false**。  
  
##  <a name="any"></a>  bitset::any  
 测试序列中是否有任何位设置为 1。  
  
```  
bool any() const;
```  
  
### <a name="return-value"></a>返回值  
 如果位组中有任何位设置为 1，则为 **true**；如果所有位均为 0，则为 **false**。  
  
### <a name="example"></a>示例  
  
```cpp  
// bitset_any.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   bitset<5> b1 ( 6 );  
   bool b, rb;  
  
   cout << "The original bitset b1( 6 ) is: ( "<< b1 << " )"  
        << endl;  
  
   b = b1.any ( );  
  
   if ( b )  
      cout << "At least one of the bits in bitset is set to 1."  
           << endl;  
   else  
      cout << "None of the bits in bitset are set to 1."  
           << endl;  
  
   bitset<5> rb1;  
   rb1 = b1.reset ( );  
  
   cout << "The reset bitset is: ( "<< b1 << " )"  
        << endl;  
  
   rb = rb1.any ( );  
  
   if ( rb )  
      cout << "At least one of the bits in the reset bitset "  
           << "are set to 1." << endl;  
   else  
      cout << "None of the bits in bitset b1 are set to 1."  
           << endl;  
}  
```  
  
```Output  
The original bitset b1( 6 ) is: ( 00110 )  
At least one of the bits in bitset is set to 1.  
The reset bitset is: ( 00000 )  
None of the bits in bitset b1 are set to 1.  
```  
  
##  <a name="bitset"></a>  bitset::bitset  
 构造 `bitset\<N>` 类的对象并将位初始化为零、某个指定值或从字符串中的字符获取的值。  
  
```  
bitset();

bitset(
    unsigned long long val);

explicit bitset(
    const char* _CStr);

template <class CharType,   
    class Traits,   
    class Allocator>  
explicit bitset(
    const basic_string<CharType, Traits, Allocator>& str,  
    typename basic_string<CharType, Traits, Allocator>::size_type _Pos = 0);

template <class CharType,  
    class Traits,  
    class Allocator>  
explicit bitset(
    const basic_string<CharType, Traits, Allocator>& str,  
    typename basic_string<CharType, Traits, Allocator>::size_type _Pos,  
    typename basic_string<CharType, Traits, Allocator>::size_type count,  
    CharType _Zero = CharType ('0'),   
    CharType _One = CharType ('1'));
```  
  
### <a name="parameters"></a>参数  
 `val`  
 使用其二进制表示法初始化正在构造的位组中的位的无符号整数。  
  
 `str`  
 由 0 和 1 组成的用于初始化位组位值的字符串。  
  
 `_CStr`  
 由 0 和 1 组成的用于初始化位组位值的 C 类型字符串。  
  
 `_Pos`  
 字符串中的字符位置，从左到右计数，且从 0 开始，用于初始化位组中的第一位。  
  
 `count`  
 字符串中的字符数，用于提供位组中位的初始值。  
  
 `_Zero`  
 用于表示 0 的字符。 默认值为“0”。  
  
 `_One`  
 用于表示 1 的字符。 默认值为“1”。  
  
### <a name="remarks"></a>备注  
 可使用三个构造函数构造 `bitset\<N>` 类的对象：  
  
-   第一个构造函数不接受参数，构造 `bitset\<N>` 类的对象并将所有 N 位初始化为默认值 0。  
  
-   第二个构造函数构造 `bitset\<N>` 类的对象并使用单个 `unsigned long long` 参数初始化所有位。  
  
-   第三个构造函数构造 `bitset\<N>` 类的对象，并将 N 位初始化为与由 0 和 1 组成的 c 类型字符字符串中提供的字符相对应的值。 不通过将字符串转换为字符串类型 `bitset<5> b5("01011");` 来调用构造函数  
  
 还提供了两个构造函数模板：  
  
-   第一个构造函数模板构造 `bitset\<N>` 类的对象并初始化由 0 和 1 组成的字符串中提供的字符中的位。 如果字符串的任何字符为非 0 或非 1，则该构造函数引发 [invalid argument](../standard-library/invalid-argument-class.md) 类的对象。 如果指定的位置 ( `_Pos`) 超出了字符串的长度，则该函数引发 [out_of_range](../standard-library/out-of-range-class.md) 类的对象。 该构造函数只设置位置 `_Pos + j` 处的字符串中的字符为 1 的位组中 *j* 位置处的位。 默认情况下，`_Pos` 是 0。  
  
-   第二个构造函数模板与第一个相似，但是包含用于指定要初始化的位数的其他参数 ( `count`)。 它还拥有两个可选参数，即 `_Zero` 和 `_One`，用于指示 `str` 中的哪些字符要分别转译为表示 0 位或 1 位。  
  
### <a name="example"></a>示例  
  
```cpp  
// bitset_bitset.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main( )  
{  
   // Using the default constructor  
   using namespace std;  
   bitset<2> b0;  
   cout << "The set of bits in bitset<2> b0 is: ( "  
        << b0 << " )." << endl;  
  
   // Using the second member function  
   bitset<5> b1 ( 6 );  
   cout << "The set of bits in bitset<5> b1( 6 ) is: ( "  
        << b1 << " )." << endl;  
  
   // The template parameter N can be an expresssion  
   bitset< 2 * sizeof ( int ) > b2;  
   cout << "The set of bits in bitset<2 * sizeof ( int ) > b2 is: ( "  
        << b2 << " )." << endl;  
  
   // The base two representation will be truncated  
   // if its length exceeds the size of the bitset  
   bitset<3> b3 ( 6 );  
   cout << "The set of bits in bitset<3> b3( 6 ) is ( "  
        << b3 << " )." << endl;  
  
   // Using a c-style string to initialize the bitset  
    bitset<7> b3andahalf ( "1001001" );  
    cout << "The set of bits in bitset<7> b3andahalf ( \"1001001\" )"  
         << " is ( " << b3andahalf << " )." << endl;   
  
   // Using the fifth member function with the first parameter  
   string bitval4 ( "10011" );  
   bitset<5> b4 ( bitval4 );  
   cout << "The set of bits in bitset<5> b4( bitval4 ) is ( "  
        << b4 << " )." << endl;  
  
   // Only part of the string may be used for initialization  
  
   // Starting at position 3 for a length of 6 (100110)  
   string bitval5 ("11110011011");  
   bitset<6> b5 ( bitval5, 3, 6 );  
   cout << "The set of bits in bitset<11> b5( bitval, 3, 6 ) is ( "  
        << b5 << " )." << endl;  
  
   // The bits not initialized with part of the string  
   // will default to zero  
   bitset<11> b6 ( bitval5, 3, 5 );  
   cout << "The set of bits in bitset<11> b6( bitval5, 3, 5 ) is ( "  
        << b6 << " )." << endl;  
  
   // Starting at position 2 and continue to the end of the string  
   bitset<9> b7 ( bitval5, 2 );  
   cout << "The set of bits in bitset<9> b7( bitval, 2 ) is ( "  
        << b7 << " )." << endl;  
}  
```  
  
```Output  
The set of bits in bitset<2> b0 is: ( 00 ).  
The set of bits in bitset<5> b1( 6 ) is: ( 00110 ).  
The set of bits in bitset<2 * sizeof ( int ) > b2 is: ( 00000000 ).  
The set of bits in bitset<3> b3( 6 ) is ( 110 ).  
The set of bits in bitset<5> b4( bitval4 ) is ( 10011 ).  
The set of bits in bitset<11> b5( bitval, 3, 6 ) is ( 100110 ).  
The set of bits in bitset<11> b6( bitval5, 3, 5 ) is ( 00000010011 ).  
The set of bits in bitset<9> b7( bitval, 2 ) is ( 110011011 ).  
```  
  
##  <a name="count"></a>  bitset::count  
 返回位序列中设置的位数。  
  
```  
size_t count() const;
```  
  
### <a name="return-value"></a>返回值  
  
位序列中设置的位数。  
  
### <a name="example"></a>示例  
  
下面的示例演示如何使用 bitset:: count 成员函数。  
  
```cpp  
// bitset_count.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main( )  
{  
    using namespace std;  
  
    bitset<5> b1(4);  
  
    cout << "The collection of bits in the original bitset is: ( "  
         << b1 << " )" << endl;  
  
    size_t i;  
    i = b1.count();  
    cout << "The number of bits in the bitset set to 1 is: "  
         << i << "." << endl;  
  
    bitset<5> fb1;  
    fb1 = b1.flip();  
  
    cout << "The collection of flipped bits in the modified bitset "  
         << "is: ( " << b1 << " )" << endl;  
  
    size_t ii;  
    ii = fb1.count();  
    cout << "The number of bits in the bitset set to 1 is: "  
         << ii << "." << endl;  
}  
```  
  
```Output  
The collection of bits in the original bitset is: ( 00100 )  
The number of bits in the bitset set to 1 is: 1.  
The collection of flipped bits in the modified bitset is: ( 11011 )  
The number of bits in the bitset set to 1 is: 4.  
```  
  
##  <a name="element_type"></a>  bitset::element_type  
 一个类型，它是 `bool` 数据类型的同义词且可用于引用位组中的元素位。  
  
```  
typedef bool element_type;  
```  
  
### <a name="example"></a>示例  
  
```cpp  
// bitset_elem_type.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   bitset<3> b1 ( 2 );  
   cout << "Original bitset b1(6) is: ( "<< b1 << " )"  
        << endl;  
  
   //Compare two ways to reference bits in a bitset  
   bool b;  
   bitset<5>::element_type e;  
  
   b = b1.test ( 2 );  
   if ( b )  
      cout << "The bit at position 2 of bitset b1"  
           << "has a value of 1." << endl;  
   else  
      cout << "The bit at position 2 of bitset b1"  
           << "has a value of 0." << endl;  
   b1[2] = 1;  
   cout << "Bitset b1 modified by b1[2] = 1 is: ( "<< b1 << " )"  
        << endl;  
  
   e = b1.test ( 2 );  
   if ( e )  
      cout << "The bit at position 2 of bitset b1"  
           << "has a value of 1." << endl;  
   else  
      cout << "The bit at position 2 of bitset b1"  
           << "has a value of 0." << endl;  
}  
```  
  
```Output  
Original bitset b1(6) is: ( 010 )  
The bit at position 2 of bitset b1has a value of 0.  
Bitset b1 modified by b1[2] = 1 is: ( 110 )  
The bit at position 2 of bitset b1has a value of 1.  
```  
  
##  <a name="flip"></a>  bitset::flip  
 反转位组中的所有位的值或反转位于指定位置的单个位。  
  
```  
bitset\<N>& flip();  
bitset\<N>& flip(size_t _Pos);
```  
  
### <a name="parameters"></a>参数  
 `_Pos`  
 要将其值反转的位的位置。  
  
### <a name="return-value"></a>返回值  
 对其调用了成员函数且经过修改的位组副本。  
  
### <a name="remarks"></a>备注  
 如果指定为参数的位置大于其位已经过反转的 **bitset\<***N***>** 的大小 *N*，则第二个成员函数引发 [out_of_range](../standard-library/out-of-range-class.md) 异常。  
  
### <a name="example"></a>示例  
  
```cpp  
// bitset_flip.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   bitset<5> b1 ( 6 );  
  
   cout << "The collection of bits in the original bitset is: ( "  
        << b1 << " )" << endl;  
  
   bitset<5> fb1;  
   fb1 = b1.flip ( );  
  
   cout << "After flipping all the bits, the bitset becomes: ( "  
        << fb1 << " )" << endl;  
  
   bitset<5> f3b1;  
   f3b1 = b1.flip ( 3 );  
  
   cout << "After flipping the fourth bit, the bitset becomes: ( "  
        << f3b1 << " )" << endl << endl;  
  
   bitset<5> b2;  
   int i;  
   for ( i = 0 ; i <= 4 ; i++ )  
   {  
      b2.flip(i);  
      cout << b2 << "  The bit flipped is in position "  
           << i << ".\n";  
   }  
}  
```  
  
```Output  
The collection of bits in the original bitset is: ( 00110 )  
After flipping all the bits, the bitset becomes: ( 11001 )  
After flipping the fourth bit, the bitset becomes: ( 10001 )  
  
00001  The bit flipped is in position 0.  
00011  The bit flipped is in position 1.  
00111  The bit flipped is in position 2.  
01111  The bit flipped is in position 3.  
11111  The bit flipped is in position 4.  
```  
  
##  <a name="none"></a>  bitset::none  
 测试位组对象中是否不存在任何已设置为 1 的位。  
  
```  
bool none() const;
```  
  
### <a name="return-value"></a>返回值  
 如果位组中不存在任何已设置为 1 的位则为 **true**；如果至少有一位已设置为 1 则为 **false**。  
  
### <a name="example"></a>示例  
  
```cpp  
// bitset_none.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   bitset<5> b1 ( 6 );  
   bool b, rb;  
  
   cout << "Original bitset b1(6) is: ( " << b1 << " )"  
        << endl;  
  
   b = b1.none ( );  
  
   if ( b )  
      cout << "None of the bits in bitset b1 are set to 1."  
           << endl;  
   else  
      cout << "At least one of the bits in bitset b1 is set to 1."  
           << endl;  
  
   bitset<5> rb1;  
   rb1 = b1.reset ( );  
   rb = rb1.none ( );  
   if ( rb )  
      cout << "None of the bits in bitset b1 are set to 1."  
           << endl;  
   else  
      cout << "At least one of the bits in bitset b1 is set to 1."  
           << endl;  
}  
```  
  
```Output  
Original bitset b1(6) is: ( 00110 )  
At least one of the bits in bitset b1 is set to 1.  
None of the bits in bitset b1 are set to 1.  
```  
  
##  <a name="op_neq"></a>  bitset::operator!=  
 测试目标位组是否与指定的位组不相等。  
  
```  
bool operator!=(const bitset\<N>& right) const;
```  
  
### <a name="parameters"></a>参数  
 `right`  
 要与目标位组比较是否不相等的位组。  
  
### <a name="return-value"></a>返回值  
 如果两个位组不同则为 **true**；如果相同则为 **false**。  
  
### <a name="remarks"></a>备注  
 位组必须大小相同才能由成员运算符函数测试是否不相等。  
  
### <a name="example"></a>示例  
  
```cpp  
// bitset_op_NE.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   bitset<5> b1 ( 7 );  
   bitset<5> b2 ( 7 );  
   bitset<5> b3 ( 2 );  
   bitset<4> b4 ( 7 );  
  
   if ( b1 != b2 )  
      cout << "Bitset b1 is different from bitset b2." << endl;  
   else  
      cout << "Bitset b1 is the same as bitset b2." << endl;  
  
   if ( b1 != b3 )  
      cout << "Bitset b1 is different from bitset b3." << endl;  
   else  
      cout << "Bitset b1 is the same as bitset b3." << endl;  
  
   // This would cause an error because bitsets must have the  
   // same size to be tested  
   // if ( b1 != b4 )  
   //   cout << "Bitset b1 is different from bitset b4." << endl;  
   // else  
   //   cout << "Bitset b1 is the same as bitset b4." << endl;  
}  
```  
  
```Output  
Bitset b1 is the same as bitset b2.  
Bitset b1 is different from bitset b3.  
```  
  
##  <a name="op_and_eq"></a>  bitset::operator&amp;=  
 使用 **AND** 逻辑操作执行位组的按位组合。  
  
```  
bitset\<N>& operator&=(const bitset\<N>& right);
```  
  
### <a name="parameters"></a>参数  
 `right`  
 要与目标位组按位组合的位组。  
  
### <a name="return-value"></a>返回值  
 将位组指定为参数，由 **AND** 按位操作生成的经过修改的目标位组。  
  
### <a name="remarks"></a>备注  
 如果每位均为 true，则 **AND** 运算符组合的两个位返回 **true**；否则，他们的组合返回 **false**。  
  
 位组必须大小相同才能由成员运算符函数使用 **AND** 运算符按位组合。  
  
### <a name="example"></a>示例  
  
```cpp  
// bitset_op_bitwise.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   bitset<5> b1 ( 7 );  
   bitset<5> b2 ( 11 );  
   bitset<4> b3 ( 7 );  
  
   cout << "The target bitset b1 is:    ( "<< b1 << " )." << endl;  
   cout << "The parameter bitset b2 is: ( "<< b2 << " )." << endl;  
   cout << endl;  
  
   b1 &= b2;  
   cout << "After bitwise AND combination,\n"  
        << " the target bitset b1 becomes:   ( "<< b1 << " )."   
        << endl;  
  
   // Note that the parameter-specified bitset is unchanged  
   cout << "The parameter bitset b2 remains: ( "<< b2 << " )."   
        << endl;  
  
   // The following would cause an error because the bisets   
   // must be of the same size to be combined  
   // b1 &= b3;  
}  
```  
  
```Output  
The target bitset b1 is:    ( 00111 ).  
The parameter bitset b2 is: ( 01011 ).  
  
After bitwise AND combination,  
 the target bitset b1 becomes:   ( 00011 ).  
The parameter bitset b2 remains: ( 01011 ).  
```  

##  <a name="op_lshift"></a> bitset::operator\<\<    
  
将位组中的位向左侧移动指定数目的位置并将结果返回到新的位组。  
  
```  
bitset\<N> operator<<(size_t _Pos) const;
```  
  
### <a name="parameters"></a>参数  
 `_Pos`  
 位组中的位要向左侧移动的位置数目。  
  
### <a name="return-value"></a>返回值  
 将位向左侧移动所需数目的位置后的修改位组。  
  
### <a name="remarks"></a>备注  
 成员运算符函数返回 **bitset**( **\*this**) **<<= pos,**，其中 [<<=](#op_lshift_eq) 将位组中的位向左侧移动指定数目的位置并将结果返回到目标位组。  
  
### <a name="example"></a>示例  
  
```cpp  
// bitset_op_LS.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   bitset<5> b1 ( 7 );  
  
   cout << "The bitset b1 is: ( "<< b1 << " )." << endl;  
  
   bitset<5> b2;  
   b2 = b1 << 2;  
  
   cout << "After shifting the bits 2 positions to the left,\n"  
        << " the bitset b2 is: ( "<< b2 << " )."  
        << endl;  
  
   bitset<5> b3 = b2 >> 1;  
  
   cout << "After shifting the bits 1 position to the right,\n"  
        << " the bitset b3 is: ( " << b3 << " )."  
        << endl;  
}  
```  
  
##  <a name="op_lshift_eq"></a>  bitset::operator&lt;&lt;=  
 将位组中的位向左侧移动指定数目的位置并将结果返回到目标位组。  
  
```  
bitset\<N>& operator<<=(size_t _Pos);
```  
  
### <a name="parameters"></a>参数  
 `_Pos`  
 位组中的位要向左侧移动的位置数目。  
  
### <a name="return-value"></a>返回值  
 经过修改的目标位组，以便已将位向左侧移动所需数目的位置。  
  
### <a name="remarks"></a>备注  
 如果不存在要移动到此位置的元素，则函数将位清除为 0 值。  
  
### <a name="example"></a>示例  
  
```cpp  
// bitset_op_LSE.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   bitset<5> b1 ( 7 );  
   cout << "The target bitset b1 is: ( "<< b1 << " )." << endl;  
   b1 <<= 2;  
   cout << "After shifting the bits 2 positions to the left,\n"  
        << " the target bitset b1 becomes: ( "<< b1 << " )."   
        << endl;  
}  
```  
  
```Output  
The target bitset b1 is: ( 00111 ).  
After shifting the bits 2 positions to the left,  
 the target bitset b1 becomes: ( 11100 ).  
```  
  
##  <a name="op_eq_eq"></a>  bitset::operator==  
 测试目标位组是否与指定的位组相等。  
  
```  
bool operator==(const bitset\<N>& right) const;
```  
  
### <a name="parameters"></a>参数  
 `right`  
 要与目标位组比较是否相等的位组。  
  
### <a name="return-value"></a>返回值  
 如果两个位组相同则为 **true**；如果不同则为 **false**。  
  
### <a name="remarks"></a>备注  
 位组必须大小相同才能由成员运算符函数测试是否相等。  
  
### <a name="example"></a>示例  
  
```cpp  
// bitset_op_EQ.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   bitset<5> b1 ( 7 );  
   bitset<5> b2 ( 7 );  
   bitset<5> b3 ( 2 );  
   bitset<4> b4 ( 7 );  
  
   if ( b1 == b2 )  
      cout << "Bitset b1 is the same as bitset b2." << endl;  
   else  
      cout << "Bitset b1 is different from bitset b2." << endl;  
  
   if ( b1 == b3 )  
      cout << "Bitset b1 is the same as bitset b3." << endl;  
   else  
      cout << "Bitset b1 is different from bitset b3." << endl;  
  
   // This would cause an error because bitsets must have the   
   // same size to be tested  
   // if ( b1 == b4 )  
   //   cout << "Bitset b1 is the same as bitset b4." << endl;  
   // else  
   //   cout << "Bitset b1 is different from bitset b4." << endl;  
}  
```  
  
```Output  
Bitset b1 is the same as bitset b2.  
Bitset b1 is different from bitset b3.  
```  
  
##  <a name="op_rshift"></a>  bitset::operator&gt;&gt;  
 将位组中的位向右侧移动指定数目的位置并将结果返回到新的位组。  
  
```  
bitset\<N> operator>>(size_t _Pos) const;
```  
  
### <a name="parameters"></a>参数  
 `_Pos`  
 位组中的位要向右侧移动的位置数目。  
  
### <a name="return-value"></a>返回值  
 新的位组，其中已相对于目标位组将位向右侧移动所需数目的位置。  
  
### <a name="example"></a>示例  
  
```cpp  
// bitset_op_RS.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   bitset<5> b1 ( 7 );  
   cout << "The bitset b1 is: ( "<< b1 << " )." << endl;  
  
   bitset<5> b2;  
   b2 = b1 << 2;  
  
   cout << "After shifting the bits 2 positions to the left,\n"  
        << " the bitset b2 is: ( "<< b2 << " )."  
        << endl;  
   bitset<5> b3 = b2 >> 1;  
  
   cout << "After shifting the bits 1 position to the right,\n"  
        << " the bitset b3 is: ( " << b3 << " )."  
        << endl;  
}  
```  
  
```Output  
The bitset b1 is: ( 00111 ).  
After shifting the bits 2 positions to the left,  
 the bitset b2 is: ( 11100 ).  
After shifting the bits 1 position to the right,  
 the bitset b3 is: ( 01110 ).  
```  
  
##  <a name="op_rshift_eq"></a>  bitset::operator&gt;&gt;=  
 将位组中的位向右侧移动指定数目的位置并将结果返回到目标位组。  
  
```  
bitset\<N>& operator>>=(size_t _Pos);
```  
  
### <a name="parameters"></a>参数  
 `_Pos`  
 位组中的位要向右侧移动的位置数目。  
  
### <a name="return-value"></a>返回值  
 经过修改的目标位组，以便已将位向右侧移动所需数目的位置。  
  
### <a name="remarks"></a>备注  
 如果不存在要移动到此位置的元素，则函数将位清除为 0 值。  
  
### <a name="example"></a>示例  
  
```cpp  
// bitset_op_RSE.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   bitset<5> b1 ( 28 );  
   cout << "The target bitset b1 is: ( "<< b1 << " )." << endl;  
  
   b1 >>= 2;  
   cout << "After shifting the bits 2 positions to the right,\n"  
        << " the target bitset b1 becomes: ( "<< b1 << " )."   
        << endl;  
}  
```  
  
```Output  
The target bitset b1 is: ( 11100 ).  
After shifting the bits 2 positions to the right,  
 the target bitset b1 becomes: ( 00111 ).  
```  
  
##  <a name="op_at"></a>  bitset::operator[]  
 如果位组可修改，则返回对位组中指定位置处的位的引用；否则返回该位置处的位值。  
  
```  
bool operator[](size_t _Pos) const;
reference operator[](size_t _Pos);
```  
  
### <a name="parameters"></a>参数  
 `_Pos`  
 位在位组内所处的位置。  
  
### <a name="remarks"></a>备注  
在构建过程中将 [\_ITERATOR\_DEBUG\_LEVEL](../standard-library/iterator-debug-level.md) 定义为 1 或 2时，如果尝试访问位组边界以外的元素，则可执行文件中将发生运行时错误。 有关详细信息，请参阅[经过检查的迭代器](../standard-library/checked-iterators.md)。  
  
### <a name="example"></a>示例  
  
```cpp  
// bitset_op_REF.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   bool b;  
   bitset<5> b1 ( 6 );  
   cout << "The initialized bitset<5> b1( 2 ) is: ( "<< b1 << " )."  
        << endl;  
  
   int i;  
   for ( i = 0 ; i <= 4 ; i++ )  
   {  
      b = b1[ i ];  
      cout << "  The bit in position "  
           << i << " is " << b << ".\n";  
   }  
}  
```  
  
##  <a name="op_xor_eq"></a>  bitset::operator^=  
 使用独占 `OR` 操作执行位组的按位组合。  
  
```  
bitset\<N>& operator^=(const bitset\<N>& right);
```  
  
### <a name="parameters"></a>参数  
 `right`  
 要与目标位组按位组合的位组。  
  
### <a name="return-value"></a>返回值  
 将位组指定为参数，由按位异 `OR` 操作生成的经过修改的目标位组。  
  
### <a name="remarks"></a>备注  
 如果至少一位，但不是所有位为 **true**，则由异 **OR** 运算符组合的两个位返回 **true**；否则，它们的组合返回 **false**。  
  
 位组必须大小相同才能由成员运算符函数使用异 `OR` 运算符按位组合。  
  
### <a name="example"></a>示例  
  
```cpp  
// bitset_op_bitwiseOR.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   bitset<5> b1 ( 7 );  
   bitset<5> b2 ( 11 );  
   bitset<4> b3 ( 7 );  
  
   cout << "The target bitset b1 is:    ( "<< b1 << " )." << endl;  
   cout << "The parameter bitset b2 is: ( "<< b2 << " )." << endl;  
   cout << endl;  
  
   b1 ^= b2;  
   cout << "After bitwise exclusive OR combination,\n"  
        << " the target bitset b1 becomes:   ( "<< b1 << " )."   
        << endl;  
  
   // Note that the parameter-specified bitset in unchanged  
   cout << "The parameter bitset b2 remains: ( "<< b2 << " )."   
        << endl;  
  
   // The following would cause an error because the bisets   
   // must be of the same size to be combined  
   // b1 |= b3;  
}  
```  
  
```Output  
The target bitset b1 is:    ( 00111 ).  
The parameter bitset b2 is: ( 01011 ).  
  
After bitwise exclusive OR combination,  
 the target bitset b1 becomes:   ( 01100 ).  
The parameter bitset b2 remains: ( 01011 ).  
```  
  
##  <a name="op_or_eq"></a>  bitset::operator&#124;=  
 使用非独占 `OR` 操作执行位组的按位组合。  
  
```  
bitset\<N>& operator|=(const bitset\<N>& right);
```  
  
### <a name="parameters"></a>参数  
 `right`  
 要与目标位组按位组合的位组。  
  
### <a name="return-value"></a>返回值  
 将位组指定为参数，由按位非独占 `OR` 操作生成的经过修改的目标位组。  
  
### <a name="remarks"></a>备注  
 如果至少一位为 **true**，则由非独占 `OR` 运算符组合的两个位返回 **true**；如果两个位均为 **false**，则它们的组合返回 **false**。  
  
 位组必须大小相同才能由成员运算符函数使用非独占 `OR` 运算符按位组合。  
  
### <a name="example"></a>示例  
  
```cpp  
// bitset_op_BIO.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   bitset<5> b1 ( 7 );  
   bitset<5> b2 ( 11 );  
   bitset<4> b3 ( 7 );  
  
   cout << "The target bitset b1 is:    ( "<< b1 << " )." << endl;  
   cout << "The parameter bitset b2 is: ( "<< b2 << " )." << endl;  
   cout << endl;  
  
   b1 |= b2;  
   cout << "After bitwise inclusive OR combination,\n"  
        << " the target bitset b1 becomes:   ( "<< b1 << " )."   
        << endl;  
  
   // Note that the parameter-specified bitset in unchanged  
   cout << "The parameter bitset b2 remains: ( "<< b2 << " )."   
        << endl;  
  
   // The following would cause an error because the bisets   
   // must be of the same size to be combined  
   // b1 |= b3;  
}  
```  
  
```Output  
The target bitset b1 is:    ( 00111 ).  
The parameter bitset b2 is: ( 01011 ).  
  
After bitwise inclusive OR combination,  
 the target bitset b1 becomes:   ( 01111 ).  
The parameter bitset b2 remains: ( 01011 ).  
```  
  
##  <a name="op_dtor"></a>  bitset::operator~  
 反转目标位组中的所有位并返回结果。  
  
```  
bitset\<N> operator~() const;
```  
  
### <a name="return-value"></a>返回值  
 已针对目标位组反转其所有位的位组。  
  
### <a name="example"></a>示例  
  
```cpp  
// bitset_op_invert.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <string>  
#include <bitset>  
  
int main( )  
{  
   using namespace std;  
  
   bitset<5> b1 ( 7 );  
   bitset<5> b2;  
   b2 = ~b1;  
  
   cout << "Bitset b1 is: ( "<< b1 << " )." << endl;  
   cout << "Bitset b2 = ~b1 is: ( "<< b2 << " )." << endl;  
  
   // These bits could also be flipped using the flip member function  
   bitset<5> b3;  
   b3 = b1.flip( );  
   cout << "Bitset b3 = b1.flip( ) is: ( "<< b2 << " )." << endl;  
}  
```  
  
```Output  
Bitset b1 is: ( 00111 ).  
Bitset b2 = ~b1 is: ( 11000 ).  
Bitset b3 = b1.flip( ) is: ( 11000 ).  
```  
  
##  <a name="reference"></a>  bitset::reference  
 一个代理类，它提供对位组（用于将单个位作为位组类的 `operator[]` 的帮助程序类进行访问和操作）中包含的位的引用。  
  
```  
class reference {  
   friend class bitset\<N>;  
public: 
   reference& operator=(bool val);
   reference& operator=(const reference& _Bitref);
   bool operator~() const;
   operator bool() const;
   reference& flip();
};  
```    
  
### <a name="parameters"></a>参数  
 `val`  
 要分配到位组中的位的 `bool` 类型的对象的值。  
  
 `_Bitref`  
 窗体 *x [ i ]* 对位组 *x* 中 *i* 位置上的位的引用。  
  
### <a name="return-value"></a>返回值  
 由类引用的第一个、第二个和第五个成员函数的自变量位置指定的对位组中的位的引用，并且由 **true** 或 **false** 来反映类引用的第三个和第四个成员函数的位组中经过修改的位的值。  
  
### <a name="remarks"></a>备注  
 `reference` 类仅作为位组 `operator[]` 的帮助程序类存在。 成员类描述可以访问位组中的单个位的对象。 让 *b* 作为 `bool` 类型的对象，*x* 和 *y* 作为 **bitset\<***N***>** 类型的对象，*i* 和 *j* 作为此类对象中的有效位置。 表示法 *x [i]* 引用位组 *x* 中的 *i* 位置上的位。 `reference` 类的成员函数按顺序提供以下操作：  
  
|操作|定义|  
|---------------|----------------|  
|*x*[*i*] = *b*|将 `bool` 值 *b* 存储在位组 *x* 中的位位置 *i* 上。|  
|*x*[*i*] = *y*[*j*]|将位 *y*[ *j*] 的值存储在位组 *x* 中的位位置 *i* 上。|  
|*b* = ~ *x*[*i*]|将位 *x*[ *i*] 的翻转值存储在 `bool` *b* 中。|  
|*b* = *x*[*i*]|将位 *x*[ *i*] 的值存储在 `bool` *b* 中。|  
|*x*[*i*]. `flip`( )|将位 *x*[ *i*] 的翻转值存储在 *x* 中的位位置 *i* 后面。|  
  
### <a name="example"></a>示例  
  
```cpp  
// bitset_reference.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   bitset<5> b1 ( 2 );  
   bitset<5> b2 ( 6 );  
   cout << "The initialized bitset<5> b1( 2 ) is: ( "<< b1 << " )."  
        << endl;  
   cout << "The initialized bitset<5> b2( 6 ) is: ( "<< b2 << " )."  
        << endl;  
  
   // Example of x [i] = b storing bool b at bit position i  
   // in bitset x  
   b1[ 0 ] = true;  
   cout << "The bitset<5> b1 with the bit at position 0 set to 1"  
        << " is: ( "<< b1 << " )" << endl;  
  
   // Example of x [i] = y [j] storing the bool value of the  
   // bit at position j in bitset y at bit position i in bitset x  
   b2 [4] = b1 [0];      // b1 [0] = true  
   cout << "The bitset<5> b2 with the bit at position 4 set to the "  
        << "value\n of the bit at position 0 of the bit in "  
        << "bitset<5> b1 is: ( "<<  b2  << " )" << endl;  
  
   // Example of b = ~x [i] flipping the value of the bit at  
   // position i of bitset x and storing the value in an   
   // object b of type bool  
   bool b = ~b2 [4];      // b2 [4] = false  
   if ( b )  
      cout << "The value of the object b = ~b2 [4] "  
           << "of type bool is true." << endl;  
   else  
      cout << "The value of the object b = ~b2 [4] "  
           << "of type bool is false." << endl;  
  
   // Example of b = x [i] storing the value of the bit at  
   // position i of bitset x in the object b of type bool  
   b = b2 [4];  
   if ( b )  
      cout << "The value of the object b = b2 [4] "  
           << "of type bool is true." << endl;  
   else  
      cout << "The value of the object b = b2 [4] "  
           << "of type bool is false." << endl;  
  
   // Example of x [i] . flip ( ) toggling the value of the bit at  
   // position i of bitset x  
   cout << "Before flipping the value of the bit at position 4 in "  
        << "bitset b2,\n it is ( "<<  b2  << " )." << endl;  
   b2 [4].flip( );  
   cout << "After flipping the value of the bit at position 4 in "  
        << "bitset b2,\n it becomes ( "<<  b2  << " )." << endl;  
   bool c;  
   c = b2 [4].flip( );  
   cout << "After a second flip, the value of the position 4"  
        << " bit in b2 is now: " << c << ".";  
}  
```  
  
```Output  
The initialized bitset<5> b1( 2 ) is: ( 00010 ).  
The initialized bitset<5> b2( 6 ) is: ( 00110 ).  
The bitset<5> b1 with the bit at position 0 set to 1 is: ( 00011 )  
The bitset<5> b2 with the bit at position 4 set to the value  
 of the bit at position 0 of the bit in bitset<5> b1 is: ( 10110 )  
The value of the object b = ~b2 [4] of type bool is false.  
The value of the object b = b2 [4] of type bool is true.  
Before flipping the value of the bit at position 4 in bitset b2,  
 it is ( 10110 ).  
After flipping the value of the bit at position 4 in bitset b2,  
 it becomes ( 00110 ).  
After a second flip, the value of the position 4 bit in b2 is now: 1.  
```  
  
##  <a name="reset"></a>  bitset::reset  
 将位组中的所有位重置为 0 或将位于指定位置的位重置为 0。  
  
```  
bitset\<N>& reset();  
bitset\<N>& reset(size_t _Pos);
```  
  
### <a name="parameters"></a>参数  
 `_Pos`  
 要重置为 0 的位组中的位的位置。  
  
### <a name="return-value"></a>返回值  
 对其调用成员函数的位组副本。  
  
### <a name="remarks"></a>备注  
 如果指定的位置大于位组的大小，则第二个成员函数引发 [out_of_range](../standard-library/out-of-range-class.md) 异常。  
  
### <a name="example"></a>示例  
  
```cpp  
// bitset_reset.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   bitset<5> b1 ( 13 );  
   cout << "The set of bits in bitset<5> b1(13) is: ( "<< b1 << " )"  
        << endl;  
  
   bitset<5> b1r3;  
   b1r3 = b1.reset( 2 );  
   cout << "The collecion of bits obtained from resetting the\n"  
        << " third bit of bitset b1 is: ( "<< b1r3 << " )"   
        << endl;  
  
   bitset<5> b1r;  
   b1r = b1.reset( );  
   cout << "The collecion of bits obtained from resetting all\n"  
        << " the elements of the bitset b1 is: ( "<< b1r << " )"  
        << endl;  
}  
```  
  
```Output  
The set of bits in bitset<5> b1(13) is: ( 01101 )  
The collecion of bits obtained from resetting the  
 third bit of bitset b1 is: ( 01001 )  
The collecion of bits obtained from resetting all  
 the elements of the bitset b1 is: ( 00000 )  
```  
  
##  <a name="set"></a>  bitset::set  
 将位组中的所有位设置为 1 或将位于指定位置的位设置为 1。  
  
```   
bitset\<N>& set();

bitset\<N>& set(
    size_t _Pos,   
    bool val = true);
```  
  
### <a name="parameters"></a>参数  
 `_Pos`  
 要设置为分配值的位组中的位的位置。  
  
 `val`  
 要向指定位置的位分配的值。  
  
### <a name="return-value"></a>返回值  
 对其调用成员函数的位组副本。  
  
### <a name="remarks"></a>备注  
 如果指定的位置大于位组的大小，则第二个成员函数引发 [out_of_range](../standard-library/out-of-range-class.md) 异常。  
  
### <a name="example"></a>示例  
  
```cpp  
// bitset_set.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   bitset<5> b1 ( 6 );  
   cout << "The set of bits in bitset<5> b1(6) is: ( "<< b1 << " )"  
        << endl;  
  
   bitset<5> b1s0;  
   b1s0 = b1.set( 0 );  
   cout << "The collecion of bits obtained from setting the\n"  
        << " zeroth bit of bitset b1 is: ( "<< b1s0 << " )"   
        << endl;  
  
   bitset<5> bs1;  
   bs1 = b1.set( );  
   cout << "The collecion of bits obtained from setting all the\n"  
        << " elements of the bitset b1 is: ( "<< bs1 << " )"  
        << endl;  
}  
```  
  
```Output  
The set of bits in bitset<5> b1(6) is: ( 00110 )  
The collecion of bits obtained from setting the  
 zeroth bit of bitset b1 is: ( 00111 )  
The collecion of bits obtained from setting all the  
 elements of the bitset b1 is: ( 11111 )  
```  
  
##  <a name="size"></a>  bitset::size  
 返回 bitset 对象中的位数。  
  
```  
size_t size() const;
```  
  
### <a name="return-value"></a>返回值  
 bitset\<N> 中 *N* 的位数。  
  
### <a name="example"></a>示例  
  下面的示例演示如何使用 bitset::count 成员函数。  
  
```cpp  
// bitset_size.cpp  
// compile with: /EHsc  
#include <bitset>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
  
    bitset<5> b1(6);  
    size_t i;  
  
    cout << "The set of bits in bitset<5> b1( 6 ) is: ( "<< b1 << " )"  
         << endl;  
  
    i = b1.size();  
  
    cout << "The number of bits in bitset b1 is: " << i << "."  
         << endl;  
}  
```  
  
```Output  
The set of bits in bitset<5> b1( 6 ) is: ( 00110 )  
The number of bits in bitset b1 is: 5.  
```  
  
##  <a name="test"></a>  bitset::test  
 测试位组中指定位置处的位是否设置为 1。  
  
```  
bool test(size_t _Pos) const;
```  
  
### <a name="parameters"></a>参数  
 `_Pos`  
 要测试其值的位组中位的位置。  
  
### <a name="return-value"></a>返回值  
 如果将参数位置指定的位设置为 1 则为 **true**；否则为 **false**。  
  
### <a name="remarks"></a>备注  
 成员函数引发 [out_of_range](../standard-library/out-of-range-class.md)



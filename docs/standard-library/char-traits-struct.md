---
title: char_traits 结构
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::char_traits
- iosfwd/std::char_traits::char_type
- iosfwd/std::char_traits::int_type
- iosfwd/std::char_traits::off_type
- iosfwd/std::char_traits::pos_type
- iosfwd/std::char_traits::state_type
- iosfwd/std::char_traits::assign
- iosfwd/std::char_traits::compare
- iosfwd/std::char_traits::copy
- iosfwd/std::char_traits::_Copy_s
- iosfwd/std::char_traits::eof
- iosfwd/std::char_traits::eq
- iosfwd/std::char_traits::eq_int_type
- iosfwd/std::char_traits::find
- iosfwd/std::char_traits::length
- iosfwd/std::char_traits::lt
- iosfwd/std::char_traits::move
- iosfwd/std::char_traits::_Move_s
- iosfwd/std::char_traits::not_eof
- iosfwd/std::char_traits::to_char_type
- iosfwd/std::char_traits::to_int_type
helpviewer_keywords:
- char_traits struct
- char_traits class
ms.assetid: 568e59f0-4521-4207-9223-9dcf6a16d620
ms.openlocfilehash: 2975c839e07093a22d910f295be730fdd68839cf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62379436"
---
# <a name="chartraits-struct"></a>char_traits 结构

Char_traits 结构描述与一个字符相关联的特性。

## <a name="syntax"></a>语法

```cpp
template <class CharType>
struct char_traits;
```

### <a name="parameters"></a>参数

*CharType*<br/>
元素数据类型。

## <a name="remarks"></a>备注

模板结构描述类型的各种字符特征`CharType`。 此模板类[basic_string](../standard-library/basic-string-class.md)以及若干 iostream 模板类，其中包括[basic_ios](../standard-library/basic-ios-class.md)，使用此信息来操作类型的元素`CharType`。 此元素类型不得要求显式构造或析构。 它必须提供带预期语义的默认构造函数、复制构造函数和赋值运算符。 按位复制必须具有与赋值相同的效果。 结构 char_traits 的任何成员函数均无法引发异常。

### <a name="typedefs"></a>Typedef

|类型名称|描述|
|-|-|
|[char_type](#char_type)|一种字符类型。|
|[int_type](#int_type)|一种整数类型，该类型可以表示类型为 `char_type` 的字符或文件尾 (EOF) 字符。|
|[off_type](#off_type)|一种整数类型，该类型可以表示流中两个位置之间的偏移量。|
|[pos_type](#pos_type)|一种整数类型，该类型可以表示流中的位置。|
|[state_type](#state_type)|一种类型，该类型表示流中的多字节字符的转换状态。|

### <a name="member-functions"></a>成员函数

|成员函数|描述|
|-|-|
|[assign](#assign)|将一个字符值分配给另一个。|
|[compare](#compare)|将两个字符串中指定数量的字符进行比较。|
|[copy](#copy)|将指定数量的字符从一个字符串复制到另一个字符串。 已否决。 改为使用 [char_traits::_Copy_s](#copy_s)。|
|[_Copy_s](#copy_s)|将指定数量的字符从一个字符串复制到另一个字符串。|
|[eof](#eof)|返回文件尾 (EOF) 字符。|
|[eq](#eq)|测试两个 `char_type` 字符是否相等。|
|[eq_int_type](#eq_int_type)|测试两个表示为 `int_type` 的字符是否相等。|
|[find](#find)|在字符范围中搜索指定字符的第一个匹配项。|
|[length](#length)|返回字符串的长度。|
|[lt](#lt)|测试一个字符是否小于另一个。|
|[move](#move)|将指定数量的字符从一个字符串复制到另一个字符串，可能会发生重叠。 已否决。 改为使用 [char_traits::_Move_s](#move_s)。|
|[_Move_s](#move_s)|将指定数量的字符从一个字符串复制到另一个字符串，可能会发生重叠。|
|[not_eof](#not_eof)|测试字符是否为文件尾 (EOF) 字符。|
|[to_char_type](#to_char_type)|将 `int_type` 字符转换为相应的 `char_type` 字符，并返回结果。|
|[to_int_type](#to_int_type)|将 `char_type` 字符转换为相应的 `int_type` 字符，并返回结果。|

## <a name="requirements"></a>要求

**标头：** \<string>

**命名空间：** std

## <a name="assign"></a>  char_traits::assign

将一个字符值分配到其他或字符串中的一系列元素。

```cpp
static void assign(char_type& _CharTo,
    const char_type& _CharFrom);

static char_type *assign(char_type* strTo,
    size_t _Num,
    char_type _CharFrom);
```

### <a name="parameters"></a>参数

**_** *CharFrom*其值将被分配的字符。

*_CharTo*<br/>
要为其分配字符值的元素。

*strTo*<br/>
要对其初始元素分配字符值的字符串或字符数组。

*_Num*<br/>
要为其分配值的元素数目。

### <a name="return-value"></a>返回值

第二个成员函数返回的指针到字符串的第一个 *_Num*元素分配的值 *_CharFrom*。

### <a name="example"></a>示例

```cpp
// char_traits_assign.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function assigning
   // one character value to another character
   char ChTo = 't';
   const char ChFrom = 'f';
   cout << "The initial characters ( ChTo , ChFrom ) are: ( "
        << ChTo << " , " << ChFrom << " )." << endl;
   char_traits<char>::assign ( ChTo , ChFrom );
   cout << "After assigning, the characters ( ChTo , ChFrom ) are: ( "
        << ChTo << " , " << ChFrom << " )." << endl << endl;

   // The second member function assigning
   // character values to initial part of a string
   char_traits<char>::char_type s1[] = "abcd-1234-abcd";
   char_traits<char>::char_type* result1;
   cout << "The target string s1 is: " << s1 << endl;
   result1 = char_traits<char>::assign ( s1 , 4 , 'f' );
   cout << "The result1 = assign ( s1 , 4 , 'f' ) is: "
        << result1 << endl;
}
```

```Output
The initial characters ( ChTo , ChFrom ) are: ( t , f ).
After assigning, the characters ( ChTo , ChFrom ) are: ( f , f ).

The target string s1 is: abcd-1234-abcd
The result1 = assign ( s1 , 4 , 'f' ) is: ffff-1234-abcd
```

## <a name="char_type"></a>char_traits:: char_type

一种字符类型。

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>备注

该类型是模板参数 `CharType` 的同义词。

### <a name="example"></a>示例

有关如何声明和使用 `char_type` 的示例，请参阅 [copy](#copy) 的示例。

## <a name="compare"></a>  char_traits::compare

将两个字符串中指定数量的字符进行比较。

```cpp
static int compare(const char_type* str1,
    const char_type* str2,
    size_t _Num);
```

### <a name="parameters"></a>参数

*str1*<br/>
要进行比较的两个字符串中的第一个。

*str2*<br/>
要进行比较的两个字符串中的第二个。

*_Num*<br/>
要比较的字符串中的元素数。

### <a name="return-value"></a>返回值

如果第一个字符串小于第二个字符串，则为负值，如果两个字符串相等则为 0，如果第一个字符串大于第二个字符串，则为正值。

### <a name="remarks"></a>备注

字符串之间的比较按照元素依次进行，第一次测试是否相等，然后，如果序列测试中出现不相等的元素对，则测试是否为小于。

如果范围内两个字符串比较结果相等，但其中一个长度大于另一个，则两个中较短的一个小于较长的一个。

### <a name="example"></a>示例

```cpp
// char_traits_compare.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main() {
   using namespace std;

   char_traits<char>::char_type* s1 = "CAB";
   char_traits<char>::char_type* s2 = "ABC";
   char_traits<char>::char_type* s3 = "ABC";
   char_traits<char>::char_type* s4 = "ABCD";

   cout << "The string s1 is: " << s1 << endl;
   cout << "The string s2 is: " << s2 << endl;
   cout << "The string s3 is: " << s3 << endl;
   cout << "The string s4 is: " << s4 << endl;

   int comp1, comp2, comp3, comp4;
   comp1 = char_traits<char>::compare ( s1 , s2 , 2 );
   comp2 = char_traits<char>::compare ( s2 , s3 , 3 );
   comp3 = char_traits<char>::compare ( s3 , s4 , 4 );
   comp4 = char_traits<char>::compare ( s4 , s3 , 4 );
   cout << "compare ( s1 , s2 , 2 ) = " << comp1 << endl;
   cout << "compare ( s2 , s3 , 3 ) = " << comp2 << endl;
   cout << "compare ( s3 , s4 , 4 ) = " << comp3 << endl;
   cout << "compare ( s4 , s3 , 4 ) = " << comp4 << endl;
}
```

## <a name="copy"></a>  char_traits::copy

将指定数量的字符从一个字符串复制到另一个字符串。

此方法可能并不安全，因为它依赖于调用方检查所传递的值是否正确。 请考虑改为使用 [char_traits::_Copy_s](#copy_s)。

```cpp
static char_type *copy(char_type* _To,
    const char_type* _From,
    size_t _Num);
```

### <a name="parameters"></a>参数

*_To*<br/>
用于接收复制的字符序列的字符串或字符数组的开头处的元素。

*_From*<br/>
要复制的源字符串或字符数组的开头处的元素。

*_Num*<br/>
要复制的元素的数量。

### <a name="return-value"></a>返回值

复制到用于接收复制的字符序列的字符串或字符数组的第一个元素。

### <a name="remarks"></a>备注

源和目标字符序列不能重叠。

### <a name="example"></a>示例

```cpp
// char_traits_copy.cpp
// compile with: /EHsc /W3
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   char_traits<char>::char_type s1[] = "abcd-1234-abcd";
   char_traits<char>::char_type s2[] = "ABCD-1234";
   char_traits<char>::char_type* result1;
   cout << "The source string is: " << s1 << endl;
   cout << "The destination string is: " << s2 << endl;
   // Note: char_traits::copy is potentially unsafe, consider
   // using char_traits::_Copy_s instead.
   result1 = char_traits<char>::copy ( s1 , s2 , 4 );  // C4996
   cout << "The result1 = copy ( s1 , s2 , 4 ) is: "
        << result1 << endl;
}
```

```Output
The source string is: abcd-1234-abcd
The destination string is: ABCD-1234
The result1 = copy ( s1 , s2 , 4 ) is: ABCD-1234-abcd
```

## <a name="copy_s"></a>  char_traits::_Copy_s

将指定数量的字符从一个字符串复制到另一个字符串。

```cpp
static char_type *_Copy_s(
    char_type* dest,
    size_t dest_size,
    const char_type* _From,
    size_t count);
```

### <a name="parameters"></a>参数

*dest*<br/>
用于接收复制的字符序列的字符串或字符数组。

*dest_size*<br/>
大小*dest*。 如果`char_type`是**char**，则此大小以字节为单位。 如果`char_type`是**wchar_t**，则此大小以字为单位。

*_From*<br/>
要复制的源字符串或字符数组。

*count*<br/>
要复制的元素的数量。

### <a name="return-value"></a>返回值

用于接收复制的字符序列的字符串或字符数组。

### <a name="remarks"></a>备注

源和目标字符序列不能重叠。

### <a name="example"></a>示例

```cpp
// char_traits__Copy_s.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
    using namespace std;

    char_traits<char>::char_type s1[] = "abcd-1234-abcd";
    char_traits<char>::char_type s2[] = "ABCD-1234";
    char_traits<char>::char_type* result1;
    cout << "The source string is: " << s1 << endl;
    cout << "The destination string is: " << s2 << endl;
    result1 = char_traits<char>::_Copy_s(s1,
        char_traits<char>::length(s1), s2, 4);
    cout << "The result1 = _Copy_s(s1, "
         << "char_traits<char>::length(s1), s2, 4) is: "
         << result1 << endl;
}
```

```Output
The source string is: abcd-1234-abcd
The destination string is: ABCD-1234
The result1 = _Copy_s(s1, char_traits<char>::length(s1), s2, 4) is: ABCD-1234-abcd
```

## <a name="eof"></a>  char_traits::eof

返回文件尾 (EOF) 字符。

```cpp
static int_type eof();
```

### <a name="return-value"></a>返回值

EOF 字符。

### <a name="remarks"></a>备注

一个值，表示文件结尾 （例如 EOF 或 WEOF）。

C++ 标准声明此值不能对应于有效的 `char_type` 值。 视觉对象C++编译器可强制此约束的类型**char**，而不是类型**wchar_t**。 下面的示例将说明这一点。

### <a name="example"></a>示例

```cpp
// char_traits_eof.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main()
{
    using namespace std;

    char_traits<char>::char_type ch1 = 'x';
    char_traits<char>::int_type int1;
    int1 = char_traits<char>::to_int_type(ch1);
    cout << "char_type ch1 is '" << ch1 << "' and corresponds to int_type "
         << int1 << "." << endl << endl;

    char_traits<char>::int_type int2 = char_traits<char>::eof();
    cout << "The eof marker for char_traits<char> is: " << int2 << endl;

    char_traits<wchar_t>::int_type int3 = char_traits<wchar_t>::eof();
    cout << "The eof marker for char_traits<wchar_t> is: " << int3 << endl;
}
```

```Output
char_type ch1 is 'x' and corresponds to int_type 120.

The eof marker for char_traits<char> is: -1
The eof marker for char_traits<wchar_t> is: 65535
```

## <a name="eq"></a>  char_traits::eq

测试两个 `char_type` 字符是否相等。

```cpp
static bool eq(const char_type& _Ch1, const char_type& _Ch2);
```

### <a name="parameters"></a>参数

*_Ch1*<br/>
要测试是否相等的两个字符中的第一个。

*_Ch2*<br/>
要测试是否相等的两个字符中的第二个。

### <a name="return-value"></a>返回值

如果第一个字符等于第二个字符，则为 **true**；否则为 **false**。

### <a name="example"></a>示例

```cpp
// char_traits_eq.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   char_traits<char>::char_type ch1 =  'x';
   char_traits<char>::char_type ch2 =  'y';
   char_traits<char>::char_type ch3 =  'x';

   // Testing for equality
   bool b1 = char_traits<char>::eq ( ch1 , ch2 );
   if ( b1 )
      cout << "The character ch1 is equal "
           << "to the character ch2." << endl;
   else
      cout << "The character ch1 is not equal "
           << "to the character ch2." << endl;

   // An equivalent and alternatively test procedure
   if ( ch1 == ch3 )
      cout << "The character ch1 is equal "
           << "to the character ch3." << endl;
   else
      cout << "The character ch1 is not equal "
           << "to the character ch3." << endl;
}
```

```Output
The character ch1 is not equal to the character ch2.
The character ch1 is equal to the character ch3.
```

## <a name="eq_int_type"></a>  char_traits::eq_int_type

测试两个表示为 `int_type` 的字符是否相等。

```cpp
static bool eq_int_type(const int_type& _Ch1, const int_type& _Ch2);
```

### <a name="parameters"></a>参数

*_Ch1*<br/>
两个字符的第一个要测试是否等于`int_type`s。

*_Ch2*<br/>
要测试是否等于 `int_type` 的两个字符中的第二个。

### <a name="return-value"></a>返回值

如果第一个字符等于第二个字符，则为 **true**；否则为 **false**。

### <a name="example"></a>示例

```cpp
// char_traits_eq_int_type.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   char_traits<char>::char_type ch1 =  'x';
   char_traits<char>::char_type ch2 =  'y';
   char_traits<char>::char_type ch3 =  'x';

   // Converting from char_type to int_type
   char_traits<char>::int_type int1, int2 , int3;
   int1 =char_traits<char>:: to_int_type ( ch1 );
   int2 =char_traits<char>:: to_int_type ( ch2 );
   int3 =char_traits<char>:: to_int_type ( ch3 );

   cout << "The char_types and corresponding int_types are:"
        << "\n    ch1 = " << ch1 << " corresponding to int1 = "
        << int1 << "."
        << "\n    ch2 = " << ch2 << " corresponding to int1 = "
        << int2 << "."
        << "\n    ch3 = " << ch3 << " corresponding to int1 = "
        << int3 << "." << endl << endl;

   // Testing for equality of int_type representations
   bool b1 = char_traits<char>::eq_int_type ( int1 , int2 );
   if ( b1 )
      cout << "The int_type representation of character ch1\n "
           << "is equal to the int_type representation of ch2."
           << endl;
   else
      cout << "The int_type representation of character ch1\n is "
           << "not equal to the int_type representation of ch2."
           << endl;

   // An equivalent and alternatively test procedure
   if ( int1 == int3 )
      cout << "The int_type representation of character ch1\n "
           << "is equal to the int_type representation of ch3."
           << endl;
   else
      cout << "The int_type representation of character ch1\n is "
           << "not equal to the int_type representation of ch3."
           << endl;
}
```

```Output
The char_types and corresponding int_types are:
    ch1 = x corresponding to int1 = 120.
    ch2 = y corresponding to int1 = 121.
    ch3 = x corresponding to int1 = 120.

The int_type representation of character ch1
is not equal to the int_type representation of ch2.
The int_type representation of character ch1
is equal to the int_type representation of ch3.
```

## <a name="find"></a>  char_traits::find

在字符范围中搜索指定字符的第一个匹配项。

```cpp
static const char_type* find(const char_type* str,
    size_t _Num,
    const char_type& _Ch);
```

### <a name="parameters"></a>参数

*str*<br/>
要搜索的字符串中的第一个字符。

*_Num*<br/>
要搜索范围内的位置数，从第一位开始计数。

*_Ch*<br/>
要在范围中搜索的字符。

### <a name="return-value"></a>返回值

如果找到匹配项，则为指向范围内指定字符的第一个匹配项的指针，否则为空指针。

### <a name="example"></a>示例

```cpp
// char_traits_find.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   const char* s1 = "f2d-1234-abcd";
   const char* result1;
   cout << "The string to be searched is: " << s1 << endl;

   // Searching for a 'd' in the first 6 positions of string s1
   result1 = char_traits<char>::find ( s1 , 6 , 'd');
   cout << "The character searched for in s1 is: "
        << *result1 << endl;
   cout << "The string beginning with the first occurrence\n "
        << "of the character 'd' is: " << result1 << endl;

   // When no match is found the NULL value is returned
   const char* result2;
   result2 = char_traits<char>::find ( s1 , 3 , 'a');
   if ( result2 == NULL )
      cout << "The result2 of the search is NULL." << endl;
   else
      cout << "The result2 of the search  is: " << result1
           << endl;
}
```

```Output
The string to be searched is: f2d-1234-abcd
The character searched for in s1 is: d
The string beginning with the first occurrence
of the character 'd' is: d-1234-abcd
The result2 of the search is NULL.
```

## <a name="int_type"></a>  char_traits::int_type

一种整数类型，该类型可以表示类型为 `char_type` 的字符或文件尾 (EOF) 字符。

```cpp
typedef long int_type;
```

### <a name="remarks"></a>备注

它必须能为类型强制转换类型的值`CharType`到`int_type`然后返回到`CharType`而无需更改的原始值。

### <a name="example"></a>示例

有关如何声明和使用 `int_type` 的示例，请参阅 [eq_int_type](#eq_int_type) 的示例。

## <a name="length"></a>  char_traits::length

返回字符串的长度。

```cpp
static size_t length(const char_type* str);
```

### <a name="parameters"></a>参数

*str*<br/>
要测量其长度的 C 字符串。

### <a name="return-value"></a>返回值

要测量的序列中的元素数量，不包括 null 终止符。

### <a name="example"></a>示例

```cpp
// char_traits_length.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   const char* str1= "Hello";
   cout << "The C-string str1 is: " << str1 << endl;

   size_t lenStr1;
   lenStr1 = char_traits<char>::length ( str1 );
   cout << "The length of C-string str1 is: "
        << lenStr1 << "." << endl;
}
```

```Output
The C-string str1 is: Hello
The length of C-string str1 is: 5.
```

## <a name="lt"></a>  char_traits::lt

测试一个字符是否小于另一个。

```cpp
static bool lt(const char_type& _Ch1, const char_type& _Ch2);
```

### <a name="parameters"></a>参数

*_Ch1*<br/>
要测试是否小于的两个字符中的第一个。

*_Ch2*<br/>
要测试是否小于的两个字符中的第二个。

### <a name="return-value"></a>返回值

如果第一个字符小于第二个字符，则为 **true**；否则为 **false**。

### <a name="example"></a>示例

```cpp
// char_traits_lt.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   char_traits<char>::char_type ch1 =  'x';
   char_traits<char>::char_type ch2 =  'y';
   char_traits<char>::char_type ch3 =  'z';

   // Testing for less than
   bool b1 = char_traits<char>::lt ( ch1 , ch2 );
   if ( b1 )
      cout << "The character ch1 is less than "
           << "the character ch2." << endl;
   else
      cout << "The character ch1 is not less "
           << "than the character ch2." << endl;

   // An equivalent and alternatively test procedure
   if ( ch3 <  ch2 )
      cout << "The character ch3 is less than "
           << "the character ch2." << endl;
   else
      cout << "The character ch3 is not less "
           << "than the character ch2." << endl;
}
```

```Output
The character ch1 is less than the character ch2.
The character ch3 is not less than the character ch2.
```

## <a name="move"></a>  char_traits::move

将某个序列中指定数量的字符复制到另一个序列，可能会发生序列重叠。

此方法可能并不安全，因为它依赖于调用方检查所传递的值是否正确。 请考虑改为使用 [char_traits::_Move_s](#move_s)。

```cpp
static char_type *move(char_type* _To,
    const char_type* _From,
    size_t _Num);
```

### <a name="parameters"></a>参数

*_To*<br/>
用于接收复制的字符序列的字符串或字符数组的开头处的元素。

*_From*<br/>
要复制的源字符串或字符数组的开头处的元素。

*_Num*<br/>
要从源字符串复制的元素数。

### <a name="return-value"></a>返回值

第一个元素*待办*复制到用于接收复制的序列的字符的字符串或字符数组。

### <a name="remarks"></a>备注

源和目标可能会重叠。

### <a name="example"></a>示例

```cpp
// char_traits_move.cpp
// compile with: /EHsc /W3
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   char_traits<char>::char_type sFrom1[] =  "abcd-1234-abcd";
   char_traits<char>::char_type sTo1[] =  "ABCD-1234";
   char_traits<char>::char_type* result1;
   cout << "The source string sFrom1 is: " << sFrom1 << endl;
   cout << "The destination stringsTo1 is: " << sTo1 << endl;
   // Note: char_traits::move is potentially unsafe, consider
   // using char_traits::_Move_s instead.
   result1 = char_traits<char>::move ( sTo1 ,  sFrom1 , 4 );  // C4996
   cout << "The result1 = move ( sTo1 , sFrom1 , 4 ) is: "
        << result1 << endl << endl;

   // When source and destination overlap
   char_traits<char>::char_type sToFrom2[] = "abcd-1234-ABCD";
   char_traits<char>::char_type* result2;
   cout << "The source/destination string sToFrom2 is: "
        << sToFrom2 << endl;
   const char* findc = char_traits<char>::find ( sToFrom2 , 4 , 'c' );
   // Note: char_traits::move is potentially unsafe, consider
   // using char_traits::_Move_s instead.
   result2 = char_traits<char>::move ( sToFrom2 , findc , 8 );  // C4996
   cout << "The result2 = move ( sToFrom2 , findc , 8 ) is: "
        << result2 << endl;
}
```

```Output
The source string sFrom1 is: abcd-1234-abcd
The destination stringsTo1 is: ABCD-1234
The result1 = move ( sTo1 , sFrom1 , 4 ) is: abcd-1234

The source/destination string sToFrom2 is: abcd-1234-ABCD
The result2 = move ( sToFrom2 , findc , 8 ) is: cd-1234-4-ABCD
```

## <a name="move_s"></a>  char_traits::_Move_s

将某个序列中指定数量的字符复制到另一个序列，可能会发生序列重叠。

```cpp
static char_type *_Move_s(
    char_type* dest,
    size_t dest_size,
    const char_type* _From,
    size_t count);
```

### <a name="parameters"></a>参数

*dest*<br/>
用于接收复制的字符序列的字符串或字符数组的开头处的元素。

*dest_size*<br/>
大小*dest*。 如果`char_type`是**char**，则表明这是以字节为单位。 如果`char_type`是**wchar_t**，则以字为单位。

*_From*<br/>
要复制的源字符串或字符数组的开头处的元素。

*count*<br/>
要从源字符串复制的元素数。

### <a name="return-value"></a>返回值

第一个元素*dest*复制到用于接收复制的序列的字符的字符串或字符数组。

### <a name="remarks"></a>备注

源和目标可能会重叠。

### <a name="example"></a>示例

```cpp
// char_traits__Move_s.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
    using namespace std;

    char_traits<char>::char_type sFrom1[] =  "abcd-1234-abcd";
    char_traits<char>::char_type sTo1[] =  "ABCD-1234";
    char_traits<char>::char_type* result1;
    cout << "The source string sFrom1 is: " << sFrom1 << endl;
    cout << "The destination stringsTo1 is: " << sTo1 << endl;
    result1 = char_traits<char>::_Move_s(sTo1,
        char_traits<char>::length(sTo1), sFrom1, 4);
    cout << "The result1 = _Move_s(sTo1, "
         << "char_traits<char>::length(sTo1), sFrom1, 4) is: "
         << result1 << endl << endl;

    // When source and destination overlap
    char_traits<char>::char_type sToFrom2[] = "abcd-1234-ABCD";
    char_traits<char>::char_type* result2;
    cout << "The source/destination string sToFrom2 is: "
         << sToFrom2 << endl;
    const char* findc = char_traits<char>::find(sToFrom2, 4, 'c');
    result2 = char_traits<char>::_Move_s(sToFrom2,
        char_traits<char>::length(sToFrom2), findc, 8);
    cout << "The result2 = _Move_s(sToFrom2, "
        << "char_traits<char>::length(sToFrom2), findc, 8) is: "
         << result2 << endl;
}
```

```Output
The source string sFrom1 is: abcd-1234-abcd
The destination stringsTo1 is: ABCD-1234
The result1 = _Move_s(sTo1, char_traits<char>::length(sTo1), sFrom1, 4) is: abcd-1234

The source/destination string sToFrom2 is: abcd-1234-ABCD
The result2 = _Move_s(sToFrom2, char_traits<char>::length(sToFrom2), findc, 8) is: cd-1234-4-ABCD
```

## <a name="not_eof"></a>  char_traits::not_eof

测试字符是否不是文件尾 (EOF) 字符或 EOF。

```cpp
static int_type not_eof(const int_type& _Ch);
```

### <a name="parameters"></a>参数

*_Ch*<br/>
表示为 `int_type` 且要测试其是否为 EOF 字符的字符。

### <a name="return-value"></a>返回值

`int_type`字符的表示形式进行测试，如果`int_type`的字符不是等于 EOF 字符。

如果字符 `int_type` 值等于 EOF `int_type` 值，则为 **false**。

### <a name="example"></a>示例

```cpp
// char_traits_not_eof.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( ) {
   using namespace std;

   char_traits<char>::char_type ch1 =  'x';
   char_traits<char>::int_type int1;
   int1 = char_traits<char>:: to_int_type ( ch1 );
   cout << "The char_type ch1 is " << ch1
        << " corresponding to int_type: "
        << int1 << "." << endl;

   // EOF member function
   char_traits <char>::int_type int2 = char_traits<char>::eof ( );
   cout << "The eofReturn is: " << int2 << endl;

   // Testing for EOF or another character
   char_traits <char>::int_type eofTest1, eofTest2;
   eofTest1 = char_traits<char>::not_eof ( int1 );
   if ( !eofTest1 )
      cout << "The eofTest1 indicates ch1 is an EOF character."
              << endl;
   else
      cout << "The eofTest1 returns: " << eofTest1
           << ", which is the character: "
           <<  char_traits<char>::to_char_type ( eofTest1 )
           << "." << endl;

   eofTest2 = char_traits<char>::not_eof ( int2 );
   if ( !eofTest2 )
      cout << "The eofTest2 indicates int2 is an EOF character."
           << endl;
   else
      cout << "The eofTest1 returns: " << eofTest2
           << ", which is the character: "
           <<  char_traits<char>::to_char_type ( eofTest2 )
           << "." << endl;
}
```

```Output
The char_type ch1 is x corresponding to int_type: 120.
The eofReturn is: -1
The eofTest1 returns: 120, which is the character: x.
The eofTest2 indicates int2 is an EOF character.
```

## <a name="off_type"></a>  char_traits::off_type

一种整数类型，该类型可以表示流中两个位置之间的偏移量。

```cpp
typedef streamoff off_type;
```

### <a name="remarks"></a>备注

此类型为带符号整数，描述的对象可存储多个流定位操作涉及的字节偏移量。 它通常为 [streamoff](../standard-library/ios-typedefs.md#streamoff) 的同义词，但它具有与该类型实质上相同的属性。

## <a name="pos_type"></a>  char_traits::pos_type

一种整数类型，该类型可以表示流中的位置。

```cpp
typedef streampos pos_type;
```

### <a name="remarks"></a>备注

此类型描述了一个对象，该对象可以存储还原某个流内的任意文件位置指示器所需的全部信息。 它通常为 [streamoff](../standard-library/ios-typedefs.md#streampos) 的同义词，但在任何情况下，它都具有与该类型实质上相同的属性。

## <a name="state_type"></a>  char_traits::state_type

一种类型，该类型表示流中的多字节字符的转换状态。

```cpp
typedef implementation-defined state_type;
```

### <a name="remarks"></a>备注

此类型描述一个可以表示转换状态的对象。 它通常为 `mbstate_t` 的同义词，但在任何情况下，它具有与该类型实质上相同的属性。

## <a name="to_char_type"></a>  char_traits::to_char_type

将 `int_type` 字符转换为相应的 `char_type` 字符，并返回结果。

```cpp
static char_type to_char_type(const int_type& _Ch);
```

### <a name="parameters"></a>参数

*_Ch*<br/>
要表示为 `char_type` 的 `int_type` 字符。

### <a name="return-value"></a>返回值

对应于 `int_type` 字符的 `char_type` 字符。

值为 *_Ch*不能表示这种情况下生成未指定的结果。

### <a name="remarks"></a>备注

转换操作 [to_int_type](#to_int_type) 和 `to_char_type`彼此相反，因此：

`to_int_type` ( `to_char_type` ( *x* ) ) == *x*

针对任何 `int_type` *x* 且

`to_char_type` ( `to_int_type` ( *x* ) ) == *x*

针对任何 `char_type` *x*。

### <a name="example"></a>示例

```cpp
// char_traits_to_char_type.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   char_traits<char>::char_type ch1 =  'a';
   char_traits<char>::char_type ch2 =  'b';
   char_traits<char>::char_type ch3 =  'a';

   // Converting from char_type to int_type
   char_traits<char>::int_type int1, int2 , int3;
   int1 =char_traits<char>:: to_int_type ( ch1 );
   int2 =char_traits<char>:: to_int_type ( ch2 );
   int3 =char_traits<char>:: to_int_type ( ch3 );

   cout << "The char_types and corresponding int_types are:"
        << "\n    ch1 = " << ch1 << " corresponding to int1 = "
        << int1 << "."
        << "\n    ch2 = " << ch2 << " corresponding to int1 = "
        << int2 << "."
        << "\n    ch3 = " << ch3 << " corresponding to int1 = "
        << int3 << "." << endl << endl;

   // Converting from int_type back to char_type
   char_traits<char>::char_type rec_ch1;
   rec_ch1 = char_traits<char>:: to_char_type ( int1);
   char_traits<char>::char_type rec_ch2;
   rec_ch2 = char_traits<char>:: to_char_type ( int2);

   cout << "The recovered char_types and corresponding int_types are:"
        << "\n    recovered ch1 = " << rec_ch1 << " from int1 = "
        << int1 << "."
        << "\n    recovered ch2 = " << rec_ch2 << " from int2 = "
        << int2 << "." << endl << endl;

   // Testing that the conversions are inverse operations
   bool b1 = char_traits<char>::eq ( rec_ch1 , ch1 );
   if ( b1 )
      cout << "The recovered char_type of ch1"
           << " is equal to the original ch1." << endl;
   else
      cout << "The recovered char_type of ch1"
           << " is not equal to the original ch1." << endl;

   // An equivalent and alternatively test procedure
   if ( rec_ch2 == ch2 )
      cout << "The recovered char_type of ch2"
           << " is equal to the original ch2." << endl;
   else
      cout << "The recovered char_type of ch2"
           << " is not equal to the original ch2." << endl;
}
```

```Output
The char_types and corresponding int_types are:
    ch1 = a corresponding to int1 = 97.
    ch2 = b corresponding to int1 = 98.
    ch3 = a corresponding to int1 = 97.

The recovered char_types and corresponding int_types are:
    recovered ch1 = a from int1 = 97.
    recovered ch2 = b from int2 = 98.

The recovered char_type of ch1 is equal to the original ch1.
The recovered char_type of ch2 is equal to the original ch2.
```

## <a name="to_int_type"></a>  char_traits::to_int_type

将 `char_type` 字符转换为相应的 `int_type` 字符，并返回结果。

```cpp
static int_type to_int_type(const char_type& _Ch);
```

### <a name="parameters"></a>参数

*_Ch*<br/>
表示为 `int_type` 的 `char_type` 字符。

### <a name="return-value"></a>返回值

对应于 `char_type` 字符的 `int_type` 字符。

### <a name="remarks"></a>备注

转换操作 `to_int_type` 和 [to_char_type](#to_char_type) 彼此相反，因此：

`to_int_type` ( `to_char_type` ( *x* ) ) == *x*

针对任何 `int_type` *x*，且

`to_char_type` ( `to_int_type` ( *x* ) ) == *x*

针对任何 `char_type` *x*。

### <a name="example"></a>示例

```cpp
// char_traits_to_int_type.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   char_traits<char>::char_type ch1 = 'a';
   char_traits<char>::char_type ch2 = 'b';
   char_traits<char>::char_type ch3 = 'a';

   // Converting from char_type to int_type
   char_traits<char>::int_type int1, int2 , int3;
   int1 =char_traits<char>:: to_int_type ( ch1 );
   int2 =char_traits<char>:: to_int_type ( ch2 );
   int3 =char_traits<char>:: to_int_type ( ch3 );

   cout << "The char_types and corresponding int_types are:"
        << "\n    ch1 = " << ch1 << " corresponding to int1 = "
        << int1 << "."
        << "\n    ch2 = " << ch2 << " corresponding to int1 = "
        << int2 << "."
        << "\n    ch3 = " << ch3 << " corresponding to int1 = "
        << int3 << "." << endl << endl;

   // Converting from int_type back to char_type
   char_traits<char>::char_type rec_ch1;
   rec_ch1 = char_traits<char>:: to_char_type ( int1);
   char_traits<char>::char_type rec_ch2;
   rec_ch2 = char_traits<char>:: to_char_type ( int2);

   cout << "The recovered char_types and corresponding int_types are:"
        << "\n    recovered ch1 = " << rec_ch1 << " from int1 = "
        << int1 << "."
        << "\n    recovered ch2 = " << rec_ch2 << " from int2 = "
        << int2 << "." << endl << endl;

   // Testing that the conversions are inverse operations
   bool b1 = char_traits<char>::eq ( rec_ch1 , ch1 );
   if ( b1 )
      cout << "The recovered char_type of ch1"
           << " is equal to the original ch1." << endl;
   else
      cout << "The recovered char_type of ch1"
           << " is not equal to the original ch1." << endl;

   // An equivalent and alternatively test procedure
   if ( rec_ch2 == ch2 )
      cout << "The recovered char_type of ch2"
           << " is equal to the original ch2." << endl;
   else
      cout << "The recovered char_type of ch2"
           << " is not equal to the original ch2." << endl;
}
```

```Output
The char_types and corresponding int_types are:
    ch1 = a corresponding to int1 = 97.
    ch2 = b corresponding to int1 = 98.
    ch3 = a corresponding to int1 = 97.

The recovered char_types and corresponding int_types are:
    recovered ch1 = a from int1 = 97.
    recovered ch2 = b from int2 = 98.

The recovered char_type of ch1 is equal to the original ch1.
The recovered char_type of ch2 is equal to the original ch2.
```

## <a name="see-also"></a>请参阅

[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>

---
title: "&lt;bitset&gt; 运算符 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 84fe6a13-6f6e-4cdc-bf8f-6f65ab1134d4
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 2a1f1c21cdcd42e7e8d33eb6405297fc88635d87
ms.lasthandoff: 02/24/2017

---
# <a name="ltbitsetgt-operators"></a>&lt;bitset&gt; 运算符
||||  
|-|-|-|  
|[operator&amp;](#operator_amp_)|[operator&gt;&gt;](#operator_gt__gt_)|[operator&lt;&lt;](#operator_lt__lt_)|  
|[operator_xor](#operator_xor)|[operator_or](#operator_or)|  
  
##  <a name="a-nameoperatorampa--operatoramp"></a><a name="operator_amp_"></a>  operator&amp;  
 执行两个位组间的按位 `AND`。  
  
```  
template <size_t size>  
bitset<size>  
operator&(
    const bitset<size>& left,  
    const bitset<size>& right);
```  
  
### <a name="parameters"></a>参数  
 ` left`  
 要将其各自的元素使用按位 `AND` 组合的两个位组中的第一个。  
  
 ` right`  
 要将其各自的元素使用按位 `AND` 组合的两个 valarray 中的第二个。  
  
### <a name="return-value"></a>返回值  
 其元素是在 ` left` 和 ` right` 的相应元素上执行 `AND` 操作的结果的位组。  
  
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
  
##  <a name="a-nameoperatorltlta--operatorltlt"></a><a name="operator_lt__lt_"></a>  operator&lt;&lt;  
 将位序列的文本表示形式插入到输出流中。  
  
```  
 
template <class CharType, class Traits, size_t N>  
basic_ostream<CharType, Traits>& operator<<(
    basic_ostream<CharType, Traits>& ostr,  
    const bitset<N>& 
    right);
```  
  
### <a name="parameters"></a>参数  
 ` right`  
 要作为字符串插入到输出流的 **bitset\<N>** 类型的对象。  
  
### <a name="return-value"></a>返回值  
 **ostr** 中的位序列的文本表示形式。  
  
### <a name="remarks"></a>备注  
 模板函数将 **operator<<** 重载，从而使位组不必先转换为字符串即可写出。 该模板函数有效执行以下操作：  
  
 **ostr** << _ *Right*. [to_string](https://msdn.microsoft.com/library/2f93c55z.aspx) < **CharType**, **Traits**, **allocator**\< **CharType**> > ( )  
  
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
  
##  <a name="a-nameoperatorgtgta--operatorgtgt"></a><a name="operator_gt__gt_"></a>  operator&gt;&gt;  
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
 `_Istr`  
 输入到输入流以插入位组的字符串。  
  
 ` right`  
 正在从输入流接收位的位组。  
  
### <a name="return-value"></a>返回值  
 此模板函数返回字符串 `_Istr`。  
  
### <a name="remarks"></a>备注  
 模板函数将 **operator>>** 重载以在位组 _ *Right* the value bitset( `str`) 中进行存储，其中 `str` 是从 `_Istr` 中提取的 [basic_string](https://msdn.microsoft.com/library/syxtdd4f.aspx) < **CharType**, **Traits**, **allocator**\< **CharType**> > **&** 类型的对象。  
  
 模板函数从 `_Istr` 中提取元素并将其插入位组，直至：  
  
-   已从输入流提取所有的位元素并将其存储在位组中。  
  
-   此位组由输入流中的位填充。  
  
-   遇到非 0 也非 1 的输入元素。  
  
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
  
##  <a name="a-nameoperatorxora--operatorxor"></a><a name="operator_xor"></a>  operator_xor  
 执行两个位组间的按位 `EXCLUSIVE-OR`。  
  
```  
template <size_t size>  
bitset<size>  
operator^(
    const bitset<size>& left,  
    const bitset<size>& right);
```  
  
### <a name="parameters"></a>参数  
 ` left`  
 要将其各自的元素使用按位 `EXCLUSIVE-OR` 组合的两个位组中的第一个。  
  
 ` right`  
 要将其各自的元素使用按位 `EXCLUSIVE-OR` 组合的两个 valarray 中的第二个。  
  
### <a name="return-value"></a>返回值  
 其元素是在 ` left` 和 ` right` 的相应元素上执行 `EXCLUSIVE-OR` 操作的结果的位组。  
  
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
  
##  <a name="a-nameoperatorora--operatoror"></a><a name="operator_or"></a>  operator_or  
 执行两个位组间的按位 `OR`。  
  
```  
template <size_t size>  
bitset<size>  
operator|(
    const bitset<size>& left,  
    const bitset<size>& right);
```  
  
### <a name="parameters"></a>参数  
 ` left`  
 要将其各自的元素使用按位 `OR` 组合的两个位组中的第一个。  
  
 ` right`  
 要将其各自的元素使用按位 `OR` 组合的两个 valarray 中的第二个。  
  
### <a name="return-value"></a>返回值  
 其元素是在 ` left` 和 ` right` 的相应元素上执行 `OR` 操作的结果的位组。  
  
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
  
## <a name="see-also"></a>另请参阅  
 [\<bitset>](../standard-library/bitset.md)



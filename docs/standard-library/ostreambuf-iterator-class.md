---
title: "ostreambuf_iterator 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- streambuf/std::ostreambuf_iterator
- iterator/std::ostreambuf_iterator::char_type
- iterator/std::ostreambuf_iterator::ostream_type
- iterator/std::ostreambuf_iterator::streambuf_type
- iterator/std::ostreambuf_iterator::traits_type
- iterator/std::ostreambuf_iterator::failed
dev_langs:
- C++
helpviewer_keywords:
- std::ostreambuf_iterator [C++]
- std::ostreambuf_iterator [C++], char_type
- std::ostreambuf_iterator [C++], ostream_type
- std::ostreambuf_iterator [C++], streambuf_type
- std::ostreambuf_iterator [C++], traits_type
- std::ostreambuf_iterator [C++], failed
ms.assetid: dad1e624-2f45-4e94-8887-a885e95f9071
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 695b8415cd5958d200ba9120e28bebd543614f24
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="ostreambufiterator-class"></a>ostreambuf_iterator 类
模板类 ostreambuf_iterator 描述一个输出迭代器对象，该对象使用提取 **operator>>** 将连续的字符元素写入输出流。 `ostreambuf_iterator` 与 [ostream_iterator 类](../standard-library/ostream-iterator-class.md)迭代器的不同之处在于，要插入输出流的对象类型为字符而不是泛型类型。  
  
## <a name="syntax"></a>语法  
  
```
template <class CharType = char class Traits = char_traits <CharType>>
```  
  
#### <a name="parameters"></a>参数  
 `CharType`  
 表示 ostreambuf_iterator 字符类型的类型。 此参数为可选参数，默认值为 `char`。  
  
 `Traits`  
 表示 ostreambuf_iterator 字符类型的类型。 此自变量是可选自变量，默认值为 `char_traits`\<*CharType>。*  
  
## <a name="remarks"></a>备注  
 ostreambuf_iterator 类必须满足输出迭代器的需求。 可使用 `ostreambuf_iterator` 直接向输出流中写入算法。 此类可提供一种低级别流迭代器，允许访问字符形式的原始（未格式化）I/O 流，并且能够绕过与高级别流迭代器相关联的缓冲和字符转换。  
  
### <a name="constructors"></a>构造函数  
  
|||  
|-|-|  
|[ostreambuf_iterator](#ostreambuf_iterator_ostreambuf_iterator)|构造一个 `ostreambuf_iterator`，以便经初始化后向输出流写入字符。|  
  
### <a name="typedefs"></a>Typedef  
  
|||  
|-|-|  
|[char_type](#char_type)|为 `ostreambuf_iterator` 的字符类型提供的类型。|  
|[ostream_type](#ostreambuf_iterator_ostream_type)|为 `ostream_iterator` 的流类型提供的类型。|  
|[streambuf_type](#streambuf_type)|为 `ostreambuf_iterator` 的流类型提供的类型。|  
|[traits_type](#traits_type)|为 `ostream_iterator` 的字符特征类型提供的类型。|  
  
### <a name="member-functions"></a>成员函数  
  
|||  
|-|-|  
|[failed](#failed)|测试插入到输出流缓冲区的操作是否失败。|  
  
### <a name="operators"></a>运算符  
  
|||  
|-|-|  
|[operator*](#op_star)|用于实现输出迭代器表达式 * `i` = `x` 的取消引用运算符。|  
|[operator++](#op_add_add)|一种非功能性递增运算符，可向调用该运算之前所处理的同一对象返回 `ostreambuf_iterator`。|  
|[operator=](#op_eq)|此运算符会将一个字符插入到关联的流缓冲区。|  
  
## <a name="requirements"></a>惠?  
 **标头：** \<iterator>  
  
 **命名空间：** std  
  
##  <a name="char_type"></a>  ostreambuf_iterator::char_type  
 为 `ostreambuf_iterator` 的字符类型提供的类型。  
  
```
typedef CharType char_type;
```  
  
### <a name="remarks"></a>备注  
 该类型是模板参数 **CharType** 的同义词。  
  
### <a name="example"></a>示例  
  
```cpp  
// ostreambuf_iterator_char_type.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   typedef ostreambuf_iterator<char>::char_type CHT1;  
   typedef ostreambuf_iterator<char>::traits_type CHTR1;  
  
   // ostreambuf_iterator for stream cout  
   // with new line delimiter:  
    ostreambuf_iterator< CHT1, CHTR1> charOutBuf ( cout );  
  
   // Standard iterator interface for writing  
   // elements to the output streambuf:  
   cout << "The characters written to the output stream\n"  
        << " by charOutBuf are: ";  
 *charOutBuf = 'O';  
   charOutBuf++;  
 *charOutBuf = 'U';  
   charOutBuf++;  
 *charOutBuf = 'T';  
   charOutBuf++;  
   cout << "." << endl;  
}  
\* Output:   
The characters written to the output stream  
 by charOutBuf are: OUT.  
*\  
```  
  
##  <a name="failed"></a>  ostreambuf_iterator::failed  
 测试插入到输出流缓冲区的操作是否失败。  
  
```
bool failed() const throw();
```  
  
### <a name="return-value"></a>返回值  
 如果之前成功插入到输出流缓冲区，则为 **true**；否则为 **false**。  
  
### <a name="remarks"></a>备注  
 如果在以前对成员 `operator=` 的任何使用中，对 **subf**_-> `sputc` 的调用返回 **eof**，则成员函数将返回 **true**。  
  
### <a name="example"></a>示例  
  
```cpp  
// ostreambuf_iterator_failed.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // ostreambuf_iterator for stream cout  
   ostreambuf_iterator<char> charOut ( cout );  
  
 *charOut = 'a';  
   charOut ++;  
 *charOut  = 'b';  
   charOut ++;     
 *charOut = 'c';  
   cout << " are characters output individually." << endl;  
  
   bool b1 = charOut.failed ( );  
   if (b1)   
       cout << "At least one insertion failed." << endl;  
   else  
       cout << "No insertions failed." << endl;  
}  
\* Output:   
abc are characters output individually.  
No insertions failed.  
*\  
```  
  
##  <a name="op_star"></a>ostreambuf_iterator::operator*  
 用于实现输出迭代器表达式 \* *i* = *x* 的非功能性的取消引用运算符。  
  
```
ostreambuf_iterator<CharType, Traits>& operator*();
```  
  
### <a name="return-value"></a>返回值  
 ostreambuf 迭代器对象。  
  
### <a name="remarks"></a>备注  
 此运算符函数仅存在于输出迭代器表达式 \* *i* = *x* 中，以便将字符输出到流缓冲区。 应用于 ostreambuf 迭代器，它将返回该迭代器；**\*iter** 返回 **iter**，  
  
### <a name="example"></a>示例  
  
```cpp  
// ostreambuf_iterator_op_deref.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // ostreambuf_iterator for stream cout  
   // with new line delimiter  
   ostreambuf_iterator<char> charOutBuf ( cout );  
  
   // Standard iterator interface for writing  
   // elements to the output stream  
   cout << "Elements written to output stream:" << endl;  
 *charOutBuf = 'O';  
   charOutBuf++;   // no effect on iterator position  
 *charOutBuf = 'U';  
 *charOutBuf = 'T';  
}  
\* Output:   
Elements written to output stream:  
OUT  
*\  
```  
  
##  <a name="op_add_add"></a>ostreambuf_iterator::operator++  
 一种非功能性递增运算符，可向调用该运算之前所处理的同一字符返回 ostream 迭代器。  
  
```
ostreambuf_iterator<CharType, Traits>& operator++();
ostreambuf_iterator<CharType, Traits>& operator++(int);
```  
  
### <a name="return-value"></a>返回值  
 对最初被寻址的字符的引用或对可转换为 `ostreambuf_iterator`\< **CharType**, **Traits**> 的实现定义的对象的引用。  
  
### <a name="remarks"></a>备注  
 该运算符用于实现输出迭代器表达式 \* *i* = *x*。  
  
### <a name="example"></a>示例  
  
```cpp  
// ostreambuf_iterator_op_incr.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // ostreambuf_iterator for stream cout  
   // with new line delimiter  
   ostreambuf_iterator<char> charOutBuf ( cout );  
  
   // Standard iterator interface for writing  
   // elements to the output stream  
   cout << "Elements written to output stream:" << endl;  
 *charOutBuf = 'O';  
   charOutBuf++;      // No effect on iterator position  
 *charOutBuf = 'U';  
 *charOutBuf = 'T';     
}  
\* Output:   
Elements written to output stream:  
OUT  
*\  
```  
  
##  <a name="op_eq"></a>ostreambuf_iterator::operator=  
 此运算符会将一个字符插入到关联的流缓冲区。  
  
```
ostreambuf_iterator<CharType, Traits>& operator=(CharType _Char);
```  
  
### <a name="parameters"></a>参数  
 `_Char`  
 要插入到流缓冲区的字符。  
  
### <a name="return-value"></a>返回值  
 对插入到流缓冲区的字符的引用。  
  
### <a name="remarks"></a>备注  
 用于实现输出迭代器表达式 \* *i* = *x* 以写入输出流的赋值运算符。  
  
### <a name="example"></a>示例  
  
```cpp  
// ostreambuf_iterator_op_assign.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // ostreambuf_iterator for stream cout  
   // with new line delimiter  
   ostreambuf_iterator<char> charOutBuf ( cout );  
  
   // Standard iterator interface for writing  
   // elements to the output stream  
   cout << "Elements written to output stream:" << endl;  
 *charOutBuf = 'O';  
   charOutBuf++;      // No effect on iterator position  
 *charOutBuf = 'U';  
 *charOutBuf = 'T';     
}  
\* Output:   
Elements written to output stream:  
OUT  
*\  
```  
  
##  <a name="ostreambuf_iterator_ostreambuf_iterator"></a>  ostreambuf_iterator::ostreambuf_iterator  
 构造一个 `ostreambuf_iterator`，以便经初始化后向输出流写入字符。  
  
```
ostreambuf_iterator(streambuf_type* strbuf) throw();
ostreambuf_iterator(ostream_type& Ostr) throw();
```  
  
### <a name="parameters"></a>参数  
 `strbuf`  
 用于初始化输出流缓冲区指针的输出 streambuf 对象。  
  
 `Ostr`  
 用于初始化输出流缓冲区指针的输出流对象。  
  
### <a name="remarks"></a>备注  
 第一个构造函数通过 `strbuf` 初始化输出流缓冲区指针。  
  
 第二个构造函数通过 `Ostr` 初始化输出流缓冲区指针。 `rdbuf`。 存储的指针不能为空指针。  
  
### <a name="example"></a>示例  
  
```cpp  
// ostreambuf_iteratorOstreambuf_iterator.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // ostreambuf_iterator for stream cout  
   ostreambuf_iterator<char> charOut ( cout );  
  
 *charOut = 'O';  
   charOut ++;  
 *charOut  = 'U';  
   charOut ++;     
 *charOut = 'T';  
   cout << " are characters output individually." << endl;  
  
   ostreambuf_iterator<char> strOut ( cout );  
   string str = "These characters are being written to the output stream.\n ";  
   copy ( str.begin ( ), str. end ( ), strOut );  
}  
\* Output:   
OUT are characters output individually.  
These characters are being written to the output stream.  
*\  
```  
  
##  <a name="ostreambuf_iterator_ostream_type"></a>  ostreambuf_iterator::ostream_type  
 为 `ostream_iterator` 的流类型提供的类型。  
  
```
typedef basicOstream<CharType, Traits> ostream_type;
```  
  
### <a name="remarks"></a>备注  
 该类型是 `basicOstream`\<**CharType**, **Traits**> 的同义词  
  
### <a name="example"></a>示例  
  有关如何声明和使用 `ostream_type` 的示例，请参阅 [ostreambuf_iterator](#ostreambuf_iterator_ostreambuf_iterator)。  
  
##  <a name="streambuf_type"></a>  ostreambuf_iterator::streambuf_type  
 为 `ostreambuf_iterator` 的流类型提供的类型。  
  
```
typedef basic_streambuf<CharType, Traits> streambuf_type;
```  
  
### <a name="remarks"></a>备注  
 该类型为 `basic_streambuf`\<**CharType**, **Traits**> 的同义词，这是 I/O 缓冲区的流类，当专用化为字符类型 `char` 时将成为 `streambuf`。  
  
### <a name="example"></a>示例  
  有关如何声明和使用 `streambuf_type` 的示例，请参阅 [ostreambuf_iterator](#ostreambuf_iterator_ostreambuf_iterator)。  
  
##  <a name="traits_type"></a>  ostreambuf_iterator::traits_type  
 为 `ostream_iterator` 的字符特征类型提供的类型。  
  
```
typedef Traits traits_type;
```  
  
### <a name="remarks"></a>备注  
 该类型是模板参数 **Traits** 的同义词。  
  
### <a name="example"></a>示例  
  
```cpp  
// ostreambuf_iterator_traits_type.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   typedef ostreambuf_iterator<char>::char_type CHT1;  
   typedef ostreambuf_iterator<char>::traits_type CHTR1;  
  
   // ostreambuf_iterator for stream cout  
   // with new line delimiter:  
    ostreambuf_iterator< CHT1, CHTR1> charOutBuf ( cout );  
  
   // Standard iterator interface for writing  
   // elements to the output streambuf:  
   cout << "The characters written to the output stream\n"  
        << " by charOutBuf are: ";  
 *charOutBuf = 'O';  
   charOutBuf++;  
 *charOutBuf = 'U';  
   charOutBuf++;  
 *charOutBuf = 'T';  
   charOutBuf++;  
   cout << "." << endl;  
}  
\* Output:   
The characters written to the output stream  
 by charOutBuf are: OUT.  
*\  
```  
  
## <a name="see-also"></a>请参阅  
 [\<iterator>](../standard-library/iterator.md)   
 [C++ 标准库中的线程安全性](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)




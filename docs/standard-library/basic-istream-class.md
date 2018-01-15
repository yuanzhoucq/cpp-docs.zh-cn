---
title: "basic_istream 类 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- istream/std::basic_istream
- istream/std::basic_istream::gcount
- istream/std::basic_istream::get
- istream/std::basic_istream::getline
- 'istream/std::basic_istream::'
- istream/std::basic_istream::peek
- istream/std::basic_istream::putback
- istream/std::basic_istream::read
- istream/std::basic_istream::readsome
- istream/std::basic_istream::seekg
- istream/std::basic_istream::sentry
- istream/std::basic_istream::swap
- istream/std::basic_istream::sync
- istream/std::basic_istream::tellg
- istream/std::basic_istream::unget
dev_langs: C++
helpviewer_keywords:
- std::basic_istream [C++]
- std::basic_istream [C++], gcount
- std::basic_istream [C++], get
- std::basic_istream [C++], getline
- std::basic_istream [C++], OVERWRITE
- std::basic_istream [C++], peek
- std::basic_istream [C++], putback
- std::basic_istream [C++], read
- std::basic_istream [C++], readsome
- std::basic_istream [C++], seekg
- std::basic_istream [C++], sentry
- std::basic_istream [C++], swap
- std::basic_istream [C++], sync
- std::basic_istream [C++], tellg
- std::basic_istream [C++], unget
ms.assetid: c7c27111-de6d-42b4-95a3-a7e65259bf17
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 14f41a90aab8e95d336df6724a7217947ec1c57c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="basicistream-class"></a>basic_istream 类
描述一个对象，它控制从具有类型为 `Elem` 的元素的流缓冲区提取元素和编码对象的操作，其中该类型也称为 [char_type](../standard-library/basic-ios-class.md#char_type)，其字符特征由类 *Tr*（也称为 [traits_type](../standard-library/basic-ios-class.md#traits_type)）决定。  
  
## <a name="syntax"></a>语法  
  
```  
template <class Elem, class Tr = char_traits<Elem>>  
class basic_istream : virtual public basic_ios<Elem, Tr>  
```  
  
## <a name="remarks"></a>备注  
 大多数重载 [operator>>](#op_gt_gt) 的成员函数都是格式化的输入函数。 它们遵循以下模式：  
  
```cpp  
iostate state = goodbit;
const sentry ok(*this);

if (ok)
{
    try
    {
        /*extract elements and convert
            accumulate flags in state.
            store a successful conversion*/
    }
    catch (...)
    {
        try
        {
            setstate(badbit);

        }
        catch (...)
        {
        }
        if ((exceptions()& badbit) != 0)
            throw;
    }
}
setstate(state);

return (*this);
```  
  
 许多其他成员函数是未格式化的输入函数。 它们遵循以下模式：  
  
```cpp  
iostate state = goodbit;
count = 0;    // the value returned by gcount  
const sentry ok(*this, true);

if (ok)
{
    try
    {
        /* extract elements and deliver
            count extracted elements in count
            accumulate flags in state */
    }
    catch (...)
    {
        try
        {
            setstate(badbit);

        }
        catch (...)
        {
        }
        if ((exceptions()& badbit) != 0)
            throw;
    }
}
setstate(state);
```  
  
 如果它们在提取元素时遇到文件结尾，两组函数都调用 [setstate](../standard-library/basic-ios-class.md#setstate)( **eofbit**)。  
  
 类 `basic_istream`< `Elem`, *Tr*> 的对象将存储：  
  
-   类 [basic_ios](../standard-library/basic-ios-class.md)< `Elem`, *Tr*> `.` 的虚拟公共基对象  
  
-   最后一个未格式化的输入操作的提取计数（在之前的代码中被称为**计数**）。  
  
## <a name="example"></a>示例  
 请参阅 [basic_ifstream 类](../standard-library/basic-ifstream-class.md)的示例，了解输入流的详细信息。  
  
### <a name="constructors"></a>构造函数  
  
|||  
|-|-|  
|[basic_istream](#basic_istream)|构造 `basic_istream` 类型的对象。|  
  
### <a name="member-functions"></a>成员函数  
  
|||  
|-|-|  
|[gcount](#gcount)|返回在最后一个未格式化输入期间读取的字符数。|  
|[get](#get)|从输入流中读取一个或多个字符。|  
|[getline](#getline)|从输入流中读取一行。|  
|[ignore](#ignore)|导致从当前读取位置跳过大量元素。|  
|[peek](#peek)|返回要读取的下一字符。|  
|[putback](#putback)|将指定的字符放入流。|  
|[read](#read)|从流中读取指定数目的字符，并将其存储到数组中。|  
|[readsome](#readsome)|仅从缓冲区读取。|  
|[seekg](#seekg)|在流中移动读取位置。|  
|[sentry](#sentry)|嵌套类描述一个其声明构造了格式化和未格式化的输入函数的对象。|  
|[swap](#swap)|将此 `basic_istream` 对象与所提供的 `basic_istream` 对象参数进行交换。|  
|[sync](#sync)|将与流关联的输入设备与流的缓冲区进行同步。|  
|[tellg](#tellg)|报告流中的当前读取位置。|  
|[unget](#unget)|将最近读取的字符放回流中。|  
  
### <a name="operators"></a>运算符  
  
|||  
|-|-|  
|[operator>>](#op_gt_gt)|调用输入流上的函数或从输入流中读取格式化数据。|  
|[operator=](#op_eq)|将运算符右侧上的 `basic_istream` 分配给此对象。 这是涉及不会留下副本的 `rvalue` 引用的移动赋值运算符。|  
  
## <a name="requirements"></a>惠?  
 **标头：**\<istream>  
  
 **命名空间：** std  
  
##  <a name="basic_istream"></a>  basic_istream::basic_istream  
 构造 `basic_istream` 类型的对象。  
  
```  
explicit basic_istream(
    basic_streambuf<Elem, Tr>* strbuf,  
    bool _Isstd = false);

basic_istream(basic_istream&& right);
```  
  
### <a name="parameters"></a>参数  
 `strbuf`  
 类型 [basic_streambuf](../standard-library/basic-streambuf-class.md) 的对象。  
  
 `_Isstd`  
 如果这是一个标准流，则为 `true`，否则为 `false`。  
  
 `right`  
 要复制的 `basic_istream` 对象。  
  
### <a name="remarks"></a>备注  
 第一个构造函数通过调用 [init](../standard-library/basic-ios-class.md#init)(_S `trbuf`) 初始化基类。 它还在提取计数中存储零。 有关此提取计数的详细信息，请参阅 [basic_istream 类](../standard-library/basic-istream-class.md)概述主题的“备注”部分。  
  
 第二个构造函数通过调用 `move( right)` 初始化基类。 它还在提取计数中存储 _R `ight.gcount()`，并在 _R `ight` 的提取计数中存储零。  
  
### <a name="example"></a>示例  
  请参阅 [basic_ifstream::basic_ifstream](../standard-library/basic-ifstream-class.md#basic_ifstream) 的示例，了解输入流的详细信息。  
  
##  <a name="gcount"></a>  basic_istream::gcount  
 返回在最后一个未格式化输入期间读取的字符数。  
  
```  
streamsize gcount() const;
```  
  
### <a name="return-value"></a>返回值  
 提取计数。  
  
### <a name="remarks"></a>备注  
 使用 [basic_istream::get](#get) 读取未格式化的字符。  
  
### <a name="example"></a>示例  
  
```cpp  
// basic_istream_gcount.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
int main( )   
{  
   cout << "Type the letter 'a': ";  
  
   ws( cin );  
   char c[10];  
  
   cin.get( &c[0],9 );  
   cout << c << endl;  
  
   cout << cin.gcount( ) << endl;  
}  
```  
  
```Output  
  
a  
  
```  
  
```Output  
  
      aType the letter 'a':  
a  
1  
```  
  
##  <a name="get"></a>  basic_istream::get  
 从输入流中读取一个或多个字符。  
  
```  
int_type get();

basic_istream<Elem, Tr>& get(Elem& Ch);
basic_istream<Elem, Tr>& get(Elem* str, streamsize count);
basic_istream<Elem, Tr>& get(Elem* str, streamsize count, Elem Delim);

basic_istream<Elem, Tr>& get(basic_streambuf<Elem, Tr>& strbuf);
basic_istream<Elem, Tr>& get(basic_streambuf<Elem, Tr>& strbuf, Elem Delim);
```  
  
### <a name="parameters"></a>参数  
 `count`  
 要从 `strbuf` 读取的字符数。  
  
 `Delim`  
 如果在 `count` 前遇到而应终止读取的字符。  
  
 `str`  
 写入的字符串。  
  
 `Ch`  
 要获取的字符。  
  
 `strbuf`  
 要写入的缓冲区。  
  
### <a name="return-value"></a>返回值  
 get 的无参数形式返回作为整数或文件结尾读取的元素。 其余形式返回流 (* `this`)。  
  
### <a name="remarks"></a>备注  
 如果可以，其中第一个未格式化的输入函数提取一个元素，如通过 `rdbuf`-> `sbumpc` 返回一样。 否则，它将返回 **traits_type::**[eof](../standard-library/char-traits-struct.md#eof)。 如果函数没有提取任何元素，则会调用 [setstate](../standard-library/basic-ios-class.md#setstate)( **failbit**)。  
  
 第二个函数以相同的方式提取 [int_type](../standard-library/basic-ios-class.md#int_type) 元素 `meta`。 如果 `meta` 经比较等于 **traits_type::eof**，则此函数调用 `setstate`( **failbit**)。 否则，它将在 `Ch` 中存储 **traits_type::**[to_char_type](../standard-library/char-traits-struct.md#to_char_type)( `meta`)。 该函数返回 **\*this**。  
  
 第三个函数返回**获取**(_ *Str*， `count`， `widen`('\  **n** '))。  
  
 第四个函数提取最多 `count` - 1 个元素并将它们存储在以 _ *Str* 开头的数组中。 在存储任何提取的元素后，它始终存储 `char_type`。 按测试顺序，提取在以下位置停止：  
  
-   在文件结尾。  
  
-   函数提取经比较与 `Delim` 相等的元素并将该元素放回受控序列后。  
  
-   函数提取 `count` - 1 个元素后。  
  
 如果函数没有提取任何元素，则会调用 `setstate`( **failbit**)。 不管怎样，它均将返回 **\*this**。  
  
 第五个函数将返回**获取**( **strbuf**， `widen`('\  **n** '))。  
  
 第六个函数提取元素并将它们插入到 **strbuf**。 提取在文件结尾或在经比较等于 *Delim* 的元素（该元素未提取）上停止。 如果插入失败或引发异常（可捕获异常但不会再次引发），提取也会在未提取所讨论的元素的情况下停止。 如果函数没有提取任何元素，则会调用 `setstate`( **failbit**)。 不管怎样，该函数均将返回 **\*this**。  
  
### <a name="example"></a>示例  
  
```cpp  
// basic_istream_get.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
int main( )   
{  
   char c[10];  
  
   c[0] = cin.get( );  
   cin.get( c[1] );  
   cin.get( &c[2],3 );  
   cin.get( &c[4], 4, '7' );  
  
   cout << c << endl;  
}  
```  
  
```Output  
  
1111  
```  
  
##  <a name="getline"></a>  basic_istream::getline  
 从输入流中获取一行。  
  
```  
basic_istream<Elem, Tr>& getline(
    char_type* str,   
    streamsize count);

basic_istream<Elem, Tr>& getline(
    char_type* str,   
    streamsize count,   
    char_type Delim);
```  
  
### <a name="parameters"></a>参数  
 `count`  
 要从 **strbuf** 读取的字符数。  
  
 `Delim`  
 如果在 `count` 前遇到而应终止读取的字符。  
  
 `str`  
 写入的字符串。  
  
### <a name="return-value"></a>返回值  
 流 ( **\*this**)。  
  
### <a name="remarks"></a>备注  
 第一个未格式化输入函数返回**getline**(_ *Str*， `count`， `widen`( `\`  **n** '))。  
  
 第二个函数提取最多 `count` - 1 个元素并将它们存储在以 _ *Str* 开头的数组中。 在存储任何提取的元素后，它始终存储字符串终止字符。 按测试顺序，提取在以下位置停止：  
  
-   在文件结尾。  
  
-   函数提取经比较与 `Delim` 相等的元素后，既不放回该元素，也不将它追加到受控序列的情况。  
  
-   函数提取 `count` - 1 个元素后。  
  
 如果函数没有提取任何元素或提取了 `count` - 1 个元素，则会调用 [setstate](../standard-library/basic-ios-class.md#setstate)( **failbit**)。 不管怎样，它均将返回 **\*this**。  
  
### <a name="example"></a>示例  
  
```cpp  
// basic_istream_getline.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
int main( )   
{  
   char c[10];  
  
   cin.getline( &c[0], 5, '2' );  
   cout << c << endl;  
}  
```  
  
```Output  
  
121  
```  
  
##  <a name="ignore"></a>  basic_istream::ignore  
 导致从当前读取位置跳过大量元素。  
  
```  
basic_istream<Elem, Tr>& ignore(
    streamsize count = 1,  
    int_type Delim = traits_type::eof());
```  
  
### <a name="parameters"></a>参数  
 `count`  
 要从当前读取位置跳过的元素数。  
  
 `Delim`  
 如果在 count 之前遇到该元素，则会导致 **ignore** 返回并允许读取 `Delim` 之后的所有元素。  
  
### <a name="return-value"></a>返回值  
 流 ( **\*this**)。  
  
### <a name="remarks"></a>备注  
 未格式化的输入函数提取最多 `count` 个元素并将其放弃。 如果 `count` 等于 **numeric_limits\<int>::max**，则它被视为任意大小。 提取尽早停止或元素上的文件结束`Ch`以便**traits_type::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( `Ch`) 进行比较等于*Delim* (此外在提取）。 该函数返回 **\*this**。  
  
### <a name="example"></a>示例  
  
```cpp  
// basic_istream_ignore.cpp  
// compile with: /EHsc  
#include <iostream>  
int main( )   
{  
   using namespace std;  
   char chararray[10];  
   cout << "Type 'abcdef': ";  
   cin.ignore( 5, 'c' );  
   cin >> chararray;  
   cout << chararray;  
}  
```  
  
```Output  
Type 'abcdef': abcdef  
def  
```  
  
##  <a name="op_gt_gt"></a>基本\_istream::operator >>
  
调用输入流上的函数或从输入流中读取格式化数据。  
  
```  
basic_istream& operator>>(basic_istream& (* Pfn)(basic_istream&));
basic_istream& operator>>(ios_base& (* Pfn)(ios_base&));
basic_istream& operator>>(basic_ios<Elem, Tr>& (* Pfn)(basic_ios<Elem, Tr>&));  
basic_istream& operator>>(basic_streambuf<Elem, Tr>* strbuf);
basic_istream& operator>>(bool& val);
basic_istream& operator>>(short& val);
basic_istream& operator>>(unsigned short& val);
basic_istream& operator>>(int& val);
basic_istream& operator>>(unsigned int& val);
basic_istream& operator>>(long& val);
basic_istream& operator>>(unsigned long& val);
basic_istream& operator>>(long long& val);
basic_istream& operator>>(unsigned long long& val);
basic_istream& operator>>(void *& val);
basic_istream& operator>>(float& val);
basic_istream& operator>>(double& val);
basic_istream& operator>>(long double& val);
```  
  
### <a name="parameters"></a>参数  
 `Pfn`  
 函数指针。  
  
 `strbuf`  
 **stream_buf** 类型的对象。  
  
 `val`  
 要从流中读取的值。  
  
### <a name="return-value"></a>返回值  
 流 ( **\*this**)。  
  
### <a name="remarks"></a>备注  
 `<istream>` 标头还定义多个全局提取运算符。 有关详细信息，请参阅 [operator>> (\<istream>)](../standard-library/istream-operators.md#op_gt_gt)。  
  
 第一个成员函数确保 **istr** >> `ws` 形式的表达式调用 [ws](../standard-library/istream-functions.md#ws)( **istr**)，然后返回 **\*this**。 第二个和第三个函数确保其他操控器（如 [hex ](../standard-library/ios-functions.md#hex)）表现相似。 其余功能构成格式化的输入函数。  
  
 函数：  
  
```  
basic_istream& operator>>(
    basic_streambuf<Elem, Tr>* strbuf);
```  
  
 如果 _ *Strbuf* 不是空指针，则提取元素，并将其插入到 `strbuf` 中。 提取在文件结尾停止。 如果插入失败或引发异常（可捕获异常但不会再次引发），提取也会在未提取所讨论的元素的情况下停止。 如果函数没有提取任何元素，则会调用 [setstate](../standard-library/basic-ios-class.md#setstate)( **failbit**)。 不管怎样，该函数均将返回 **\*this**。  
  
 函数：  
  
```  
basic_istream& operator>>(bool& val);
```  
  
 通过调用 [use_facet](../standard-library/basic-filebuf-class.md#open) < `num_get`\< **Elem**, **InIt**>( [getloc](../standard-library/ios-base-class.md#getloc)) 提取字段，并将其转换为布尔值。 [get](../standard-library/ios-base-class.md#getloc)( **InIt**( [rdbuf](../standard-library/basic-ios-class.md#rdbuf)), `Init`(0), **\*this**, `getloc`, `val`)。 此处，将 **InIt** 定义为 [istreambuf_iterator](../standard-library/istreambuf-iterator-class.md)\< **Elem**, **Tr**>。 该函数返回 **\*this**。  
  
 函数：  
  
```  
basic_istream& operator>>(short& val);
basic_istream& operator>>(unsigned short& val);
basic_istream& operator>>(int& val);
basic_istream& operator>>(unsigned int& val);
basic_istream& operator>>(long& val);
basic_istream& operator>>(unsigned long& val); 
basic_istream& operator>>(long long& val);
basic_istream& operator>>(unsigned long long& val); 
basic_istream& operator>>(void *& val);
```  
  
 通过调用 `use_facet`< `num_get`\< **Elem**, **InIt**>( `getloc`)，每个函数均可提取字段，并将其转换为数字值。 [get](#get)( **InIt**( `rdbuf`), `Init`(0), **\*this**, `getloc`, `val`)。 在这里， **InIt**定义为`istreambuf_iterator` \< **Elem**， **Tr**>，和`val`具有类型**长**，`unsigned long`，或**void \*** 根据需要。  
  
 如果转换的值不能表示为 `val` 类型，则函数调用 [setstate](../standard-library/basic-ios-class.md#setstate)( **failbit**)。 不管怎样，该函数均将返回 **\*this**。  
  
 函数：  
  
```  
basic_istream& operator>>(float& val);
basic_istream& operator>>(double& val);
basic_istream& operator>>(long double& val);
```  
  
 通过调用 `use_facet`< `num_get`\< **Elem**, **InIt**>( `getloc`)，每个函数均可提取字段，并将其转换为数字值。 **get**( **InIt**( `rdbuf`), `Init`(0), **\*this**, `getloc`, `val`)。 此处，**InIt** 定义为 `istreambuf_iterator`\< **Elem**, **Tr**>，而 `val` 根据需要具有类型 **double** 或 `long double`。  
  
 如果转换的值不能表示为 `val` 类型，则函数调用 `setstate`( **failbit**)。 不管怎样，它均将返回 **\*this**。  
  
### <a name="example"></a>示例  
  
```cpp  
// istream_basic_istream_op_is.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
  
ios_base& hex2( ios_base& ib )   
{  
   ib.unsetf( ios_base::dec );  
   ib.setf( ios_base::hex );  
   return ib;  
}  
  
basic_istream<char, char_traits<char> >& somefunc(basic_istream<char, char_traits<char> > &i)  
{  
   if ( i == cin )   
   {  
      cerr << "i is cin" << endl;  
   }  
   return i;  
}  
  
int main( )   
{  
   int i = 0;  
   cin >> somefunc;  
   cin >> i;  
   cout << i << endl;  
   cin >> hex2;  
   cin >> i;  
   cout << i << endl;  
}  
```  
  
##  <a name="op_eq"></a>  basic_istream::operator=  
 将运算符右侧上的 `basic_istream` 分配给此对象。 这是涉及不会留下副本的 `rvalue` 引用的移动赋值运算符。  
  
```  
basic_istream& operator=(basic_istream&& right);
```  
  
### <a name="parameters"></a>参数  
 `right`  
 对 `basic_ifstream` 对象的 `rvalue` 引用。  
  
### <a name="return-value"></a>返回值  
 返回 *this。  
  
### <a name="remarks"></a>备注  
 成员运算符调用 swap `( right)`。  
  
##  <a name="peek"></a>  basic_istream::peek  
 返回要读取的下一字符。  
  
```  
int_type peek();
```  
  
### <a name="return-value"></a>返回值  
 要读取的下一字符。  
  
### <a name="remarks"></a>备注  
 如果可以，未格式化的输入函数提取一个元素，如通过 `rdbuf` -> [sgetc](../standard-library/basic-streambuf-class.md#sgetc) 返回一样。 否则，它将返回 **traits_type::**[eof](../standard-library/char-traits-struct.md#eof)。  
  
### <a name="example"></a>示例  
  
```cpp  
// basic_istream_peek.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
int main( )   
{  
   char c[10], c2;  
   cout << "Type 'abcde': ";  
  
   c2 = cin.peek( );  
   cin.getline( &c[0], 9 );  
  
   cout << c2 << " " << c << endl;  
}  
```  
  
```Output  
  
abcde  
  
```  
  
```Output  
  
      abcdeType 'abcde': abcde  
a abcde  
```  
  
##  <a name="putback"></a>  basic_istream::putback  
 将指定的字符放入流。  
  
```  
basic_istream<Elem, Tr>& putback(
    char_type Ch);
```  
  
### <a name="parameters"></a>参数  
 `Ch`  
 要放回到流中的字符。  
  
### <a name="return-value"></a>返回值  
 流 ( **\*this**)。  
  
### <a name="remarks"></a>备注  
 如果可以，[未格式化的输入函数](../standard-library/basic-istream-class.md)放回 `Ch`，如通过调用 [rdbuf](../standard-library/basic-ios-class.md#rdbuf)`->`[sputbackc](../standard-library/basic-streambuf-class.md#sputbackc) 放回一样。 如果 rdbuf 是空指针，或者如果对 `sputbackc` 的调用返回 **traits_type::**[eof](../standard-library/char-traits-struct.md#eof)，则函数调用 [setstate](../standard-library/basic-ios-class.md#setstate)( **badbit**)。 不管怎样，它均将返回 **\*this**。  
  
### <a name="example"></a>示例  
  
```cpp  
// basic_istream_putback.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
int main( )   
{  
   char c[10], c2, c3;  
  
   c2 = cin.get( );  
   c3 = cin.get( );  
   cin.putback( c2 );  
   cin.getline( &c[0], 9 );  
   cout << c << endl;  
}  
```  
  
```Output  
  
qwq  
```  
  
##  <a name="read"></a>  basic_istream::read  
 从流中读取指定数目的字符，并将其存储到数组中。  
  
 此方法可能并不安全，因为它依赖于调用方检查所传递的值是否正确。  
  
```  
basic_istream<Elem, Tr>& read(
    char_type* str,   
    streamsize count);
```  
  
### <a name="parameters"></a>参数  
 `str`  
 要从中读取字符的数组。  
  
 `count`  
 要读取的字符数。  
  
### <a name="return-value"></a>返回值  
 流 ( `*this`)。  
  
### <a name="remarks"></a>备注  
 未格式化的输入函数提取最多 `count` 个元素，并将它们存储在以 _ `Str` 开头的数组中。 提取在文件结尾停止，在这种情况下，函数调用 [setstate](../standard-library/basic-ios-class.md#setstate)( `failbit`)。 不管怎样，它均将返回 `*this`。  
  
### <a name="example"></a>示例  
  
```cpp  
// basic_istream_read.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
int main()  
{  
    char c[10];  
    int count = 5;  
  
    cout << "Type 'abcde': ";  
  
    // Note: cin::read is potentially unsafe, consider  
    // using cin::_Read_s instead.  
    cin.read(&c[0], count);  
    c[count] = 0;  
  
    cout << c << endl;  
}  
```  
  
```Output  
  
abcde  
  
```  
  
```Output  
  
      abcdeType 'abcde': abcde  
abcde  
```  
  
##  <a name="readsome"></a>  basic_istream::readsome  
 读取指定数量的字符值。  
  
 此方法可能并不安全，因为它依赖于调用方检查所传递的值是否正确。  
  
```  
streamsize readsome(
    char_type* str,  
    streamsize count);
```  
  
### <a name="parameters"></a>参数  
 `str`  
 `readsome` 存储它所读取字符的数组。  
  
 `count`  
 要读取的字符数。  
  
### <a name="return-value"></a>返回值  
 实际读取的字符数 [gcount](#gcount)。  
  
### <a name="remarks"></a>备注  
 此未格式化的输入函数从输入流最多提取 `count` 个元素，并将它们存储在数组 `str` 中。  
  
 此函数不会等待输入。 它会读取任何可用的数据。  
  
### <a name="example"></a>示例  
  
```cpp  
// basic_istream_readsome.cpp  
// compile with: /EHsc /W3  
#include <iostream>  
using namespace std;  
  
int main( )  
{  
   char c[10];  
   int count = 5;  
  
   cout << "Type 'abcdefgh': ";  
  
   // cin.read blocks until user types input.  
   // Note: cin::read is potentially unsafe, consider  
   // using cin::_Read_s instead.  
   cin.read(&c[0], 2);  
  
   // Note: cin::readsome is potentially unsafe, consider  
   // using cin::_Readsome_s instead.  
   int n = cin.readsome(&c[0], count);  // C4996  
   c[n] = 0;  
   cout << n << " characters read" << endl;  
   cout << c << endl;  
}  
```  
  
##  <a name="seekg"></a>  basic_istream::seekg  
 在流中移动读取位置。  
  
```  
basic_istream<Elem, Tr>& seekg(pos_type pos);

basic_istream<Elem, Tr>& seekg(off_type off, ios_base::seekdir way);
```  
  
### <a name="parameters"></a>参数  
 `pos`  
 要将读取指针移动到的绝对位置。  
  
 `off`  
 相对于 `way`，移动读取指针的偏移量。  
  
 `way`  
 其中一个 [ios_base::seekdir](../standard-library/ios-base-class.md#seekdir) 枚举。  
  
### <a name="return-value"></a>返回值  
 流 ( **\*this**)。  
  
### <a name="remarks"></a>备注  
 第一个成员函数执行绝对查找，第二个成员函数执行相对查找。  
  
> [!NOTE]
>  不要对文本文件使用第二个成员函数，因为标准 C++ 不支持在文本文件中进行相对查找。  
  
 对于某些 **pos_type** 临时对象 **newpos** 来说，如果 [fail](../standard-library/basic-ios-class.md#fail) 为 false，则第一个成员函数调用 **newpos** = [rdbuf](../standard-library/basic-ios-class.md#rdbuf) -> [pubseekpos](../standard-library/basic-streambuf-class.md#pubseekpos)( `pos`)。 如果 **fail** 为 false，则第二个函数调用 **newpos** = **rdbuf** -> [pubseekoff](../standard-library/basic-streambuf-class.md#pubseekoff)( `off`, `way`)。 在任一情况下，如果 ( `off_type`) **newpos** == ( `off_type`)(-1)（定位操作失败），则函数调用 **istr**. [setstate](../standard-library/basic-ios-class.md#setstate)( **failbit**)。 两个函数均返回 **\*this**。  
  
 如果 [fail](../standard-library/basic-ios-class.md#fail) 为 true，则成员函数不执行任何操作。  
  
### <a name="example"></a>示例  
  
```cpp  
// basic_istream_seekg.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <fstream>  
  
int main ( )   
{  
   using namespace std;  
   ifstream file;  
   char c, c1;  
  
   file.open( "basic_istream_seekg.txt" );  
   file.seekg(2);   // seek to position 2  
   file >> c;  
   cout << c << endl;  
}  
```  
  
##  <a name="sentry"></a>  basic_istream::sentry  
 嵌套类描述一个对象，其声明构造了格式化和未格式化的输入函数。  
  
class sentry {  
   public:  
   explicit sentry( basic_istream\<Elem, Tr>& _Istr,  
   bool _Noskip = false); operator bool() const; };  
  
### <a name="remarks"></a>备注  
 如果 `_Istr.`[good](../standard-library/basic-ios-class.md#good) 为 true，则构造函数：  
  
-   调用 `_Istr`。 [tie](../standard-library/basic-ios-class.md#tie) -> [flush](../standard-library/basic-ostream-class.md#flush)，如果 `_Istr`. `tie` 不是空指针  
  
-   有效地调用 [ws](../standard-library/istream-functions.md#ws)( `_Istr`)，如果 `_Istr`. [flags](../standard-library/ios-base-class.md#flags)**&**[skipws](../standard-library/ios-functions.md#skipws) 为非零  
  
 经过任何此类准备工作之后，如果 `_Istr`. **good** 为 false，则构造函数调用 `_Istr`. [setstate](../standard-library/basic-ios-class.md#setstate)( **failbit**)。 不管怎样，构造函数将由 `_Istr`. **good** 返回的值存储在 **status** 中。 稍后对 **operator bool** 的调用可提供此存储值。  
  
##  <a name="swap"></a>  basic_istream::swap  
 交换两个 `basic_istream` 对象的内容。  
  
```  
void swap(basic_istream& right);
```  
  
### <a name="parameters"></a>参数  
 `right`  
 对 `basic_istream` 对象的左值引用。  
  
### <a name="remarks"></a>备注  
 此成员函数调用 [basic_ios::swap](../standard-library/basic-ios-class.md#swap)`(right)`。 它还会将提取计数与 `right` 的提取计数进行交换。  
  
##  <a name="sync"></a>  basic_istream::sync  
 将与流关联的输入设备与流的缓冲区进行同步。  
  
```  
int sync();
```  
  
### <a name="return-value"></a>返回值  
 如果 [rdbuf](../standard-library/basic-ios-class.md#rdbuf) 是空指针，则该函数将返回 -1。 否则，该函数调用 `rdbuf` -> [pubsync](../standard-library/basic-streambuf-class.md#pubsync). 如果返回 -1，则该函数将调用 [setstate](../standard-library/basic-ios-class.md#setstate)( **badbit**) 并返回 -1。 否则，该函数返回零。  
  
##  <a name="tellg"></a>  basic_istream::tellg  
 报告流中的当前读取位置。  
  
```  
pos_type tellg();
```  
  
### <a name="return-value"></a>返回值  
 流中的当前新位置。  
  
### <a name="remarks"></a>备注  
 如果 [fail](../standard-library/basic-ios-class.md#fail) 为 false，则成员函数返回 [rdbuf](../standard-library/basic-ios-class.md#rdbuf) -> [pubseekoff](../standard-library/basic-streambuf-class.md#pubseekoff)(0, `cur`, **in**)。 否则，将返回 `pos_type`(-1)。  
  
### <a name="example"></a>示例  
  
```cpp  
// basic_istream_tellg.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <fstream>  
  
int main()  
{  
    using namespace std;  
    ifstream file;  
    char c;  
    streamoff i;  
  
    file.open("basic_istream_tellg.txt");  
    i = file.tellg();  
    file >> c;  
    cout << c << " " << i << endl;  
  
    i = file.tellg();  
    file >> c;  
    cout << c << " " << i << endl;  
}  
```  
  
##  <a name="unget"></a>  basic_istream::unget  
 将最近读取的字符放回流中。  
  
```  
basic_istream<Elem, Tr>& unget();
```  
  
### <a name="return-value"></a>返回值  
 流 ( **\*this**)。  
  
### <a name="remarks"></a>备注  
 如果可以，[未格式化的输入的函数](../standard-library/basic-istream-class.md)放回流中的上一个元素，如同通过调用 `rdbuf` -> [sungetc](../standard-library/basic-streambuf-class.md#sungetc) 一样。 如果 [rdbuf](../standard-library/basic-ios-class.md#rdbuf) 是空指针，或者如果对 `sungetc` 的调用返回 **traits_type::**[eof](../standard-library/basic-ios-class.md#eof)，则函数调用 [setstate](../standard-library/basic-ios-class.md#setstate)( **badbit**)。 不管怎样，它均将返回 **\*this**。  
  
 有关 `unget` 可能的失败方式的详细信息，请参阅 [basic_streambuf::sungetc](../standard-library/basic-streambuf-class.md#sungetc)。  
  
### <a name="example"></a>示例  
  
```cpp  
// basic_istream_unget.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
int main( )   
{  
   char c[10], c2;  
  
   cout << "Type 'abc': ";  
   c2 = cin.get( );  
   cin.unget( );  
   cin.getline( &c[0], 9 );  
   cout << c << endl;  
}  
```  
  
```Output  
  
abc  
  
```  
  
```Output  
  
      abcType 'abc': abc  
abc  
```  
  
## <a name="see-also"></a>请参阅  
 [C++ 标准库中的线程安全性](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 编程](../standard-library/iostream-programming.md)   
 [iostreams 约定](../standard-library/iostreams-conventions.md)


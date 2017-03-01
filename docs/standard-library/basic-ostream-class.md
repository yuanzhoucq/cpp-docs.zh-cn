---
title: "basic_ostream 类 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std::basic_ostream
- std.basic_ostream
- ostream/std::basic_ostream
- basic_ostream
dev_langs:
- C++
helpviewer_keywords:
- basic_ostream class
ms.assetid: 5baadc65-b662-4fab-8c9f-94457c58cda1
caps.latest.revision: 24
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 73cde54e382bb04b82739239bd0f07142c5b3321
ms.lasthandoff: 02/24/2017

---
# <a name="basicostream-class"></a>basic_ostream 类
此模板类描述一个控制将元素和编码对象插入流缓冲区的对象（其字符特征由类 **Tr** 确定，也称为 [traits_type](../standard-library/basic-ios-class.md#basic_ios__traits_type)），该流缓冲区具有 **Elem** 类型的元素（也称为 [char_type](../standard-library/basic-ios-class.md#basic_ios__char_type)）。  
  
## <a name="syntax"></a>语法  
  
```  
template <class Elem, class Tr = char_traits<Elem>>  
class basic_ostream : virtual public basic_ios<Elem, Tr>  
```  
  
#### <a name="parameters"></a>参数  
 `Elem`  
 `char_type`。  
  
 `Tr`  
 字符 `traits_type`。  
  
## <a name="remarks"></a>备注  
 重载 [operator<<](#basic_ostream__operator_lt__lt_) 的大部分成员函数是格式化的输出函数。 它们遵循以下模式：  
  
```  
iostate state = goodbit;  
const sentry ok(*this);

if (ok)  
 {try  
 {<convert and insert elements  
    accumulate flags in state> }  
    catch (...)  
 {try  
 {setstate(badbit);

}  
    catch (...)  
 {}  
    if ((exceptions()& badbit) != 0)  
    throw; }}  
width(0);
// Except for operator<<(Elem)  
setstate(state);

return (*this);
```  
  
 两个其他成员函数是未格式化的输出函数。 它们遵循以下模式：  
  
```  
iostate state = goodbit;  
const sentry ok(*this);

if (!ok)  
    state |= badbit;  
else  
 {try  
 {<obtain and insert elements  
    accumulate flags in state> }  
    catch (...)  
 {try  
 {setstate(badbit);

}  
    catch (...)  
 {}  
    if ((exceptions()& badbit) != 0)  
    throw; }}  
setstate(state);

return (*this);
```  
  
 如果它们在插入元素时遭遇失败，两组函数都会调用 [setstate](../standard-library/basic-ios-class.md#basic_ios__setstate)**(badbit)**。  
  
 类 basic_istream\< **Elem**, **Tr**> 的对象仅存储类 [basic_ios](../standard-library/basic-ios-class.md)**\<Elem**, **Tr>** 的虚拟公共基对象。  
  
## <a name="example"></a>示例  
 请参阅 [basic_ofstream 类](../standard-library/basic-ofstream-class.md)的示例，了解有关输出流的详细信息。  
  
### <a name="constructors"></a>构造函数  
  
|||  
|-|-|  
|[basic_ostream](#basic_ostream__basic_ostream)|构造 `basic_ostream` 对象。|  
  
### <a name="member-functions"></a>成员函数  
  
|||  
|-|-|  
|[flush](#basic_ostream__flush)|刷新缓冲区。|  
|[put](#basic_ostream__put)|将字符放入流中。|  
|[seekp](#basic_ostream__seekp)|重置在输出流中的位置。|  
|[sentry](#basic_ostream__sentry)|嵌套的类描述一个对象，该对象的声明构造格式化的输出函数和未格式化的输出函数。|  
|[swap](#basic_ostream__operator_eq)|将此 `basic_ostream` 对象的值与提供的 `basic_ostream` 对象的值进行交换。|  
|[tellp](#basic_ostream__tellp)|报告在输出流中的位置。|  
|[write](#basic_ostream__write)|将字符放入流中。|  
  
### <a name="operators"></a>运算符  
  
|||  
|-|-|  
|[operator=](#basic_ostream_operator_eq)|将提供的 `basic_ostream` 对象参数的值赋给此对象。|  
|[operator<<](#basic_ostream_operator_lt_lt_)|写入流。|  

## <a name="requirements"></a>要求  
 **标头：**\<ostream>  
  
 **命名空间：** std  
  
##  <a name="a-namebasicostreambasicostreama--basicostreambasicostream"></a><a name="basic_ostream__basic_ostream"></a>  basic_ostream::basic_ostream  
 构造 `basic_ostream` 对象。  
  
```  
explicit basic_ostream(
    basic_streambuf<Elem, Tr>* strbuf,  
    bool _Isstd = false);

basic_ostream(basic_ostream&& right);
```  
  
### <a name="parameters"></a>参数  
 ` strbuf`  
 类型 [basic_streambuf](../standard-library/basic-streambuf-class.md) 的对象。  
  
 `_Isstd`  
如果这是一个标准流，则为  `true`，否则为 `false`。  
  
 ` right`  
 对 `basic_ostream` 类型的对象的右值引用。  
  
### <a name="remarks"></a>备注  
 第一个构造函数通过调用 [init](../standard-library/basic-ios-class.md#basic_ios__init)(` strbuf`) 初始化基类。 第二个构造函数通过调用 [basic_ios::move](../standard-library/basic-ios-class.md#basic_ios__move)`(`` right``)` 初始化基类。  
  
### <a name="example"></a>示例  
  请参阅 [basic_ofstream::basic_ofstream](../standard-library/basic-ofstream-class.md#basic_ofstream__basic_ofstream) 的示例，了解有关输出流的详细信息。  
  
##  <a name="a-namebasicostreamflusha--basicostreamflush"></a><a name="basic_ostream__flush"></a>  basic_ostream::flush  
 刷新缓冲区。  
  
```  
basic_ostream<Elem, Tr>& flush();
```  
  
### <a name="return-value"></a>返回值  
 对 Basic_ostream 对象的引用。  
  
### <a name="remarks"></a>备注  
 如果 [rdbuf](../standard-library/basic-ios-class.md#basic_ios__rdbuf) 不是空指针，则函数将调用 **rdbuf->**[pubsync](../standard-library/basic-streambuf-class.md#basic_streambuf__pubsync)。 如果返回 -1，则该函数将调用 [setstate](../standard-library/basic-ios-class.md#basic_ios__setstate)(**badbit**)。 它将返回 **\*this**。  
  
### <a name="example"></a>示例  
  
```cpp  
// basic_ostream_flush.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   cout << "test";  
   cout.flush();  
}  
```  
  
```Output  
test  
```  
  
##  <a name="a-namebasicostreamoperatorltlta--basicostreamoperatorltlt"></a><a name="basic_ostream_operator_lt_lt_"></a>basic_ostream::operator&lt;&lt;  
 写入流。  
  
```  
basic_ostream<Elem, Tr>& operator<<(
    basic_ostream<Elem, Tr>& (* Pfn)(basic_ostream<Elem, Tr>&));

basic_ostream<Elem, Tr>& operator<<(
    ios_base& (* Pfn)(ios_base&));

basic_ostream<Elem, Tr>& operator<<(
    basic_ios<Elem, Tr>& (* Pfn)(basic_ios<Elem, Tr>&));

basic_ostream<Elem, Tr>& operator<<(basic_streambuf<Elem, Tr>* strbuf);
basic_ostream<Elem, Tr>& operator<<(bool val);
basic_ostream<Elem, Tr>& operator<<(short val);
basic_ostream<Elem, Tr>& operator<<(unsigned short val);
basic_ostream<Elem, Tr>& operator<<(int __w64  val);
basic_ostream<Elem, Tr>& operator<<(unsigned int __w64  val);
basic_ostream<Elem, Tr>& operator<<(long val);
basic_ostream<Elem, Tr>& operator<<(unsigned long __w64  val);
basic_ostream<Elem, Tr>& operator<<(long long val);
basic_ostream<Elem, Tr>& operator<<(unsigned long long val);
basic_ostream<Elem, Tr>& operator<<(float val);
basic_ostream<Elem, Tr>& operator<<(double val);
basic_ostream<Elem, Tr>& operator<<(long double val);
basic_ostream<Elem, Tr>& operator<<(const void* val);
```  
  
### <a name="parameters"></a>参数  
 `Pfn`  
 函数指针。  
  
 ` strbuf`  
 指向 **stream_buf** 对象的指针。  
  
 ` val`  
 要写入到流的元素。  
  
### <a name="return-value"></a>返回值  
 对 Basic_ostream 对象的引用。  
  
### <a name="remarks"></a>备注  
 `<ostream>` 标头还定义多个全局插入运算符。 有关详细信息，请参阅 [operator<< (\<ostream>)](../standard-library/ostream-operators.md#operator_lt__lt_)。  
  
 第一个成员函数确保 **ostr << endl** 形式的表达式调用 [endl](../standard-library/ostream-functions.md#endl)**(ostr)**，然后返回 **\*this**。 第二个和第三个函数确保其他操控器（如 [hex ](../standard-library/ios-functions.md#hex)）表现相似。 其余函数均是格式化的输出函数。  
  
 函数  
  
```  
basic_ostream<Elem, Tr>& operator<<(basic_streambuf<Elem, Tr>* strbuf);
```  
  
 如果 ` strbuf` 不是空指针，则该函数从 ` strbuf` 提取元素，并将其插入。 提取会在文件结尾停止，或者如果提取引发异常（为重新引发的异常），则提取也会停止。 如果插入失败，则也会在尚未提取所讨论元素的情况下导致提取停止。 如果该函数没有插入任何元素，或者如果提取引发异常，则函数调用 [setstate](../standard-library/basic-ios-class.md#basic_ios__setstate)(**failbit**)。 不管怎样，该函数均将返回 **\*this**。  
  
 函数  
  
```  
basic_ostream<Elem, Tr>& operator<<(bool val);
```  
  
 将 _`Val` 转换为布尔字段，并通过调用 [use_facet](../standard-library/basic-filebuf-class.md#basic_filebuf__open)**<num_put\<Elem, OutIt>**`(`[getloc](../standard-library/ios-base-class.md#ios_base__getloc)). [put](#basic_ostream__put)(**OutIt**([rdbuf](../standard-library/basic-ios-class.md#basic_ios__rdbuf)), **\*this**, `getloc`, **val**) 插入它。 此处，将 **OutIt** 定义为 [ostreambuf_iterator](../standard-library/ostreambuf-iterator-class.md)**\<Elem, Tr>**。 该函数返回 **\*this**。  
  
 函数  
  
```  
basic_ostream<Elem, Tr>& operator<<(short val);
basic_ostream<Elem, Tr>& operator<<(unsigned short val);
basic_ostream<Elem, Tr>& operator<<(int val);
basic_ostream<Elem, Tr>& operator<<(unsigned int __w64  val);
basic_ostream<Elem, Tr>& operator<<(long val);
basic_ostream<Elem, Tr>& operator<<(unsigned long val);
basic_ostream<Elem, Tr>& operator<<(long long val);
basic_ostream<Elem, Tr>& operator<<(unsigned long long val);
basic_ostream<Elem, Tr>& operator<<(const void* val);
```  
  
 每个函数将 ` val` 转换为数字字段，并通过调用 **use_facet<num_put\<Elem, OutIt>**(`getloc`). **put**(**OutIt**(`rdbuf`), **\*this**, `getloc`, **val**) 插入它。 此处，将 **OutIt** 定义为 **ostreambuf_iterator\<Elem, Tr>**。 该函数返回 **\*this**。  
  
 函数  
  
```  
basic_ostream<Elem, Tr>& operator<<(float val);
basic_ostream<Elem, Tr>& operator<<(double val);
basic_ostream<Elem, Tr>& operator<<(long double val);
```  
  
 每个函数将 `val` 转换为数字字段，并通过调用 **use_facet<num_put\<Elem, OutIt>**(`getloc`)**. put**(**OutIt**(`rdbuf`), **\*this**, `getloc`, **val**) 插入它。 此处，将 **OutIt** 定义为 **ostreambuf_iterator\<Elem, Tr>**。 该函数返回 **\*this**。  
  
### <a name="example"></a>示例  
  
```cpp  
// basic_ostream_op_write.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <string.h>  
  
using namespace std;  
  
ios_base& hex2( ios_base& ib )  
{  
   ib.unsetf( ios_base::dec );  
   ib.setf( ios_base::hex );  
   return ib;  
}  
  
basic_ostream<char, char_traits<char> >& somefunc(basic_ostream<char, char_traits<char> > &i)
{
    if (i == cout)
    {
        i << "i is cout" << endl;
    }
    return i;
}

class CTxtStreambuf : public basic_streambuf< char, char_traits< char > >
{
public:
    CTxtStreambuf(char *_pszText)
    {
        pszText = _pszText;
        setg(pszText, pszText, pszText + strlen(pszText));
    };
    char *pszText;
};

int main()
{
    cout << somefunc;
    cout << 21 << endl;

    hex2(cout);
    cout << 21 << endl;

    CTxtStreambuf f("text in streambuf");
    cout << &f << endl;
}
```  
  
##  <a name="a-namebasicostreamoperatoreqa--basicostreamoperator"></a><a name="basic_ostream__operator_eq"></a>  basic_ostream::operator=  
 将提供的 `basic_ostream` 对象参数的值赋给此对象。  
  
```  
basic_ostream& operator=(basic_ostream&& right);
```  
  
### <a name="parameters"></a>参数  
 ` right`  
 对 `basic_ostream` 对象的 `rvalue` 引用。  
  
### <a name="remarks"></a>备注  
 成员运算符调用 swap `(`` right``)`。  
  
##  <a name="a-namebasicostreamputa--basicostreamput"></a><a name="basic_ostream__put"></a>  basic_ostream::put  
 将字符放入流中。  
  
```  
basic_ostream<Elem, Tr>& put(char_type _Ch);
```  
  
### <a name="parameters"></a>参数  
 `_Ch`  
 一个字符。  
  
### <a name="return-value"></a>返回值  
 对 Basic_ostream 对象的引用。  
  
### <a name="remarks"></a>备注  
 未格式化的输出函数插入元素 `_Ch`。 它将返回 **\*this**。  
  
### <a name="example"></a>示例  
  
```cpp  
// basic_ostream_put.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   cout.put( 'v' );  
   cout << endl;  
   wcout.put( L'l' );  
}  
```  
  
```Output  
v  
l  
```  
  
##  <a name="a-namebasicostreamseekpa--basicostreamseekp"></a><a name="basic_ostream__seekp"></a>  basic_ostream::seekp  
 重置输出流中的位置。  
  
```  
basic_ostream<Elem, Tr>& seekp(pos_type _Pos);

basic_ostream<Elem, Tr>& seekp(off_type _Off, ios_base::seekdir _Way);
```  
  
### <a name="parameters"></a>参数  
 `_Pos`  
 流中的位置。  
  
 `_Off`  
 相对于 `_Way` 的偏移量。  
  
 `_Way`  
 其中一个 [ios_base::seekdir](../standard-library/ios-base-class.md#ios_base__seekdir) 枚举。  
  
### <a name="return-value"></a>返回值  
 对 Basic_ostream 对象的引用。  
  
### <a name="remarks"></a>备注  
 对于某些 `pos_type` 临时对象 **newpos**，如果 [fail](../standard-library/basic-ios-class.md#basic_ios__fail) 为 **false**，则第一个成员函数调用 **newpos =** [rdbuf](../standard-library/basic-ios-class.md#basic_ios__rdbuf)**->** [pubseekpos](../standard-library/basic-streambuf-class.md#basic_streambuf__pubseekpos)(_*Pos*)。 如果 **fail** 为 false，则第二个函数调用 **newpos = rdbuf->** [pubseekoff](../standard-library/basic-streambuf-class.md#basic_streambuf__pubseekoff)(*_Off, _Way*)。 在任一情况下，如果 (`off_type`)**newpos ==** (`off_type`)(-1)（定位操作失败），则函数调用 **istr.**[setstate](../standard-library/basic-ios-class.md#basic_ios__setstate)(**failbit**)。 两个函数均返回 **\*this**。  
  
### <a name="example"></a>示例  
  
```cpp  
// basic_ostream_seekp.cpp  
// compile with: /EHsc  
#include <fstream>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    ofstream x("basic_ostream_seekp.txt");  
    streamoff i = x.tellp();  
    cout << i << endl;  
    x << "testing";  
    i = x.tellp();  
    cout << i << endl;  
    x.seekp(2);   // Put char in third char position in file  
    x << " ";  
  
    x.seekp(2, ios::end);   // Put char two after end of file  
    x << "z";  
}  
```  
  
```Output  
0  
7  
```  
  
##  <a name="a-namebasicostreamsentrya--basicostreamsentry"></a><a name="basic_ostream__sentry"></a>  basic_ostream::sentry  
 嵌套的类描述一个对象，该对象的声明构造格式化的输出函数和未格式化的输出函数。  
  
class sentry {  
   public:  
   explicit sentry(basic_ostream\<Elem, Tr>& _Ostr); operator bool() const; ~sentry(); };  
  
### <a name="remarks"></a>备注  
 嵌套的类描述一个对象，该对象的声明构造格式化的输出函数和未格式化的输出函数。 如果 **ostr.**[good](../standard-library/basic-ios-class.md#basic_ios__good) 为 **true** 且 **ostr.**[tie](../standard-library/basic-ios-class.md#basic_ios__tie) 不是空指针，则构造函数调用 **ostr.tie->**[flush](#basic_ostream__flush)。 然后，构造函数将 **ostr.good** 返回的值存储在 **status** 中。 稍后对 **operator bool** 的调用可提供此存储值。  
  
 如果 `uncaught_exception` 返回 **false**并且 [flags](../standard-library/ios-base-class.md#ios_base__flags) **&** [unitbuf](../standard-library/ios-functions.md#unitbuf) 为非零，则析构函数调用 [flush](#basic_ostream__flush)。  
  
##  <a name="a-namebasicostreamswapa--basicostreamswap"></a><a name="basic_ostream__swap"></a>  basic_ostream::swap  
 将此 `basic_ostream` 对象的值与提供的 `basic_ostream` 的值进行交换。  
  
```  
void swap(basic_ostream& right);
```  
  
### <a name="parameters"></a>参数  
 ` right`  
 对 `basic_ostream` 对象的引用。  
  
### <a name="remarks"></a>备注  
 此成员函数调用 [basic_ios::swap](../standard-library/basic-ios-class.md#basic_ios__swap)`(`` right``)` 以将此对象的内容与 ` right` 的内容进行交换。  
  
##  <a name="a-namebasicostreamtellpa--basicostreamtellp"></a><a name="basic_ostream__tellp"></a>  basic_ostream::tellp  
 报告输出流中的位置。  
  
```  
pos_type tellp();
```  
  
### <a name="return-value"></a>返回值  
 输出流中的位置。  
  
### <a name="remarks"></a>备注  
 如果 [fail](../standard-library/basic-ios-class.md#basic_ios__fail) 为 **false**，则成员函数返回 [rdbuf](../standard-library/basic-ios-class.md#basic_ios__rdbuf)**->** [pubseekoff](../standard-library/basic-streambuf-class.md#basic_streambuf__pubseekoff)(0, `cur`, **in**)。 否则，将返回 `pos_type`(-1)。  
  
### <a name="example"></a>示例  
  有关使用 `tellp` 的示例，请参阅 [seekp](#basic_ostream__seekp)。  
  
##  <a name="a-namebasicostreamwritea--basicostreamwrite"></a><a name="basic_ostream__write"></a>  basic_ostream::write  
 将字符放入流中。  
  
```  
basic_ostream<Elem, Tr>& write(const char_type* str, streamsize count);
```  
  
### <a name="parameters"></a>参数  
 ` count`  
 要放入流中的字符计数。  
  
 ` str`  
 要放入流中的字符。  
  
### <a name="return-value"></a>返回值  
 对 Basic_ostream 对象的引用。  
  
### <a name="remarks"></a>备注  
 [未格式化的输出函数](../standard-library/basic-ostream-class.md)插入从 ` str` 开始的 ` count` 元素的序列。  
  
### <a name="example"></a>示例  
  有关使用 `write` 的示例，请参阅 [streamsize](../standard-library/ios-typedefs.md#streamsize)。  
  
## <a name="see-also"></a>另请参阅  
 [C++ 标准库中的线程安全性](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 编程](../standard-library/iostream-programming.md)   
 [iostreams 约定](../standard-library/iostreams-conventions.md)



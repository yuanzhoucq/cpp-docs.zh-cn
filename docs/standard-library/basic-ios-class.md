---
title: "basic_ios 类 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std.basic_ios
- ios/std::basic_ios
- basic_ios
- std::basic_ios
dev_langs:
- C++
helpviewer_keywords:
- basic_ios class
ms.assetid: 4fdcd8e1-62d2-4611-8a70-1e4f58434007
caps.latest.revision: 24
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
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 6987d9c75785ebb716324395e0ce295d4155e55f
ms.lasthandoff: 02/24/2017

---
# <a name="basicios-class"></a>basic_ios 类
此模板类描述了依赖于模板参数的输入流（属于模板类 [basic_istream](../standard-library/basic-istream-class.md)）和输出流（属于模板类 [basic_ostream](../standard-library/basic-ostream-class.md)）通用的存储和成员函数。 （[ios_base](../standard-library/ios-base-class.md) 类描述不依赖于模板参数的通用内容。）**basic_ios\<class Elem, class Traits>** 类的对象帮助控制具有 **Elem** 类型元素的流，其字符特征由 **Traits** 类确定。  
  
## <a name="syntax"></a>语法  
  
```  
 
template <class Elem, class Traits>  
class basic_ios : public ios_base  
```  
  
#### <a name="parameters"></a>参数  
 `Elem`  
 一种类型。  
  
 `Traits`  
 `char_traits` 类型的变量。  
  
## <a name="remarks"></a>备注  
 **basic_ios\<class Elem, class Traits>** 类的对象存储：  
  
-   指向 [basic_istream](../standard-library/basic-istream-class.md)**\<Elem, Traits>** 类型的对象的绑定指针。  
  
-   指向 [basic_streambuf](../standard-library/basic-streambuf-class.md)**\<Elem, Traits >** 类型的对象的流缓冲区指针。  
  
- [格式设置信息](../standard-library/ios-base-class.md)。  
  
- [ios_base](../standard-library/ios-base-class.md) 类型的基对象中的[流状态信息](../standard-library/ios-base-class.md)。  
  
-   `char_type` 类型的对象中的填充字符。  
  
### <a name="constructors"></a>构造函数  
  
|||  
|-|-|  
|[basic_ios](#basic_ios__basic_ios)|构造 `basic_ios` 类。|  
  
### <a name="typedefs"></a>Typedef  
  
|||  
|-|-|  
|[char_type](#basic_ios__char_type)|模板参数 `Elem` 的同义词。|  
|[int_type](#basic_ios__int_type)|`Traits::int_type` 的同义词。|  
|[off_type](#basic_ios__off_type)|`Traits::off_type` 的同义词。|  
|[pos_type](#basic_ios__pos_type)|`Traits::pos_type` 的同义词。|  
|[traits_type](#basic_ios__traits_type)|模板参数 `Traits` 的同义词。|  
  
### <a name="member-functions"></a>成员函数  
  
|||  
|-|-|  
|[bad](#basic_ios__bad)|指示流缓冲区的完整性损失。|  
|[clear](#basic_ios__clear)|清除所有错误标志。|  
|[copyfmt](#basic_ios__copyfmt)|将标志从一个流复制到另一个流。|  
|[eof](#basic_ios__eof)|指示是否已到达流的结尾。|  
|[exceptions](#basic_ios__exceptions)|指示流将引发哪些异常。|  
|[fail](#basic_ios__fail)|指示从流中提取有效字段失败。|  
|[fill](#basic_ios__fill)|指定或返回在文本宽度小于流宽度时将使用的字符。|  
|[good](#basic_ios__good)|指示流处于良好状态。|  
|[imbue](#basic_ios__imbue)|更改区域设置。|  
|[init](#basic_ios__init)|通过 `basic_ios` 构造函数调用。|  
|[move](#basic_ios__move)|将所有值（指向流缓冲区的指针除外）从参数移动到当前对象。|  
|[narrow](#basic_ios__narrow)|查找给定 `char_type` 的等效字符型。|  
|[rdbuf](#basic_ios__rdbuf)|将流路由到指定缓冲区。|  
|[rdstate](#basic_ios__rdstate)|读取标志的位状态。|  
|[set_rdbuf](#basic_ios__set_rdbuf)|分配流缓冲区作为此流对象的读取缓冲区。|  
|[setstate](#basic_ios__setstate)|设置其他标志。|  
|[swap](#basic_ios__swap)|将此 `basic_ios` 对象中的值与另一个 `basic_ios` 对象中的值进行交换。 不会交换指向流缓冲区的指针。|  
|[tie](#basic_ios__tie)|确保依次处理流。|  
|[widen](#basic_ios__widen)|查找给定字符型的等效 `char_type`。|  
  
### <a name="operators"></a>运算符  
  
|||  
|-|-|  
|[explicit operator bool](#basic_ios__operator_bool)|允许将 `basic_ios` 对象作为作 `bool`。 禁用自动类型转换以防止产生常见的意外副作用。|  
|[operator void *](#basic_ios__operator_void_star)|指示流是否仍处于良好状态。|  
|[operator!](#basic_ios__operator_not)|指示流是否完好无损。|  
  
## <a name="requirements"></a>要求  
 **标头：**\<ios>  
  
 **命名空间：** std  
  
##  <a name="a-namebasiciosbada--basiciosbad"></a><a name="basic_ios__bad"></a>  basic_ios::bad  
 指示流缓冲区的完整性损失  
  
```  
bool bad() const;
```  
  
### <a name="return-value"></a>返回值  
 如果 `rdstate & badbit` 为非零，则为 `true`，否则为 `false`。  
  
 有关 `badbit` 的详细信息，请参阅 [ios_base::iostate](../standard-library/ios-base-class.md#ios_base__iostate)。  
  
### <a name="example"></a>示例  
  
```cpp  
// basic_ios_bad.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( void )  
{  
  using namespace std;  
  bool b = cout.bad( );  
  cout << boolalpha;  
  cout << b << endl;  
    
  b = cout.good( );  
  cout << b << endl;  
}  
  
```  
  
##  <a name="a-namebasiciosbasiciosa--basiciosbasicios"></a><a name="basic_ios__basic_ios"></a>  basic_ios::basic_ios  
 构造 basic_ios 类。  
  
```   
explicit basic_ios(basic_streambuf<Elem,  Traits>* sb);
basic_ios();
```  
  
### <a name="parameters"></a>参数  
 `sb`  
 用于存储输入或输出元素的标准缓冲区。  
  
### <a name="remarks"></a>备注  
 第一个构造函数通过调用 [init](#basic_ios__init)(_ *Sb*) 可初始化其成员对象。 第二个（受保护的）构造函数取消初始化其成员对象。 稍后对 **init** 的调用必须先初始化此对象，然后才可被安全销毁。  
  
##  <a name="a-namebasicioschartypea--basicioschartype"></a><a name="basic_ios__char_type"></a>  basic_ios::char_type  
 模板参数 **Elem** 的同义词。  
  
```   
typedef Elem char_type;  
```  
  
##  <a name="a-namebasicioscleara--basiciosclear"></a><a name="basic_ios__clear"></a>  basic_ios::clear  
 清除所有错误标志。  
  
```   
void clear(iostate state = goodbit, bool reraise = false); 
void clear(io_state state);
```  
  
### <a name="parameters"></a>参数  
 `state`（可选）  
 清除所有标志后你想要设置的标志。 默认为 `goodbit`。  
  
 `reraise`（可选）  
 指定是否应重新引发这个异常。 默认为 `false`（将不重新引发异常）。  
  
### <a name="remarks"></a>备注  
 标志为 **goodbit**、**failbit**、**eofbit** 和 **badbit**。 使用 [good](#basic_ios__good)、[bad](#basic_ios__bad)、[eof](#basic_ios__eof) 和 [fail](#basic_ios__fail) 测试这些标志  
  
 成员函数将存储的流状态信息替换为：  
  
 `state` &#124; `(`[rdbuf](#basic_ios__rdbuf) != 0 **goodbit** : **badbit**)  
  
 如果 `state`**&**[exceptions](#basic_ios__exceptions) 为非零，则它会抛出类 [failure](../standard-library/ios-base-class.md#ios_base__failure) 的一个对象。  
  
### <a name="example"></a>示例  
  请参阅 [rdstate](#basic_ios__rdstate) 和 [getline](../standard-library/string-functions.md#getline) 了解使用 **clear** 的示例。  
  
##  <a name="a-namebasicioscopyfmta--basicioscopyfmt"></a><a name="basic_ios__copyfmt"></a>  basic_ios::copyfmt  
 将标志从一个流复制到另一个流。  
  
```   
basic_ios<Elem, Traits>& copyfmt(
const basic_ios<Elem, Traits>& right);
```  
  
### <a name="parameters"></a>参数  
 ` right`  
 要复制其标志的流。  
  
### <a name="return-value"></a>返回值  
 正在向其复制标志的流的 **this** 对象。  
  
### <a name="remarks"></a>备注  
 成员函数将报告回调 eventÂ erase_event。 然后，它将填充字符、绑定指针和格式设置信息从 ` right` 复制到 **\*this**。 在更改异常掩码之前，它会报告回调事件 copyfmt_event。 复制完成后，如果 **state &**[exceptions](#basic_ios__exceptions) 为非零，则该函数将有效地调用带参数 [rdstate](#basic_ios__rdstate) 的 [clear](#basic_ios__clear)。 它将返回 **\*this**。  
  
### <a name="example"></a>示例  
  
```cpp    
// basic_ios_copyfmt.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <fstream>  
  
int main( )  
{  
  using namespace std;  
  ofstream x( "test.txt" );  
  int i = 10;  
    
  x << showpos;  
  cout << i << endl;  
  cout.copyfmt( x );  
  cout << i << endl;  
}  
  
```  
  
##  <a name="a-namebasicioseofa--basicioseof"></a><a name="basic_ios__eof"></a>  basic_ios::eof  
 指示是否已到达流的结尾。  
  
```  
bool eof() const;
```  
  
### <a name="return-value"></a>返回值  
 如果已到达流的结尾，则为 `true`，否则为 `false`。  
  
### <a name="remarks"></a>备注  
 如果 [rdstate](#basic_ios__rdstate) `& eofbit` 为非零，则成员函数将返回 `true`。 有关 `eofbit` 的详细信息，请参阅 [ios_base::iostate](../standard-library/ios-base-class.md#ios_base__iostate)。  
  
### <a name="example"></a>示例  
  
```cpp    
// basic_ios_eof.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <fstream>  
  
using namespace std;  
  
int main( int argc, char* argv[] )  
{  
  fstream   fs;  
  int n = 1;  
  fs.open( "basic_ios_eof.txt" );   // an empty file  
  cout << boolalpha  
  cout << fs.eof() << endl;  
  fs >> n;   // Read the char in the file  
  cout << fs.eof() << endl;  
}  
  
```  
  
##  <a name="a-namebasiciosexceptionsa--basiciosexceptions"></a><a name="basic_ios__exceptions"></a>  basic_ios::exceptions  
 指示流将引发哪些异常。  
  
```   
iostate exceptions() const; 
void exceptions(iostate Newexcept);
void exceptions(io_state Newexcept);
```  
  
### <a name="parameters"></a>参数  
 *Newexcept*  
 希望抛出异常的标志。  
  
### <a name="return-value"></a>返回值  
 当前指定的用于为流抛出异常的标志。  
  
### <a name="remarks"></a>备注  
 第一个成员函数返回存储的异常掩码。 第二个成员函数在异常掩码中存储 *_Except* 并返回其先前的存储值。 注意，存储新异常掩码会与调用 [clear](#basic_ios__clear)( [rdstate](#basic_ios__rdstate) ) 一样抛出异常。  
  
### <a name="example"></a>示例  
  
```cpp  
// basic_ios_exceptions.cpp  
// compile with: /EHsc /GR  
#include <iostream>  
  
int main( )  
{  
  using namespace std;  
    
  cout << cout.exceptions( ) << endl;  
  cout.exceptions( ios::eofbit );  
  cout << cout.exceptions( ) << endl;  
  try  
  {  
    cout.clear( ios::eofbit );   // Force eofbit on  
  }  
  catch ( exception &e )  
  {  
    cout.clear( );  
    cout << "Caught the exception." << endl;  
    cout << "Exception class: " << typeid(e).name()  << endl;  
    cout << "Exception description: " << e.what() << endl;  
  }  
}  
  
```  
  
```Output  
  
0  
1  
Caught the exception.  
Exception class: class std::ios_base::failure  
Exception description: ios_base::eofbit set   
```  
  
##  <a name="a-namebasiciosfaila--basiciosfail"></a><a name="basic_ios__fail"></a>  basic_ios::fail  
 指示从流中提取有效字段失败。  
  
```  
bool fail() const;
```  
  
### <a name="return-value"></a>返回值  
 如果 [rdstate](#basic_ios__rdstate) `& (badbit|failbit)` 为非零，则为 `true`，否则为 `false`。  
  
 有关 `failbit` 的详细信息，请参阅 [ios_base::iostate](../standard-library/ios-base-class.md#ios_base__iostate)。  
  
### <a name="example"></a>示例  
  
```cpp  
// basic_ios_fail.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( void )  
{  
  using namespace std;  
  bool b = cout.fail( );  
  cout << boolalpha;  
  cout << b << endl;  
}  
  
```  
  
##  <a name="a-namebasiciosfilla--basiciosfill"></a><a name="basic_ios__fill"></a>  basic_ios::fill  
 指定或返回在文本宽度小于流宽度时将使用的字符。  
  
```   
char_type fill() const; 
char_type fill(char_type Char);
```  
  
### <a name="parameters"></a>参数  
 `Char`  
 希望用作填充字符的字符。  
  
### <a name="return-value"></a>返回值  
 当前的填充字符。  
  
### <a name="remarks"></a>备注  
 第一个成员函数返回存储的填充字符。 第二个成员函数将 `Char` 存储在填充字符中，并返回其先前的存储值。  
  
### <a name="example"></a>示例  
  
```cpp  
// basic_ios_fill.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <iomanip>  
  
int main( )  
{  
  using namespace std;  
    
  cout << setw( 5 ) << 'a' << endl;     
  cout.fill( 'x' );  
  cout << setw( 5 ) << 'a' << endl;      
  cout << cout.fill( ) << endl;  
}  
  
```  
  
```Output  
  
a  
xxxxa  
x   
```  
  
##  <a name="a-namebasiciosgooda--basiciosgood"></a><a name="basic_ios__good"></a>  basic_ios::good  
 指示流处于良好状态。  
  
```  
bool good() const;
```  
  
### <a name="return-value"></a>返回值  
 如果 [rdstate](#basic_ios__rdstate) `== goodbit`（未设置任何状态标志），则为 `true`，否则为 `false`。  
  
 有关 `goodbit` 的详细信息，请参阅 [ios_base::iostate](../standard-library/ios-base-class.md#ios_base__iostate)。  
  
### <a name="example"></a>示例  
  请参阅 [basic_ios:: bad](#basic_ios__bad)，了解使用 `good` 的示例。  
  
##  <a name="a-namebasiciosimbuea--basiciosimbue"></a><a name="basic_ios__imbue"></a>  basic_ios::imbue  
 更改区域设置。  
  
```   
locale imbue(const locale& Loc);
```  
  
### <a name="parameters"></a>参数  
 `Loc`  
 区域设置字符串。  
  
### <a name="return-value"></a>返回值  
 先前的区域设置。  
  
### <a name="remarks"></a>备注  
 如果 [rdbuf](#basic_ios__rdbuf) 不是空指针，则成员函数将调用  
  
 `rdbuf`-> [pubimbue](../standard-library/basic-streambuf-class.md#basic_streambuf__pubimbue)(_ *Loc*)  
  
 不管怎样，它都将返回 [ios_base::imbue](../standard-library/ios-base-class.md#ios_base__imbue)(_ *Loc*)。  
  
### <a name="example"></a>示例  
  
```cpp  
// basic_ios_imbue.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <locale>  
  
int main( )  
{  
  using namespace std;  
    
  cout.imbue( locale( "french_france" ) );  
  double x = 1234567.123456;  
  cout << x << endl;  
}  
  
```  
  
##  <a name="a-namebasiciosinita--basiciosinit"></a><a name="basic_ios__init"></a>  basic_ios::init  
 由 basic_ios 构造函数调用。  
  
```  
 
void init(basic_streambuf<Elem,Traits>* _Sb, bool _Isstd = false);
```  
  
### <a name="parameters"></a>参数  
 `_Sb`  
 用于存储输入或输出元素的标准缓冲区。  
  
 `_Isstd`  
 指定这是否是一个标准流。  
  
### <a name="remarks"></a>备注  
 成员函数将值存储在所有成员对象中，因此：  
  
- [rdbuf](#basic_ios__rdbuf) 返回 *_Sb*。  
  
- [tie](#basic_ios__tie) 返回空指针。  
  
- 如果 `_Sb` 为非零，则 [rdstate](#basic_ios__rdstate) 返回 [goodbit](../standard-library/ios-base-class.md#ios_base__iostate)，否则将返回 [badbit](../standard-library/ios-base-class.md#ios_base__iostate)。  
  
- [exceptions](#basic_ios__exceptions) 返回 **goodbit**。  
  
- [flags](../standard-library/ios-base-class.md#ios_base__flags) 返回 [skipws](../standard-library/ios-base-class.md#ios_base__fmtflags) &#124; [dec](../standard-library/ios-base-class.md#ios_base__fmtflags)。  
  
- [width](../standard-library/ios-base-class.md#ios_base__width) 返回 0。  
  
- [precision](../standard-library/ios-base-class.md#ios_base__precision) 返回 6。  
  
- [fill](#basic_ios__fill) 返回空格字符。  
  
- [getloc](../standard-library/ios-base-class.md#ios_base__getloc) 返回 `locale::classic`。  
  
- [iword](../standard-library/ios-base-class.md#ios_base__iword) 返回零，[pword](../standard-library/ios-base-class.md#ios_base__pword) 返回针对所有参数值的空指针。  
  
##  <a name="a-namebasiciosinttypea--basiciosinttype"></a><a name="basic_ios__int_type"></a>  basic_ios::int_type  
 **traits_type::int_type** 的同义词。  
  
```  
typedef typename traits_type::int_type int_type;  
```  
  
##  <a name="a-namebasiciosmovea--basiciosmove"></a><a name="basic_ios__move"></a>  basic_ios::move  
 将所有值（指向流缓冲区的指针除外）从参数移动到当前对象。  
  
```   
void move(basic_ios&& right);
```  
  
### <a name="parameters"></a>参数  
 `right`  
 从中移动值的 `ios_base` 对象。  
  
### <a name="remarks"></a>备注  
 受保护成员函数将存储在 ` right` 中的所有值移动到 `*this`，存储的 `stream buffer pointer` 除外，它将保留在 ` right` 中不作更改并设置为 `*this` 中的空指针。 将存储的 `tie pointer` 设置为 ` right` 中的空指针。  
  
##  <a name="a-namebasiciosnarrowa--basiciosnarrow"></a><a name="basic_ios__narrow"></a>  basic_ios::narrow  
 查找给定 `char_type` 的等效字符型。  
  
```  
 
char narrow(char_type Char, char Default = '\0') const;
```  
  
### <a name="parameters"></a>参数  
 `Char`  
 要转换的 `char`。  
  
 `Default`  
 如果未找到等效字符，则返回希望返回的 `char`。  
  
### <a name="return-value"></a>返回值  
 给定 `char_type` 的等效 `char`。  
  
### <a name="remarks"></a>备注  
 成员函数返回 [use_facet](../standard-library/basic-filebuf-class.md#basic_filebuf__open)**<**Â **ctype**\< **E**> >( [getloc](../standard-library/ios-base-class.md#ios_base__getloc)( ) )。 `narrow`( `Char`, `Default`)。  
  
### <a name="example"></a>示例  
  
```cpp  
// basic_ios_narrow.cpp  
// compile with: /EHsc  
#include <ios>  
#include <iostream>  
#include <wchar.h>  
  
int main( )  
{  
  using namespace std;  
  wchar_t *x = L"test";  
  char y[10];  
  cout << x[0] << endl;  
  wcout << x << endl;  
  y[0] = wcout.narrow( x[0] );  
  cout << y[0] << endl;  
}  
  
```  
  
##  <a name="a-namebasiciosofftypea--basiciosofftype"></a><a name="basic_ios__off_type"></a>  basic_ios::off_type  
 **traits_type::off_type** 的同义词。  
  
```  
typedef typename traits_type::off_type off_type;  
```  
  
##  <a name="a-namebasiciosoperatorvoidstara--basiciosoperator-void-"></a><a name="basic_ios__operator_void_star"></a>  basic_ios::operator void *  
 指示流是否仍处于良好状态。  
  
```  
 operator void *() const;
```  
  
### <a name="return-value"></a>返回值  
 仅在 [fail](#basic_ios__fail) 时，该运算符才会返回空指针。  
  
### <a name="example"></a>示例  
  
```cpp  
// basic_ios_opgood.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )  
{  
  using namespace std;  
  cout << (bool)(&cout != 0) << endl;   // Stream is still good  
}  
  
```  
  
```Output  
1  
```  
  
##  <a name="a-namebasiciosoperatornota--basiciosoperator"></a><a name="basic_ios__operator_not"></a>  basic_ios::operator!  
 指示流是否完好无损。  
  
```   
bool operator!() const;
```  
  
### <a name="return-value"></a>返回值  
 返回 [fail](#basic_ios__fail)。  
  
### <a name="example"></a>示例  
  
```cpp  
// basic_ios_opbad.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )  
{  
  using namespace std;  
  cout << !cout << endl;   // Stream is not bad  
}  
  
```  
  
```Output  
0  
```  
  
##  <a name="a-namebasiciosoperatorboola--basiciosoperator-bool"></a><a name="basic_ios__operator_bool"></a>  basic_ios::operator bool  
 允许将 `basic_ios` 对象作为作 `bool`。 禁用自动类型转换以防止产生常见的意外副作用。  
  
```  
explicit operator bool() const;
```  
  
### <a name="remarks"></a>备注  
 仅在 `fail``()` 时，此运算符才返回可转换为 `false` 的值。 返回类型只能转换为 `bool`，而不能转换为 `void *` 或其他已知的标量类型。  
  
##  <a name="a-namebasiciospostypea--basiciospostype"></a><a name="basic_ios__pos_type"></a>  basic_ios::pos_type  
 **traits_type::pos_type** 的同义词。  
  
```  
typedef typename traits_type::pos_type pos_type;  
```  
  
##  <a name="a-namebasiciosrdbufa--basiciosrdbuf"></a><a name="basic_ios__rdbuf"></a>  basic_ios::rdbuf  
 将流路由到指定缓冲区。  
  
```   
basic_streambuf<Elem, Traits> *rdbuf() const; 
basic_streambuf<Elem, Traits> *rdbuf(
basic_streambuf<Elem, Traits>* _Sb);
```  
  
### <a name="parameters"></a>参数  
 `_Sb`  
 流。  
  
### <a name="remarks"></a>备注  
 第一个成员函数将返回存储的流缓冲区指针。  
  
 第二个成员函数在存储的流缓冲区指针中存储 `_Sb`，并返回以前存储的值。  
  
### <a name="example"></a>示例  
  
```cpp  
// basic_ios_rdbuf.cpp  
// compile with: /EHsc  
#include <ios>  
#include <iostream>  
#include <fstream>  
  
int main( )  
{  
  using namespace std;  
  ofstream file( "rdbuf.txt" );  
  streambuf *x = cout.rdbuf( file.rdbuf( ) );  
  cout << "test" << endl;   // Goes to file  
  cout.rdbuf(x);  
  cout << "test2" << endl;  
}  
  
```  
  
```Output  
test2  
```  
  
##  <a name="a-namebasiciosrdstatea--basiciosrdstate"></a><a name="basic_ios__rdstate"></a>  basic_ios::rdstate  
 读取标志的位状态。  
  
```  
 
iostate rdstate() const;
```  
  
### <a name="return-value"></a>返回值  
 存储的流状态信息。  
  
### <a name="example"></a>示例  
  
```cpp  
// basic_ios_rdstate.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <fstream>  
using namespace std;  
  
void TestFlags( ios& x )  
{  
  cout << ( x.rdstate( ) & ios::badbit ) << endl;  
  cout << ( x.rdstate( ) & ios::failbit ) << endl;  
  cout << ( x.rdstate( ) & ios::eofbit ) << endl;  
  cout << endl;  
}  
  
int main( )  
{  
  fstream x( "c:\test.txt", ios::out );  
  x.clear( );  
  TestFlags( x );  
  x.clear( ios::badbit | ios::failbit | ios::eofbit );  
  TestFlags( x );  
}  
  
```  
  
```Output  
  
0  
0  
0  
  
4  
2  
1   
```  
  
##  <a name="a-namebasiciossetstatea--basiciossetstate"></a><a name="basic_ios__setstate"></a>  basic_ios::setstate  
 设置其他标志。  
  
```   
void setstate(iostate _State);
```  
  
### <a name="parameters"></a>参数  
 `_State`  
 要设置的其他标志。  
  
### <a name="remarks"></a>备注  
 成员函数有效地调用 [clear](#basic_ios__clear)(_ *State* &#124; [rdstate](#basic_ios__rdstate))。  
  
### <a name="example"></a>示例  
  
```cpp    
// basic_ios_setstate.cpp  
// compile with: /EHsc  
#include <ios>  
#include <iostream>  
using namespace std;  
  
int main( )  
{  
  bool b = cout.bad( );  
  cout << b << endl;   // Good  
  cout.clear( ios::badbit );  
  b = cout.bad( );  
  // cout.clear( );  
  cout << b << endl;   // Is bad, good  
  b = cout.fail( );  
  cout << b << endl;   // Not failed  
  cout.setstate( ios::failbit );  
  b = cout.fail( );  
  cout.clear( );  
  cout << b << endl;   // Is failed, good  
  return 0;  
}  
  
```  
  
```Output  
  
0  
1   
```  
  
##  <a name="a-namebasiciossetrdbufa--basiciossetrdbuf"></a><a name="basic_ios__set_rdbuf"></a>  basic_ios::set_rdbuf  
 分配流缓冲区作为此流对象的读取缓冲区。  
  
```   
void set_rdbuf(
basic_streambuf<Elem, Tr>* strbuf)  
```  
  
### <a name="parameters"></a>参数  
 ` strbuf`  
 要成为读取缓冲区的流缓冲区。  
  
### <a name="remarks"></a>备注  
 受保护的成员函数在 `stream buffer pointer` 中存储 ` strbuf`。它未调用 `clear`。  
  
##  <a name="a-namebasiciostiea--basiciostie"></a><a name="basic_ios__tie"></a>  basic_ios::tie  
 确保依次处理流。  
  
```  
 
basic_ostream<Elem, Traits> *tie() const; 
basic_ostream<Elem, Traits> *tie(
basic_ostream<Elem, Traits>* str);
```  
  
### <a name="parameters"></a>参数  
 ` str`  
 一个流。  
  
### <a name="return-value"></a>返回值  
 第一个成员函数返回存储的绑定指针。 第二个成员函数将 ` str` 存储在绑定指针中，并返回其先前的存储值。  
  
### <a name="remarks"></a>备注  
 `tie` 导致两个流同步，使得一个流上的操作在另一个流上的操作完成之后发生。  
  
### <a name="example"></a>示例  
  在此例中，通过将 cin 绑定到 cout，可保证“输入数字:”字符串在该数字本身从 cin 提取之前进入控制台。 这消除了当读取相应数字时，“输入数字:”字符串仍在缓冲区中的可能性，使得我们确定用户实际上会得到一些提示来进行响应。 默认情况下，cin 和 cout 绑定在一起。  
  
```  
  
#include <ios>  
#include <iostream>  
  
int main( )  
{  
  using namespace std;  
  int i;  
  cin.tie( &cout );  
  cout << "Enter a number:";  
  cin >> i;  
}  
  
```  
  
##  <a name="a-namebasiciostraitstypea--basiciostraitstype"></a><a name="basic_ios__traits_type"></a>  basic_ios::traits_type  
 模板参数 **Traits** 的同义词。  
  
```   
typedef Traits traits_type;  
```  
  
##  <a name="a-namebasicioswidena--basicioswiden"></a><a name="basic_ios__widen"></a>  basic_ios::widen  
 查找给定 `char` 的等效 `char_type`。  
  
```   
char_type widen(char Char) const;
```  
  
### <a name="parameters"></a>参数  
 `Char`  
 要转换的字符。  
  
### <a name="return-value"></a>返回值  
 查找给定 `char` 的等效 `char_type`。  
  
### <a name="remarks"></a>备注  
 成员函数返回 [use_facet](../standard-library/basic-filebuf-class.md#basic_filebuf__open)< **ctype**\< **E**> >( [getloc](../standard-library/ios-base-class.md#ios_base__getloc)). `widen`( `Char`).  
  
### <a name="example"></a>示例  
  
```cpp    
// basic_ios_widen.cpp  
// compile with: /EHsc  
#include <ios>  
#include <iostream>  
#include <wchar.h>  
  
int main( )  
{  
  using namespace std;  
  char *z = "Hello";  
  wchar_t y[2] = {0,0};  
  cout << z[0] << endl;  
  y[0] = wcout.widen( z[0] );  
  wcout << &y[0] << endl;  
}  
  
```  
  
##  <a name="a-namebasiciosswapa--basiciosswap"></a><a name="basic_ios__swap"></a>  basic_ios::swap  
 将此 `basic_ios` 对象中的值与另一个 `basic_ios` 对象中的值进行交换。 但是，不会交换指向流缓冲区的指针。  
  
```   
void swap(basic_ios&& right);
```  
  
### <a name="parameters"></a>参数  
 `right`  
 用于交换值的 `basic_ios` 对象。  
  
### <a name="remarks"></a>备注  
 受保护的成员函数交换存储在 ` right` 与 `*this` 中的所有值，存储在 `stream buffer pointer` 中的值除外。  
  
## <a name="see-also"></a>另请参阅  
 [C++ 标准库中的线程安全性](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 编程](../standard-library/iostream-programming.md)   
 [iostreams 约定](../standard-library/iostreams-conventions.md)



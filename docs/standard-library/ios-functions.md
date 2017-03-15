---
title: "&lt;ios&gt; 函数 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1382d53f-e531-4b41-adf6-6a1543512e51
caps.latest.revision: 10
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 91e10200576389edcaff55860da3a8a701e75bab
ms.lasthandoff: 02/24/2017

---
# <a name="ltiosgt-functions"></a>&lt;ios&gt; 函数
||||  
|-|-|-|  
|[defaultfloat](#ios_defaultfloat)|[boolalpha](#boolalpha)|[dec](#dec)|  
|[fixed](#fixed)|[hex](#hex)|[内部](#internal)|  
|[left](#left)|[noboolalpha](#noboolalpha)|[noshowbase](#noshowbase)|  
|[noshowpoint](#noshowpoint)|[noshowpos](#noshowpos)|[noskipws](#noskipws)|  
|[nounitbuf](#nounitbuf)|[nouppercase](#nouppercase)|[oct](#oct)|  
|[right](#right)|[scientific](#scientific)|[showbase](#showbase)|  
|[showpoint](#showpoint)|[showpos](#showpos)|[skipws](#skipws)|  
|[unitbuf](#unitbuf)|[uppercase](#uppercase)|  
  
##  <a name="a-nameboolalphaa--boolalpha"></a><a name="boolalpha"></a>  boolalpha  
 指定类型为 [bool](../cpp/bool-cpp.md) 的变量在流中显示为 **true** 或 **false**。  
  
```  
ios_base& boolalpha(ios_base& str);
```  
  
### <a name="parameters"></a>参数  
 ` str`  
 对 [ios_base](../standard-library/ios-base-class.md) 类型的对象的引用，或对从 `ios_base` 继承的类型的引用。  
  
### <a name="return-value"></a>返回值  
 对 _ *Str* 派生所源自的对象的引用。  
  
### <a name="remarks"></a>备注  
 默认情况下，`bool` 类型的变量显示为 1 或 0。  
  
 `boolalpha` 有效调用 ` str.`[setf](../standard-library/ios-base-class.md#ios_base__setf)( `ios_base::boolalpha`)，然后返回 ` str.`  
  
 [noboolalpha](../standard-library/ios-functions.md#noboolalpha) 会取消 `boolalpha` 的效果。  
  
### <a name="example"></a>示例  
  
```cpp  
// ios_boolalpha.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   bool b = true;  
   cout << b << endl;  
   boolalpha( cout );  
   cout << b << endl;  
   noboolalpha( cout );  
   cout << b << endl;  
   cout << boolalpha << b << endl;  
}  
```  
  
```Output  
1  
true  
1  
true  
```  
  
##  <a name="a-namedeca--dec"></a><a name="dec"></a>dec  
 指定以十进制计数法形式显示整数变量。  
  
```  
ios_base& dec(ios_base& str);
```  
  
### <a name="parameters"></a>参数  
 ` str`  
 对 [ios_base](../standard-library/ios-base-class.md) 类型的对象的引用，或对从 `ios_base` 继承的类型的引用。  
  
### <a name="return-value"></a>返回值  
 对 _ *Str* 派生所源自的对象的引用。  
  
### <a name="remarks"></a>备注  
 默认情况下，整型变量以十进制计数法显示。  
  
 **dec** 有效调用 ` str``.`[setf](../standard-library/ios-base-class.md#ios_base__setf)( `ios_base::dec`**, ios_base::basefield**)，然后返回 ` str`。  
  
### <a name="example"></a>示例  
  
```cpp  
// ios_dec.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   int i = 100;  
  
   cout << i << endl;   // Default is base 10  
   cout << hex << i << endl;     
   dec( cout );  
   cout << i << endl;  
   oct( cout );  
   cout << i << endl;  
   cout << dec << i << endl;  
}  
```  
  
```Output  
100  
64  
100  
144  
100  
```  
  
##  <a name="a-nameiosdefaultfloata--ltiosgt-defaultfloat"></a><a name="ios_defaultfloat"></a>&lt;ios&gt; defaultfloat  
 配置 `ios_base` 对象的标记以使用浮点值的默认显示格式。  
  
```  
ios_base& defaultfloat(ios_base& _Iosbase);
```  
  
### <a name="parameters"></a>参数  
 `_Iosbase`  
 一个 `ios_base` 对象。  
  
### <a name="remarks"></a>备注  
 此操控器会有效调用 _I `osbase.`[ios_base::unsetf](../standard-library/ios-base-class.md#ios_base__unsetf)`(ios_base::floatfield)`，然后返回 _I `osbase`。  
  
##  <a name="a-namefixeda--fixed"></a><a name="fixed"></a>fixed  
 指定浮点数以自动设置小数点表示法显示。  
  
```  
ios_base& fixed(ios_base& str);
```  
  
### <a name="parameters"></a>参数  
 ` str`  
 对 [ios_base](../standard-library/ios-base-class.md) 类型的对象的引用，或对从 `ios_base` 继承的类型的引用。  
  
### <a name="return-value"></a>返回值  
 对 _ *Str* 派生所源自的对象的引用。  
  
### <a name="remarks"></a>备注  
 **fixed** 是浮点数的默认显示表示法。 [scientific](../standard-library/ios-functions.md#scientific) 会导致使用科学记数法显示浮点数。  
  
 此操控器有效调用 * str.*[setf](../standard-library/ios-base-class.md#ios_base__setf)( `ios_base::fixed`, **ios_base::floatfield**)，然后返回 ` str`。  
  
### <a name="example"></a>示例  
  
```cpp  
// ios_fixed.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   float i = 1.1F;  
  
   cout << i << endl;   // fixed is the default  
   cout << scientific << i << endl;  
   cout.precision( 1 );  
   cout << fixed << i << endl;  
}  
```  
  
```Output  
1.1  
1.100000e+000  
1.1  
```  
  
##  <a name="a-namehexa--hex"></a><a name="hex"></a>hex  
 指定以十六进制计数法形式显示整型变量。  
  
```  
ios_base& hex(ios_base& str);
```  
  
### <a name="parameters"></a>参数  
 ` str`  
 对 [ios_base](../standard-library/ios-base-class.md) 类型的对象的引用，或对从 `ios_base` 继承的类型的引用。  
  
### <a name="return-value"></a>返回值  
 对 _ *Str* 派生所源自的对象的引用。  
  
### <a name="remarks"></a>备注  
 默认情况下，整型变量以十进制计数法显示。 [dec](../standard-library/ios-functions.md#dec) 和 [oct](../standard-library/ios-functions.md#oct) 也会改变整型变量显示的方式。  
  
 此操控器有效调用 ` str`**.**[setf](../standard-library/ios-base-class.md#ios_base__setf)( `ios_base::hex`, **ios_base::basefield**)，然后返回 ` str`。  
  
### <a name="example"></a>示例  
  有关如何使用 **hex** 的示例，请参阅 [dec](../standard-library/ios-functions.md#dec)。  
  
##  <a name="a-nameinternala--internal"></a><a name="internal"></a>internal  
 导致数字的符号左对齐，数字右对齐。  
  
```  
ios_base& internal(ios_base& str);
```  
  
### <a name="parameters"></a>参数  
 ` str`  
 对 [ios_base](../standard-library/ios-base-class.md) 类型的对象的引用，或对从 `ios_base` 继承的类型的引用。  
  
### <a name="return-value"></a>返回值  
 对 ` str` 派生所源自的对象的引用。  
  
### <a name="remarks"></a>备注  
 [showpos](../standard-library/ios-functions.md#showpos) 会对正数显示此符号。  
  
 此操控器有效调用 ` str`. [setf](../standard-library/ios-base-class.md#ios_base__setf)( [ios_base::internal](../standard-library/ios-base-class.md#ios_base__fmtflags), [ios_base::adjustfield](../standard-library/ios-base-class.md#ios_base__fmtflags))，然后返回 ` str`。  
  
### <a name="example"></a>示例  
  
```cpp  
// ios_internal.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <iomanip>  
  
int main( void )   
{  
   using namespace std;  
   float i = -123.456F;  
   cout.fill( '.' );  
   cout << setw( 10 ) << i << endl;  
   cout << setw( 10 ) << internal << i << endl;  
}  
```  
  
```Output  
..-123.456  
-..123.456  
```  
  
##  <a name="a-namelefta--left"></a><a name="left"></a>left  
 导致宽度比输出宽度短的文本在流刷新过程中显示时带有左边距。  
  
```  
ios_base& left(ios_base& str);
```  
  
### <a name="parameters"></a>参数  
 ` str`  
 对 [ios_base](../standard-library/ios-base-class.md) 类型的对象的引用，或对从 `ios_base` 继承的类型的引用。  
  
### <a name="return-value"></a>返回值  
 对 _ *Str* 派生所源自的对象的引用。  
  
### <a name="remarks"></a>备注  
 此操控器有效调用 ` str.`[setf](../standard-library/ios-base-class.md#ios_base__setf)( `ios_base::left`, **ios_base::adjustfield**)，然后返回 ` str`。  
  
### <a name="example"></a>示例  
  
```cpp  
// ios_left.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   double f1= 5.00;  
   cout.width( 20 );   
   cout << f1 << endl;  
   cout << left << f1 << endl;  
}  
```  
  
```Output  
                   5  
5  
```  
  
##  <a name="a-namenoboolalphaa--noboolalpha"></a><a name="noboolalpha"></a>noboolalpha  
 指定类型为 [bool](../cpp/bool-cpp.md) 的变量在流中显示为 1 或 0。  
  
```  
ios_base& noboolalpha(ios_base& str);
```  
  
### <a name="parameters"></a>参数  
 ` str`  
 对 [ios_base](../standard-library/ios-base-class.md) 类型的对象的引用，或对从 `ios_base` 继承的类型的引用。  
  
### <a name="return-value"></a>返回值  
 对 _ *Str* 派生所源自的对象的引用。  
  
### <a name="remarks"></a>备注  
 默认情况，`noboolalpha` 是有效的。  
  
 `noboolalpha` 有效调用 ` str.`[unsetf](../standard-library/ios-base-class.md#ios_base__unsetf)( `ios_base::boolalpha`)，然后返回 ` str`。  
  
 [boolalpha](../standard-library/ios-functions.md#boolalpha) 会取消 `noboolalpha` 的效果。  
  
### <a name="example"></a>示例  
  有关使用 `noboolalpha` 的示例，请参阅 [boolalpha](../standard-library/ios-functions.md#boolalpha)。  
  
##  <a name="a-namenoshowbasea--noshowbase"></a><a name="noshowbase"></a>noshowbase  
 关闭显示数字所采用的进制的指示。  
  
```  
ios_base& noshowbase(ios_base& str);
```  
  
### <a name="parameters"></a>参数  
 ` str`  
 对 [ios_base](../standard-library/ios-base-class.md) 类型的对象的引用，或对从 `ios_base` 继承的类型的引用。  
  
### <a name="return-value"></a>返回值  
 对 _ *Str* 派生所源自的对象的引用。  
  
### <a name="remarks"></a>备注  
 默认情况下，`noshowbase` 处于打开状态。 使用 [showbase](../standard-library/ios-functions.md#showbase) 来指示数字基数。  
  
 此操控器有效调用 ` str.`[unsetf](../standard-library/ios-base-class.md#ios_base__unsetf)( `ios_base::showbase`)，然后返回 ` str`。  
  
### <a name="example"></a>示例  
  有关如何使用 `noshowbase` 的示例，请参阅 [showbase](../standard-library/ios-functions.md#showbase)。  
  
##  <a name="a-namenoshowpointa--noshowpoint"></a><a name="noshowpoint"></a>noshowpoint  
 仅显示浮点数（其小数部分为零）的整数部分。  
  
```  
ios_base& noshowpoint(ios_base& str);
```  
  
### <a name="parameters"></a>参数  
 ` str`  
 对 [ios_base](../standard-library/ios-base-class.md) 类型的对象的引用，或对从 `ios_base` 继承的类型的引用。  
  
### <a name="return-value"></a>返回值  
 对 _ *Str* 派生所源自的对象的引用。  
  
### <a name="remarks"></a>备注  
 `noshowpoint` 默认为打开；使用 [showpoint](../standard-library/ios-functions.md#showpoint) 和 [precision](../standard-library/ios-base-class.md#ios_base__precision) 显示小数点后的零。  
  
 此操控器有效调用 ` str.`[unsetf](../standard-library/ios-base-class.md#ios_base__unsetf)( `ios_base::showpoint`)，然后返回 ` str`。  
  
### <a name="example"></a>示例  
  
```cpp  
// ios_noshowpoint.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   double f1= 5.000;  
   cout << f1 << endl;   // noshowpoint is default  
   cout.precision( 4 );  
   cout << showpoint << f1 << endl;  
   cout << noshowpoint << f1 << endl;  
}  
```  
  
```Output  
5  
5.000  
5  
```  
  
##  <a name="a-namenoshowposa--noshowpos"></a><a name="noshowpos"></a>noshowpos  
 导致正数不显式带有符号。  
  
```  
ios_base& noshowpos(ios_base& str);
```  
  
### <a name="parameters"></a>参数  
 ` str`  
 对 [ios_base](../standard-library/ios-base-class.md) 类型的对象的引用，或对从 `ios_base` 继承的类型的引用。  
  
### <a name="return-value"></a>返回值  
 对 _ *Str* 派生所源自的对象的引用。  
  
### <a name="remarks"></a>备注  
 默认情况下，`noshowpos` 处于打开状态。  
  
 此操控器有效调用 ` str.`[unsetf](../standard-library/ios-base-class.md#ios_base__unsetf)( `ios_base::showps`)，然后返回 ` str`。  
  
### <a name="example"></a>示例  
  有关使用 `noshowpos` 的示例，请参阅 [showpos](../standard-library/ios-functions.md#showpos)。  
  
##  <a name="a-namenoskipwsa--noskipws"></a><a name="noskipws"></a>noskipws  
 导致输入流读取空格。  
  
```  
ios_base& noskipws(ios_base& str);
```  
  
### <a name="parameters"></a>参数  
 ` str`  
 对 [ios_base](../standard-library/ios-base-class.md) 类型的对象的引用，或对从 `ios_base` 继承的类型的引用。  
  
### <a name="return-value"></a>返回值  
 对 _ *Str* 派生所源自的对象的引用。  
  
### <a name="remarks"></a>备注  
 [skipws](../standard-library/ios-functions.md#skipws) 默认为开启状态。 读取到流中的空格时，它表示缓冲区的结束。  
  
 此操控器有效调用 ` str.`[unsetf](../standard-library/ios-base-class.md#ios_base__unsetf)( `ios_base::skipws`)，然后返回 ` str`。  
  
### <a name="example"></a>示例  
  
```cpp  
// ios_noskipws.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <string>  
  
int main() {  
   using namespace std;     
   string s1, s2, s3;  
   cout << "Enter three strings: ";  
   cin >> noskipws >> s1 >> s2 >> s3;  
   cout << "." << s1  << "." << endl;  
   cout << "." << s2 << "." << endl;  
   cout << "." << s3 << "." << endl;     
}  
```  
  
##  <a name="a-namenounitbufa--nounitbuf"></a><a name="nounitbuf"></a>nounitbuf  
 导致缓冲区已满时缓冲和处理输出。  
  
```  
ios_base& nounitbuf(ios_base& str);
```  
  
### <a name="parameters"></a>参数  
 ` str`  
 对 [ios_base](../standard-library/ios-base-class.md) 类型的对象的引用，或对从 `ios_base` 继承的类型的引用。  
  
### <a name="return-value"></a>返回值  
 对 _ *Str* 派生所源自的对象的引用。  
  
### <a name="remarks"></a>备注  
 [unitbuf](../standard-library/ios-functions.md#unitbuf) 导致在缓冲区未满时处理缓冲区。  
  
 此操控器有效调用 ` str.`[unsetf](../standard-library/ios-base-class.md#ios_base__unsetf)( `ios_base::unitbuf`)，然后返回 ` str`。  
  
##  <a name="a-namenouppercasea--nouppercase"></a><a name="nouppercase"></a>nouppercase  
 指定十六进制数字和科学计数法形式的指数以小写形式显示。  
  
```  
ios_base& nouppercase(ios_base& str);
```  
  
### <a name="parameters"></a>参数  
 ` str`  
 对 [ios_base](../standard-library/ios-base-class.md) 类型的对象的引用，或对从 `ios_base` 继承的类型的引用。  
  
### <a name="return-value"></a>返回值  
 对 _ *Str* 派生所源自的对象的引用。  
  
### <a name="remarks"></a>备注  
 此操控器有效调用 ` str.`[unsetf](../standard-library/ios-base-class.md#ios_base__unsetf)( `ios_base::uppercase`)，然后返回 ` str`。  
  
### <a name="example"></a>示例  
  有关使用 `nouppercase` 的示例，请参阅 [uppercase](../standard-library/ios-functions.md#uppercase)。  
  
##  <a name="a-nameocta--oct"></a><a name="oct"></a>oct  
 指定以八进制计数法形式显示整数变量。  
  
```  
ios_base& oct(ios_base& str);
```  
  
### <a name="parameters"></a>参数  
 ` str`  
 对 [ios_base](../standard-library/ios-base-class.md) 类型的对象的引用，或对从 `ios_base` 继承的类型的引用。  
  
### <a name="return-value"></a>返回值  
 对 _ *Str* 派生所源自的对象的引用。  
  
### <a name="remarks"></a>备注  
 默认情况下，整型变量以十进制计数法显示。 [dec](../standard-library/ios-functions.md#dec) 和 [hex](../standard-library/ios-functions.md#hex) 也会改变整型变量显示的方式。  
  
 此操控器有效调用 ` str.`[setf](../standard-library/ios-base-class.md#ios_base__setf)( `ios_base::oct`, `ios_base::basefield`)，然后返回 ` str`。  
  
### <a name="example"></a>示例  
  有关如何使用 **oct** 的示例，请参阅 [dec](../standard-library/ios-functions.md#dec)。  
  
##  <a name="a-namerighta--right"></a><a name="right"></a>right  
 导致宽度比输出宽度短的文本在流刷新过程中显示时带有右边距。  
  
```  
ios_base& right(ios_base& str);
```  
  
### <a name="parameters"></a>参数  
 ` str`  
 对 [ios_base](../standard-library/ios-base-class.md) 类型的对象的引用，或对从 `ios_base` 继承的类型的引用。  
  
### <a name="return-value"></a>返回值  
 对 _ *Str* 派生所源自的对象的引用。  
  
### <a name="remarks"></a>备注  
 [left](../standard-library/ios-functions.md#left) 还会修改文本对齐方式。  
  
 此操控器有效调用 ` str.`[setf](../standard-library/ios-base-class.md#ios_base__setf)( `ios_base::right`, `ios_base::adjustfield`)，然后返回 ` str`。  
  
### <a name="example"></a>示例  
  
```cpp  
// ios_right.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   double f1= 5.00;  
   cout << f1 << endl;  
   cout.width( 20 );  
   cout << f1 << endl;  
   cout.width( 20 );  
   cout << left << f1 << endl;  
   cout.width( 20 );  
   cout << f1 << endl;  
   cout.width( 20 );  
   cout << right << f1 << endl;  
   cout.width( 20 );  
   cout << f1 << endl;  
}  
```  
  
```Output  
5  
                   5  
5                     
5                     
                   5  
                   5  
```  
  
##  <a name="a-namescientifica--scientific"></a><a name="scientific"></a>scientific  
 导致使用科学记数法显示浮点数。  
  
```  
ios_base& scientific(ios_base& str);
```  
  
### <a name="parameters"></a>参数  
 ` str`  
 对 [ios_base](../standard-library/ios-base-class.md) 类型的对象的引用，或对从 `ios_base` 继承的类型的引用。  
  
### <a name="return-value"></a>返回值  
 对 _ *Str* 派生所源自的对象的引用。  
  
### <a name="remarks"></a>备注  
 默认对浮点数启用 [fixed](../standard-library/ios-functions.md#fixed) 表示法。  
  
 此操控器有效调用 ` str.`[setf](../standard-library/ios-base-class.md#ios_base__setf)( `ios_base::scientific`, `ios_base::floatfield`)，然后返回 ` str`。  
  
### <a name="example"></a>示例  
  
```cpp  
// ios_scientific.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   float i = 100.23F;  
  
   cout << i << endl;  
   cout << scientific << i << endl;  
}  
```  
  
```Output  
100.23  
1.002300e+002  
```  
  
##  <a name="a-nameshowbasea--showbase"></a><a name="showbase"></a>showbase  
 指示显示数字所采用的进制。  
  
```  
ios_base& showbase(ios_base& str);
```  
  
### <a name="parameters"></a>参数  
 ` str`  
 对 [ios_base](../standard-library/ios-base-class.md) 类型的对象的引用，或对从 `ios_base` 继承的类型的引用。  
  
### <a name="return-value"></a>返回值  
 对 _ *Str* 派生所源自的对象的引用。  
  
### <a name="remarks"></a>备注  
 可使用 [dec](../standard-library/ios-functions.md#dec)、[oct](../standard-library/ios-functions.md#oct) 或 [hex](../standard-library/ios-functions.md#hex) 更改数字的基数。  
  
 此操控器有效调用 ` str.`[setf](../standard-library/ios-base-class.md#ios_base__setf)( `ios_base::showbase`)，然后返回 ` str`。  
  
### <a name="example"></a>示例  
  
```cpp  
// ios_showbase.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   int j = 100;  
  
   cout << showbase << j << endl;   // dec is default  
   cout << hex << j << showbase << endl;  
   cout << oct << j << showbase << endl;  
  
   cout << dec << j << noshowbase << endl;  
   cout << hex << j << noshowbase << endl;  
   cout << oct << j << noshowbase << endl;  
}  
```  
  
```Output  
100  
0x64  
0144  
100  
64  
144  
```  
  
##  <a name="a-nameshowpointa--showpoint"></a><a name="showpoint"></a>showpoint  
 显示浮点数的整数部分和小数点右侧的数字，即使小数部分为零。  
  
```  
ios_base& showpoint(ios_base& str);
```  
  
### <a name="parameters"></a>参数  
 ` str`  
 对 [ios_base](../standard-library/ios-base-class.md) 类型的对象的引用，或对从 `ios_base` 继承的类型的引用。  
  
### <a name="return-value"></a>返回值  
 对 _ *Str* 派生所源自的对象的引用。  
  
### <a name="remarks"></a>备注  
 [noshowpoint](../standard-library/ios-functions.md#noshowpoint) 默认为开启状态。  
  
 此操控器有效调用 ` str.`[setf](../standard-library/ios-base-class.md#ios_base__setf)( `ios_base::showpoint`)，然后返回 ` str`。  
  
### <a name="example"></a>示例  
  有关使用 `showpoint` 的示例，请参阅 [noshowpoint](../standard-library/ios-functions.md#noshowpoint)。  
  
##  <a name="a-nameshowposa--showpos"></a><a name="showpos"></a>showpos  
 导致正数显式带有符号。  
  
```  
ios_base& showpos(ios_base& str);
```  
  
### <a name="parameters"></a>参数  
 ` str`  
 对 [ios_base](../standard-library/ios-base-class.md) 类型的对象的引用，或对从 `ios_base` 继承的类型的引用。  
  
### <a name="return-value"></a>返回值  
 对 _ *Str* 派生所源自的对象的引用。  
  
### <a name="remarks"></a>备注  
 [noshowpos](../standard-library/ios-functions.md#noshowpos) 为默认值。  
  
 此操控器有效调用 ` str.`[setf](../standard-library/ios-base-class.md#ios_base__setf)( `ios_base::showpos`)，然后返回 ` str`。  
  
### <a name="example"></a>示例  
  
```cpp  
// ios_showpos.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   int i = 1;  
  
   cout << noshowpos << i << endl;   // noshowpos is default  
   cout << showpos << i << endl;  
}  
```  
  
```Output  
1  
+1  
```  
  
##  <a name="a-nameskipwsa--skipws"></a><a name="skipws"></a>skipws  
 导致输入流不读取空格。  
  
```  
ios_base& skipws(ios_base& str);
```  
  
### <a name="parameters"></a>参数  
 ` str`  
 对 [ios_base](../standard-library/ios-base-class.md) 类型的对象的引用，或对从 `ios_base` 继承的类型的引用。  
  
### <a name="return-value"></a>返回值  
 对 _ *Str* 派生所源自的对象的引用。  
  
### <a name="remarks"></a>备注  
 默认情况，`skipws` 是有效的。 [noskipws](../standard-library/ios-functions.md#noskipws) 会导致从输入流中读取空格。  
  
 此操控器有效调用 ` str.`[setf](../standard-library/ios-base-class.md#ios_base__setf)( `ios_base::skipws`)，然后返回 ` str`。  
  
### <a name="example"></a>示例  
  
```cpp  
#include <iostream>  
#include <string>  
  
int main( )   
{  
   using namespace std;  
   char s1, s2, s3;  
   cout << "Enter three characters: ";  
   cin >> skipws >> s1 >> s2 >> s3;  
   cout << "." << s1  << "." << endl;  
   cout << "." << s2 << "." << endl;  
   cout << "." << s3 << "." << endl;  
}  
```  
  
```Output  
  
1 2 3  
  
```  
  
```Output  
  
      1 2 3.1.  
.2.  
.3.  
```  
  
##  <a name="a-nameunitbufa--unitbuf"></a><a name="unitbuf"></a>unitbuf  
 导致在缓冲区未满时处理输出。  
  
```  
ios_base& unitbuf(ios_base& str);
```  
  
### <a name="parameters"></a>参数  
 ` str`  
 对 [ios_base](../standard-library/ios-base-class.md) 类型的对象的引用，或对从 `ios_base` 继承的类型的引用。  
  
### <a name="return-value"></a>返回值  
 对 ` str` 派生所源自的对象的引用。  
  
### <a name="remarks"></a>备注  
 请注意，`endl` 也会刷新缓冲区。  
  
 [nounitbuf](../standard-library/ios-functions.md#nounitbuf) 默认为开启状态。  
  
 此操控器有效调用 ` str.`[setf](../standard-library/ios-base-class.md#ios_base__setf)( [ios_base::unitbuf](../standard-library/ios-base-class.md#ios_base__fmtflags))，然后返回 ` str`。  
  
##  <a name="a-nameuppercasea--uppercase"></a><a name="uppercase"></a>uppercase  
 指定十六进制数字和科学计数法形式的指数以大写形式显示。  
  
```  
ios_base& uppercase(ios_base& str);
```  
  
### <a name="parameters"></a>参数  
 ` str`  
 对 [ios_base](../standard-library/ios-base-class.md) 类型的对象的引用，或对从 `ios_base` 继承的类型的引用。  
  
### <a name="return-value"></a>返回值  
 对 ` str` 派生所源自的对象的引用。  
  
### <a name="remarks"></a>备注  
 [nouppercase](../standard-library/ios-functions.md#nouppercase) 默认为开启状态。  
  
 此操控器有效调用 ` str.`[setf](../standard-library/ios-base-class.md#ios_base__setf)( [ios_base::uppercase](../standard-library/ios-base-class.md#ios_base__fmtflags))，然后返回 ` str`。  
  
### <a name="example"></a>示例  
  
```cpp  
// ios_uppercase.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( void )   
{  
   using namespace std;  
  
   double i = 1.23e100;  
   cout << i << endl;  
   cout << uppercase << i << endl;  
  
   int j = 10;  
   cout << hex << nouppercase << j << endl;  
   cout << hex << uppercase << j << endl;  
}  
```  
  
```Output  
1.23e+100  
1.23E+100  
a  
A  
```  
  
## <a name="see-also"></a>另请参阅  
 [\<ios>](../standard-library/ios.md)



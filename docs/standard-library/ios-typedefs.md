---
title: '&lt;ios&gt; typedef | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- iosfwd/std::ios
- iosfwd/std::streamoff
- iosfwd/std::streampos
- iosfwd/std::streamsize
- iosfwd/std::wios
- iosfwd/std::wstreampos
ms.assetid: 0b962632-3439-44de-bf26-20c67a7f0ff3
caps.latest.revision: 
manager: ghogen
ms.openlocfilehash: 6c94f157a28c606db6e7523b9af18e972f870c46
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="ltiosgt-typedefs"></a>&lt;ios&gt; typedef
||||  
|-|-|-|  
|[ios](#ios)|[streamoff](#streamoff)|[streampos](#streampos)|  
|[streamsize](#streamsize)|[wios](#wios)|[wstreampos](#wstreampos)|  
  
##  <a name="ios"></a>ios  
 支持旧 iostream 库中的 ios 类。  
  
```  
typedef basic_ios<char, char_traits<char>> ios;  
```  
  
### <a name="remarks"></a>备注  
 该类型是模板类 [basic_ios](../standard-library/basic-ios-class.md) 的同义词，专用于具有默认字符特征的 `char` 类型的元素。  
  
##  <a name="streamoff"></a>streamoff  
 支持内部操作。  
  
```  
#ifdef _WIN64  
    typedef __int64 streamoff;  
#else  
    typedef long streamoff;  
#endif  
```  
  
### <a name="remarks"></a>备注  
 此类型为带符号整数，该整数描述的对象可存储多个流定位操作涉及的字节偏移。 它的表示形式具有至少 32 个值位。 它并不需要大得足以表示流中任意字节位置。 值 **streamoff(-1)** 通常指示错误的偏移。  
  
##  <a name="streampos"></a>streampos  
 保留缓冲区指针或文件指针的当前位置。  
  
```  
typedef fpos<mbstate_t> streampos;  
```  
  
### <a name="remarks"></a>备注  
 该类型是 [fpos](../standard-library/fpos-class.md)< `mbstate_t`> 的同义词。  
  
### <a name="example"></a>示例  
  
```cpp  
// ios_streampos.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <fstream>  
  
int main( )   
{  
   using namespace std;  
  
   ofstream x( "iostream.txt" );  
   x << "testing";  
   streampos y = x.tellp( );  
   cout << y << endl;  
}  
```  
  
```Output  
7  
```  
  
##  <a name="streamsize"></a>streamsize  
 表示流的大小。  
  
```  
#ifdef _WIN64  
    typedef __int64 streamsize;  
#else  
    typedef int streamsize;  
#endif  
```  
  
### <a name="remarks"></a>备注  
 此类型为带符号整数，该整数描述的对象可存储多个流操作涉及的元素数量计数。 它的表示形式具有至少 16 个值位。 它并不需要大得足以表示流中任意字节位置。  
  
### <a name="example"></a>示例  
  编译并运行如下程序后，请浏览文件 file test 以查看 `streamsize` 设置的效果。  
  
```  
// ios_streamsize.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <fstream>  
  
int main( )   
{  
   using namespace std;  
   char a[16] = "any such text";  
   ofstream x( "test.txt" );  
   streamsize y = 6;  
   x.write( a, y );  
}  
```  
  
##  <a name="wios"></a>wios  
 支持旧 iostream 库中的 wios 类。  
  
```  
typedef basic_ios<wchar_t, char_traits<wchar_t>> wios;  
```  
  
### <a name="remarks"></a>备注  
 该类型是模板类 [basic_ios](../standard-library/basic-ios-class.md) 的同义词，专用于具有默认字符特征的 `wchar_t` 类型的元素。  
  
##  <a name="wstreampos"></a>wstreampos  
 保留缓冲区指针或文件指针的当前位置。  
  
```  
typedef fpos<mbstate_t> wstreampos;  
```  
  
### <a name="remarks"></a>备注  
 该类型是 [fpos](../standard-library/fpos-class.md)< `mbstate_t`> 的同义词。  
  
### <a name="example"></a>示例  
  
```cpp  
// ios_wstreampos.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <fstream>  
  
int main( )   
{  
   using namespace std;  
   wofstream xw( "wiostream.txt" );  
   xw << L"testing";  
   wstreampos y = xw.tellp( );  
   cout << y << endl;  
}  
```  
  
```Output  
7  
```  
  
## <a name="see-also"></a>请参阅  
 [\<ios>](../standard-library/ios.md)


---
title: "numpunct 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "xlocnum/std::numpunct"
  - "std::numpunct"
  - "numpunct"
  - "std.numpunct"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "numpunct 类"
ms.assetid: 73fb93cc-ac11-4c98-987c-bfa6267df596
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# numpunct 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

一种模板类，用于描述一个对象来充当区域设置 facet，以便描述 `CharType` 类型的序列，后者用于表示与数字和布尔表达式的格式化及标点有关的信息。  
  
## <a name="syntax"></a>语法  
  
```  
template <class CharType>  
class numpunct : public locale::facet;  
```  
  
#### <a name="parameters"></a>参数  
 `CharType`  
 在程序中用于对区域设置中的字符进行编码的类型。  
  
## <a name="remarks"></a>备注  
 对于任何区域设置 facet，静态对象 ID 的初始存储值为零。 第一次尝试访问其存储的值中存储唯一正值中的 **id。**  
  
### <a name="constructors"></a>构造函数  
  
|||  
|-|-|  
|[numpunct](#numpunct__numpunct)|`numpunct` 类型的对象的构造函数。|  
  
### <a name="typedefs"></a>Typedef  
  
|||  
|-|-|  
|[char_type](#numpunct__char_type)|一种类型，此类型用于描述区域设置使用的字符。|  
|[string_type](#numpunct__string_type)|一种类型，此类型描述包含 `CharType` 类型字符的字符串。|  
  
### <a name="member-functions"></a>成员函数  
  
|||  
|-|-|  
|[decimal_point](#numpunct__decimal_point)|返回要用作小数点的区域设置特定元素。|  
|[do_decimal_point](#numpunct__do_decimal_point)|一种受保护的虚拟成员函数，通过调用此函数可返回要用作小数点的区域设置特定元素。|  
|[do_falsename](#numpunct__do_falsename)|一种受保护的虚拟成员函数，通过调用此函数可返回要用作值 `false` 的文本表示形式的字符串。|  
|[do_grouping](#numpunct__do_grouping)|一种受保护的虚拟成员函数，通过调用此函数可返回用于确定位数如何分组到任何小数点左边的区域设置特定规则。|  
|[do_thousands_sep](#numpunct__do_thousands_sep)|一种受保护的虚拟成员函数，通过调用此函数可返回要用作千位分隔符的区域设置特定元素。|  
|[do_truename](#numpunct__do_truename)|一种受保护的虚拟成员函数，通过调用此函数可返回要用作值 `true` 的文本表示形式的字符串。|  
|[falsename](#numpunct__falsename)|返回要用作值 `false` 的文本表示形式的字符串。|  
|[分组](#numpunct__grouping)|返回用于确定位数如何分组到任何小数点左边的区域设置特定规则。|  
|[thousands_sep](#numpunct__thousands_sep)|返回要用作千位分隔符的区域设置特定元素。|  
|[truename](#numpunct__truename)|返回要用作值 `true` 的文本表示形式的字符串。|  
  
## <a name="requirements"></a>要求  
 **标头︰** \< 区域设置>  
  
 **命名空间：** std  
  
##  <a name="a-namenumpunctchartypea-numpunctchartype"></a><a name="numpunct__char_type"></a>  numpunct:: char_type  
 一种类型，此类型用于描述区域设置使用的字符。  
  
```  
typedef CharType char_type;  
```  
  
### <a name="remarks"></a>备注  
 类型是模板参数的同义词 **CharType。**  
  
##  <a name="a-namenumpunctdecimalpointa-numpunctdecimalpoint"></a><a name="numpunct__decimal_point"></a>  numpunct:: decimal_point  
 返回要用作小数点的区域设置特定元素。  
  
```  
CharType decimal_point() const;
```  
  
### <a name="return-value"></a>返回值  
 要用作小数点的区域设置特定元素。  
  
### <a name="remarks"></a>备注  
 成员函数将返回 [do_decimal_point](#numpunct__do_decimal_point)。  
  
### <a name="example"></a>示例  
  
```  
// numpunct_decimal_point.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <sstream>  
using namespace std;  
int main( )  
{  
   locale loc( "german_germany" );  
  
   const numpunct <char> &npunct =   
   use_facet <numpunct <char> >( loc);  
   cout << loc.name( ) << " decimal point "<<   
   npunct.decimal_point( ) << endl;  
   cout << loc.name( ) << " thousands separator "   
   << npunct.thousands_sep( ) << endl;  
};  
```  
  
```Output  
German_Germany.1252 decimal point ,  
German_Germany.1252 thousands separator .  
```  
  
##  <a name="a-namenumpunctdodecimalpointa-numpunctdodecimalpoint"></a><a name="numpunct__do_decimal_point"></a>  numpunct:: do_decimal_point  
 一种受保护的虚拟成员函数，通过调用此函数可返回要用作小数点的区域设置特定元素。  
  
```  
virtual CharType do_decimal_point() const;
```  
  
### <a name="return-value"></a>返回值  
 要用作小数点的区域设置特定元素。  
  
### <a name="example"></a>示例  
  请参阅示例 [decimal_point](#numpunct__decimal_point), ，其中的虚拟成员函数将由 `decimal_point`。  
  
##  <a name="a-namenumpunctdofalsenamea-numpunctdofalsename"></a><a name="numpunct__do_falsename"></a>  numpunct:: do_falsename  
 受保护虚拟成员函数将返回一个序列，以便使用值的文本表示形式， **false**。  
  
```  
virtual string_type do_falsename() const;
```  
  
### <a name="return-value"></a>返回值  
 一个包含要使用的值的文本表示形式的序列的字符串 **false**。  
  
### <a name="remarks"></a>备注  
 成员函数将返回字符串"false"来表示值 **false** 在所有区域设置中。  
  
### <a name="example"></a>示例  
  请参阅示例 [falsename](#numpunct__falsename), ，其中的虚拟成员函数将由 `falsename`。  
  
##  <a name="a-namenumpunctdogroupinga-numpunctdogrouping"></a><a name="numpunct__do_grouping"></a>  numpunct:: do_grouping  
 一种受保护的虚拟成员函数，通过调用此函数可返回用于确定位数如何分组到任何小数点左边的区域设置特定规则。  
  
```  
virtual string do_grouping() const;
```  
  
### <a name="return-value"></a>返回值  
 用于确定位数如何分组到任何小数点左边的区域设置特定规则。  
  
### <a name="remarks"></a>备注  
 此受保护的虚拟成员函数可返回一个区域设置特定规则，用于确定如何对任何小数点左侧的数字进行分组。 编码是相同 **lconv::grouping**。  
  
### <a name="example"></a>示例  
  请参阅示例 [分组](#numpunct__grouping), ，其中的虚拟成员函数将由 **分组**。  
  
##  <a name="a-namenumpunctdothousandssepa-numpunctdothousandssep"></a><a name="numpunct__do_thousands_sep"></a>  numpunct:: do_thousands_sep  
 一种受保护的虚拟成员函数，通过调用此函数可返回要用作千位分隔符的区域设置特定元素。  
  
```  
virtual CharType do_thousands_sep() const;
```  
  
### <a name="return-value"></a>返回值  
 返回要用作千位分隔符的区域设置特定元素。  
  
### <a name="remarks"></a>备注  
 受保护虚拟成员函数返回类型的区域设置特定元素 **CharType** 要用作组分隔符的任何小数点左侧。  
  
### <a name="example"></a>示例  
  请参阅示例 [thousands_sep](#numpunct__thousands_sep), ，其中的虚拟成员函数将由 `thousands_sep`。  
  
##  <a name="a-namenumpunctdotruenamea-numpunctdotruename"></a><a name="numpunct__do_truename"></a>  numpunct:: do_truename  
 一种受保护虚拟成员函数调用以返回要使用的值的文本表示形式的字符串， **true**。  
  
```  
virtual string_type do_truename() const;
```  
  
### <a name="remarks"></a>备注  
 要使用的值的文本表示形式的字符串 **true**。  
  
 所有区域设置返回字符串"true"来表示值 **true**。  
  
### <a name="example"></a>示例  
  请参阅示例 [truename](#numpunct__truename), ，其中的虚拟成员函数将由 `truename`。  
  
##  <a name="a-namenumpunctfalsenamea-numpunctfalsename"></a><a name="numpunct__falsename"></a>  numpunct:: falsename  
 返回要使用的值的文本表示形式的字符串 **false**。  
  
```  
string_type falsename() const;
```  
  
### <a name="return-value"></a>返回值  
 一个包含一系列字符串 **CharType**s 可用作值的文本表示 **false**。  
  
### <a name="remarks"></a>备注  
 成员函数将返回字符串"false"来表示值 **false** 在所有区域设置中。  
  
 成员函数将返回 [do_falsename](#numpunct__do_falsename)。  
  
### <a name="example"></a>示例  
  
```  
// numpunct_falsename.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <sstream>  
using namespace std;  
int main( )  
{  
   locale loc( "English" );  
  
   const numpunct <char> &npunct = use_facet <numpunct <char> >( loc );  
   cout << loc.name( ) << " truename "<< npunct.truename( ) << endl;  
   cout << loc.name( ) << " falsename "<< npunct.falsename( ) << endl;  
  
   locale loc2( "French" );  
   const numpunct <char> &npunct2 = use_facet <numpunct <char> >(loc2);  
   cout << loc2.name( ) << " truename "<< npunct2.truename( ) << endl;  
   cout << loc2.name( ) << " falsename "<< npunct2.falsename( ) << endl;  
}  
```  
  
```Output  
English_United States.1252 truename true  
English_United States.1252 falsename false  
French_France.1252 truename true  
French_France.1252 falsename false  
```  
  
##  <a name="a-namenumpunctgroupinga-numpunctgrouping"></a><a name="numpunct__grouping"></a>  numpunct:: grouping  
 返回用于确定位数如何分组到任何小数点左边的区域设置特定规则。  
  
```  
string grouping() const;
```  
  
### <a name="return-value"></a>返回值  
 用于确定位数如何分组到任何小数点左边的区域设置特定规则。  
  
### <a name="remarks"></a>备注  
 成员函数将返回 [do_grouping](#numpunct__do_grouping)。  
  
### <a name="example"></a>示例  
  
```  
// numpunct_grouping.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <sstream>  
using namespace std;  
int main( )  
{  
   locale loc( "german_germany");  
  
   const numpunct <char> &npunct =   
       use_facet < numpunct <char> >( loc );  
   for (unsigned int i = 0; i < npunct.grouping( ).length( ); i++)  
   {  
      cout << loc.name( ) << " international grouping:\n the "  
           << i <<"th group to the left of the radix character "  
           << "is of size " << (int)(npunct.grouping ( )[i])   
           << endl;  
   }  
}  
```  
  
```Output  
German_Germany.1252 international grouping:  
 the 0th group to the left of the radix character is of size 3  
```  
  
##  <a name="a-namenumpunctnumpuncta-numpunctnumpunct"></a><a name="numpunct__numpunct"></a>  numpunct:: numpunct  
 `numpunct` 类型的对象的构造函数。  
  
```  
explicit numpunct(size_t _Refs = 0);
```  
  
### <a name="parameters"></a>参数  
 `_Refs`  
 用来指定对象的内存管理的类型的整数值。  
  
### <a name="remarks"></a>备注  
 可能的值 `_Refs` 参数和其重要性都是︰  
  
-   0: 对象的生存期由包含它的区域设置。  
  
-   1︰ 必须手动管理对象的生存期。  
  
-   \> 0︰ 未定义这些值。  
  
 由于保护析构函数，是可能的没有直接的示例。  
  
 构造函数初始化与与其基对象 **区域设置::**[方面](../standard-library/locale-class.md#facet_class)( `_Refs`)。  
  
##  <a name="a-namenumpunctstringtypea-numpunctstringtype"></a><a name="numpunct__string_type"></a>  numpunct:: string_type  
 该类型描述包含类型的字符的字符串 **CharType**。  
  
```  
typedef basic_string<CharType, Traits, Allocator> string_type;  
```  
  
### <a name="remarks"></a>备注  
 此类型描述模板类的专用化 [basic_string](../standard-library/basic-string-class.md) 其对象可存储的标点序列副本。  
  
##  <a name="a-namenumpunctthousandssepa-numpunctthousandssep"></a><a name="numpunct__thousands_sep"></a>  numpunct:: thousands_sep  
 返回要用作千位分隔符的区域设置特定元素。  
  
```  
CharType thousands_sep() const;
```  
  
### <a name="return-value"></a>返回值  
 要用作千位的区域设置特定元素分隔符。  
  
### <a name="remarks"></a>备注  
 成员函数将返回 [do_thousands_sep](#numpunct__do_thousands_sep)。  
  
### <a name="example"></a>示例  
  
```  
// numpunct_thou_sep.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <sstream>  
using namespace std;  
int main( )  
{  
   locale loc( "german_germany" );  
  
   const numpunct <char> &npunct =   
   use_facet < numpunct < char > >( loc );  
   cout << loc.name( ) << " decimal point "<<   
   npunct.decimal_point( ) << endl;  
   cout << loc.name( ) << " thousands separator "   
   << npunct.thousands_sep( ) << endl;  
};  
```  
  
```Output  
German_Germany.1252 decimal point ,  
German_Germany.1252 thousands separator .  
```  
  
##  <a name="a-namenumpuncttruenamea-numpuncttruename"></a><a name="numpunct__truename"></a>  numpunct:: truename  
 返回要使用的值的文本表示形式的字符串 **true**。  
  
```  
string_type falsename() const;
```  
  
### <a name="return-value"></a>返回值  
 要使用的值的文本表示形式的字符串 **true**。  
  
### <a name="remarks"></a>备注  
 成员函数将返回 [do_truename](#numpunct__do_truename)。  
  
 所有区域设置返回字符串"true"来表示值 **true**。  
  
### <a name="example"></a>示例  
  
```  
// numpunct_truename.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <sstream>  
using namespace std;  
int main( )  
{  
   locale loc( "English" );  
  
   const numpunct < char> &npunct = use_facet <numpunct <char> >( loc );  
   cout << loc.name( ) << " truename "<< npunct.truename( ) << endl;  
   cout << loc.name( ) << " falsename "<< npunct.falsename( ) << endl;  
  
   locale loc2("French");  
   const numpunct <char> &npunct2 = use_facet <numpunct <char> >( loc2 );  
   cout << loc2.name( ) << " truename "<< npunct2.truename( ) << endl;  
   cout << loc2.name( ) << " falsename "<< npunct2.falsename( ) << endl;  
}  
```  
  
```Output  
English_United States.1252 truename true  
English_United States.1252 falsename false  
French_France.1252 truename true  
French_France.1252 falsename false  
```  
  
## <a name="see-also"></a>另请参阅  
 [\< 区域设置>](../standard-library/locale.md)   
 [facet 类](../standard-library/locale-class.md#facet_class)   
 [C + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)


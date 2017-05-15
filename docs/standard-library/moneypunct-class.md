---
title: "moneypunct 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- moneypunct
- xlocmon/std::moneypunct
- locale/std::moneypunct::char_type
- locale/std::moneypunct::string_type
- locale/std::moneypunct::curr_symbol
- locale/std::moneypunct::decimal_point
- locale/std::moneypunct::do_curr_symbol
- locale/std::moneypunct::do_decimal_point
- locale/std::moneypunct::do_frac_digits
- locale/std::moneypunct::do_grouping
- locale/std::moneypunct::do_neg_format
- locale/std::moneypunct::do_negative_sign
- locale/std::moneypunct::do_pos_format
- locale/std::moneypunct::do_positive_sign
- locale/std::moneypunct::do_thousands_sep
- locale/std::moneypunct::frac_digits
- locale/std::moneypunct::grouping
- locale/std::moneypunct::neg_format
- locale/std::moneypunct::negative_sign
- locale/std::moneypunct::pos_format
- locale/std::moneypunct::positive_sign
- locale/std::moneypunct::thousands_sep
dev_langs:
- C++
helpviewer_keywords:
- moneypunct class
ms.assetid: cf2650da-3e6f-491c-95d5-23e57f582ee6
caps.latest.revision: 20
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
ms.openlocfilehash: 9567db1b823f373a5ea26e6d113cc9176901453d
ms.contentlocale: zh-cn
ms.lasthandoff: 04/29/2017

---
# <a name="moneypunct-class"></a>moneypunct 类
此模板类描述一个对象来充当区域设置 facet，以便描述用来表示货币输入字段或货币输出字段的 `CharType` 类序列。 如果模板参数 `Intl` 为 `true`，则遵守国际约定。  
  
## <a name="syntax"></a>语法  
  
```  
template <class CharType, bool Intl>  
class moneypunct;  
```  
  
#### <a name="parameters"></a>参数  
 `CharType`  
 在程序中用于对字符进行编码的类型。  
  
 `Intl`  
 一种用于指定是否遵守国际约定的标志。  
  
## <a name="remarks"></a>备注  
 对于任何区域设置 facet，静态对象 ID 的初始存储值为零。 首次尝试访问其存储值后，将在 **ID** 中存储唯一正值。  
  
 常量静态对象 intl 用于存储模板参数 **Intl** 的值。  
  
### <a name="constructors"></a>构造函数  
  
|||  
|-|-|  
|[moneypunct](#moneypunct)|`moneypunct` 类型对象的构造函数。|  
  
### <a name="typedefs"></a>Typedef  
  
|||  
|-|-|  
|[char_type](#char_type)|一种类型，此类型用于描述区域设置使用的字符。|  
|[string_type](#string_type)|一种类型，此类型描述包含 `CharType` 类型字符的字符串。|  
  
### <a name="member-functions"></a>成员函数  
  
|||  
|-|-|  
|[curr_symbol](#curr_symbol)|返回要用作货币符号的区域设置特定元素序列。|  
|[decimal_point](#decimal_point)|返回要用作小数点符号的区域设置特定元素序列。|  
|[do_curr_symbol](#do_curr_symbol)|一种受保护的虚拟成员函数，可返回要用作货币符号的区域设置特定元素序列。|  
|[do_decimal_point](#do_decimal_point)|一种受保护的虚拟成员函数，通过调用此函数可返回要用作小数点符号的区域设置特定元素序列。|  
|[do_frac_digits](#do_frac_digits)|此受保护的虚拟成员函数可返回一个在任何小数点右侧显示的位数计数。|  
|[do_grouping](#do_grouping)|此受保护的虚拟成员函数可返回一个区域设置特定规则，用于确定如何对任何小数点左侧的数字进行分组。|  
|[do_neg_format](#do_neg_format)|一种受保护的虚拟成员函数，通过调用此函数可返回一个区域设置特定规则，用于对包含负数的输出结果进行格式化。|  
|[do_negative_sign](#do_negative_sign)|一种受保护的虚拟成员函数，通过调用此函数可返回要用作负号符号的区域设置特定元素序列。|  
|[do_pos_format](#do_pos_format)|一种受保护的虚拟成员函数，通过调用此函数可返回一个区域设置特定规则，用于对包含正数的输出结果进行格式化。|  
|[do_positive_sign](#do_positive_sign)|一种受保护的虚拟成员函数，通过调用此函数可返回要用作正号符号的区域设置特定元素序列。|  
|[do_thousands_sep](#do_thousands_sep)|一种受保护的虚拟成员函数，通过调用此函数可返回要用作千位分隔符号的区域设置特定元素序列。|  
|[frac_digits](#frac_digits)|可返回一个在任何小数点右侧显示的位数计数。|  
|[grouping](#grouping)|返回用于确定位数如何分组到任何小数点左边的区域设置特定规则。|  
|[neg_format](#neg_format)|返回一个区域设置特定规则，用于对包含负数的输出结果进行格式化。|  
|[negative_sign](#negative_sign)|返回要用作负号符号的区域设置特定元素序列。|  
|[pos_format](#pos_format)|返回一个区域设置特定规则，用于对包含正数的输出结果进行格式化。|  
|[positive_sign](#positive_sign)|返回要用作正号符号的区域设置特定元素序列。|  
|[thousands_sep](#thousands_sep)|返回要用作千位分隔符号的区域设置特定元素序列。|  
  
## <a name="requirements"></a>要求  
 **标头：**\<locale>  
  
 **命名空间：** std  
  
##  <a name="char_type"></a>moneypunct::char_type  
 一种类型，此类型用于描述区域设置使用的字符。  
  
```  
typedef CharType char_type;  
```  
  
### <a name="remarks"></a>备注  
 该类型是模板参数 **CharType** 的同义词。  
  
##  <a name="curr_symbol"></a>moneypunct::curr_symbol  
 返回要用作货币符号的区域设置特定元素序列。  
  
```  
string_type curr_symbol() const;
```  
  
### <a name="return-value"></a>返回值  
 包含货币符号的字符串。  
  
### <a name="remarks"></a>备注  
 此成员函数返回 [do_curr_symbol](#do_curr_symbol)。  
  
### <a name="example"></a>示例  
  
```cpp  
// moneypunct_curr_symbol.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <sstream>  
using namespace std;  
int main( )  
{  
   locale loc( "german_germany" );  
  
   const moneypunct < char, true > &mpunct = use_facet < moneypunct < char, true > >(loc);  
   cout << loc.name( ) << " international currency symbol "<<  mpunct.curr_symbol( ) << endl;  
  
   const moneypunct < char, false> &mpunct2 = use_facet < moneypunct < char, false> >(loc);  
   cout << loc.name( ) << " domestic currency symbol "<<  mpunct2.curr_symbol( ) << endl;  
};  
```  
  
##  <a name="decimal_point"></a>moneypunct::decimal_point  
 返回要用作小数点符号的区域设置特定元素序列。  
  
```  
CharType decimal_point() const;
```  
  
### <a name="return-value"></a>返回值  
 要用作小数点符号的区域设置特定元素序列。  
  
### <a name="remarks"></a>备注  
 此成员函数返回 [do_decimal_point](#do_decimal_point)。  
  
### <a name="example"></a>示例  
  
```cpp  
// moneypunct_decimal_pt.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <sstream>  
using namespace std;  
int main( )  
{  
   locale loc("german_germany");  
  
   const moneypunct < char, true > &mpunct = use_facet   
      < moneypunct < char, true > >(loc);  
   cout << loc.name( ) << " international decimal point "  
        << mpunct.decimal_point( ) << endl;  
  
   const moneypunct < char, false> &mpunct2 = use_facet   
      < moneypunct < char, false> >(loc);  
   cout << loc.name( ) << " domestic decimal point "  
        << mpunct2.decimal_point( ) << endl;  
}  
```  
  
```Output  
German_Germany.1252 international decimal point ,  
German_Germany.1252 domestic decimal point ,  
```  
  
##  <a name="do_curr_symbol"></a>  moneypunct::do_curr_symbol  
 一种受保护的虚拟成员函数，可返回要用作货币符号的区域设置特定元素序列。  
  
```  
virtual string_type do_curr_symbol() const;
```  
  
### <a name="return-value"></a>返回值  
 要用作小数点符号的区域设置特定元素序列。  
  
### <a name="example"></a>示例  
  请参阅 [curr_symbol](#curr_symbol) 的示例，其中虚拟成员函数由 `curr_symbol` 调用。  
  
##  <a name="do_decimal_point"></a>  moneypunct::do_decimal_point  
 一种受保护的虚拟成员函数，可返回要用作小数点符号的区域设置特定元素序列。  
  
```  
virtual CharType do_decimal_point() const;
```  
  
### <a name="return-value"></a>返回值  
 要用作小数点符号的区域设置特定元素序列。  
  
### <a name="example"></a>示例  
  请参阅 [decimal_point](#decimal_point) 的示例，其中虚拟成员函数由 `decimal_point` 调用。  
  
##  <a name="do_frac_digits"></a>  moneypunct::do_frac_digits  
 一种受保护的虚拟成员函数，可返回一个在任何小数点右侧显示的位数计数。  
  
```  
virtual int do_frac_digits() const;
```  
  
### <a name="return-value"></a>返回值  
 一个在任何小数点右侧显示的区域设置特定位数计数。  
  
### <a name="example"></a>示例  
  请参阅 [frac_digits](#frac_digits) 的示例，其中虚拟成员函数由 `frac_digits` 调用。  
  
##  <a name="do_grouping"></a>  moneypunct::do_grouping  
 一种受保护的虚拟成员函数，可返回用于确定如何对任何小数点左侧的数字进行分组的区域设置特定规则。  
  
```  
virtual string do_grouping() const;
```  
  
### <a name="return-value"></a>返回值  
 用于确定如何对任何小数点左侧的数字进行分组的区域设置特定规则。  
  
### <a name="example"></a>示例  
  请参阅 [grouping](#grouping) 的示例，其中虚拟成员函数由 **grouping** 调用。  
  
##  <a name="do_neg_format"></a>  moneypunct::do_neg_format  
 一种受保护的虚拟成员函数，通过调用此函数可返回一个区域设置特定规则，用于对包含负数的输出结果进行格式化。  
  
```  
virtual pattern do_neg_format() const;
```  
  
### <a name="return-value"></a>返回值  
 此受保护的虚拟成员函数可返回一个区域设置特定规则，用于确定生成负金额的货币输出字段的方式。 **pattern::field** 的四个元素中的每一个都可以具有以下值：  
  
- **none** - 用于匹配零个或多个空格，或不生成任何内容。  
  
- **sign** - 用于匹配或生成正负号。  
  
- **space** - 用于匹配零个或多个空格，或生成空格。  
  
- **symbol** - 用于匹配或生成货币符号。  
  
- **value** - 用于匹配或生成货币值。  
  
 生成货币输出字段组件和匹配货币输入字段组件都以这些元素在 **pattern::field** 中的显示的顺序进行。 每个值 **sign**、**symbol**、**value**、**none** 或 **space** 必须出现一次。 值 **none** 不能第一个出现。 值 **space** 不能第一个或最后一个出现。 如果 **Intl** 为 true，则顺序为 **symbol**、**sign**、**none**，然后是 **value**。  
  
 `moneypunct`\< **CharType**, **Intl**> 的模板版本返回 `{`**money_base::symbol**, **money_base::sign**, **money_base::value**, **money_base::none**`}`。  
  
### <a name="example"></a>示例  
  请参阅 [neg_format](#neg_format) 的示例，其中虚拟成员函数由 `neg_format` 调用。  
  
##  <a name="do_negative_sign"></a>  moneypunct::do_negative_sign  
 一种受保护的虚拟成员函数，通过调用此函数可返回要用作负号符号的区域设置特定元素序列。  
  
```  
virtual string_type do_negative_sign() const;
```  
  
### <a name="return-value"></a>返回值  
 要用作负号的区域设置特定元素序列。  
  
### <a name="example"></a>示例  
  请参阅 [negative_sign](#negative_sign) 的示例，其中虚拟成员函数由 `negative_sign` 调用。  
  
##  <a name="do_pos_format"></a>  moneypunct::do_pos_format  
 一种受保护的虚拟成员函数，通过调用此函数可返回一个区域设置特定规则，用于对包含正数的输出结果进行格式化。  
  
```  
virtual pattern do_pos_format() const;
```  
  
### <a name="return-value"></a>返回值  
 此受保护的虚拟成员函数可返回一个区域设置特定规则，用于确定生成正金额的货币输出字段的方式。 （它还确定如何匹配货币输入字段的组件。）该编码与 [do_neg_format](#do_neg_format) 的编码相同。  
  
 moneypunct\< **CharType**, **Inputlterator**> 的模板版本返回 `{`**money_base::symbol**, **money_base::sign**, **money_base::value**, **money_base::none**`}`。  
  
### <a name="example"></a>示例  
  请参阅 [pos_format](#pos_format) 的示例，其中虚拟成员函数由 `pos_format` 调用。  
  
##  <a name="do_positive_sign"></a>  moneypunct::do_positive_sign  
 一种受保护的虚拟成员函数，可返回要用作正号的区域设置特定元素序列。  
  
```  
virtual string_type do_positive_sign() const;
```  
  
### <a name="return-value"></a>返回值  
 要用作正号的区域设置特定元素序列。  
  
### <a name="example"></a>示例  
  请参阅 [positive_sign](#positive_sign) 的示例，其中虚拟成员函数由 `positive_sign` 调用。  
  
##  <a name="do_thousands_sep"></a>  moneypunct::do_thousands_sep  
 一种受保护的虚拟成员函数，可返回要用作任何小数点左侧的组分隔符的区域设置特定元素。  
  
```  
virtual CharType do_thousands_sep() const;
```  
  
### <a name="return-value"></a>返回值  
 要用作任何小数点左侧的组分隔符的区域设置特定元素。  
  
### <a name="example"></a>示例  
  请参阅 [thousands_sep](#thousands_sep) 的示例，其中虚拟成员函数由 `thousands_sep` 调用。  
  
##  <a name="frac_digits"></a>  moneypunct::frac_digits  
 可返回一个在任何小数点右侧显示的位数计数。  
  
```  
int frac_digits() const;
```  
  
### <a name="return-value"></a>返回值  
 一个在任何小数点右侧显示的区域设置特定位数计数。  
  
### <a name="remarks"></a>备注  
 此成员函数返回 [do_frac_digits](#do_frac_digits)。  
  
### <a name="example"></a>示例  
  
```cpp  
// moneypunct_frac_digits.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <sstream>  
using namespace std;  
int main( )  
{  
   locale loc( "german_germany" );  
  
   const moneypunct <char, true> &mpunct =   
       use_facet <moneypunct <char, true> >(loc);  
   for (unsigned int i = 0; i <mpunct.grouping( ).length( ); i++ )  
   {  
      cout << loc.name( ) << " international grouping:\n the "  
           << i <<"th group to the left of the radix character "  
           << "is of size " << (int)(mpunct.grouping ( )[i])   
           << endl;  
   }  
   cout << loc.name( ) << " international frac_digits\n to the right"  
        << " of the radix character: "  
        << mpunct.frac_digits ( ) << endl << endl;  
  
   const moneypunct <char, false> &mpunct2 =   
       use_facet <moneypunct <char, false> >(loc);  
   for (unsigned int i = 0; i <mpunct2.grouping( ).length( ); i++ )  
   {  
      cout << loc.name( ) << " domestic grouping:\n the "  
           << i <<"th group to the left of the radix character "  
           << "is of size " << (int)(mpunct2.grouping ( )[i])   
           << endl;  
   }  
   cout << loc.name( ) << " domestic frac_digits\n to the right"  
        << " of the radix character: "  
        << mpunct2.frac_digits ( ) << endl << endl;  
}  
```  
  
```Output  
German_Germany.1252 international grouping:  
 the 0th group to the left of the radix character is of size 3  
German_Germany.1252 international frac_digits  
 to the right of the radix character: 2  
  
German_Germany.1252 domestic grouping:  
 the 0th group to the left of the radix character is of size 3  
German_Germany.1252 domestic frac_digits  
 to the right of the radix character: 2  
```  
  
##  <a name="grouping"></a>  moneypunct::grouping  
 返回用于确定位数如何分组到任何小数点左边的区域设置特定规则。  
  
```  
string grouping() const;
```  
  
### <a name="return-value"></a>返回值  
 用于确定如何对任何小数点左侧的数字进行分组的区域设置特定规则。  
  
### <a name="remarks"></a>备注  
 此成员函数返回 [do_grouping](#do_grouping)。  
  
### <a name="example"></a>示例  
  
```cpp  
// moneypunct_grouping.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <sstream>  
using namespace std;  
int main( )  
{  
   locale loc( "german_germany" );  
  
   const moneypunct <char, true> &mpunct =   
       use_facet <moneypunct <char, true> >( loc );  
   for (unsigned int i = 0; i <mpunct.grouping( ).length( ); i++ )  
   {  
      cout << loc.name( ) << " international grouping:\n the "  
           << i <<"th group to the left of the radix character "  
           << "is of size " << (int)(mpunct.grouping ( )[i])   
           << endl;  
   }  
   cout << loc.name( ) << " international frac_digits\n to the right"  
        << " of the radix character: "  
        << mpunct.frac_digits ( ) << endl << endl;  
  
   const moneypunct <char, false> &mpunct2 =   
       use_facet <moneypunct <char, false> >( loc );  
   for (unsigned int i = 0; i <mpunct2.grouping( ).length( ); i++ )  
   {  
      cout << loc.name( ) << " domestic grouping:\n the "  
           << i <<"th group to the left of the radix character "  
           << "is of size " << (int)(mpunct2.grouping ( )[i])   
           << endl;  
   }  
   cout << loc.name( ) << " domestic frac_digits\n to the right"  
        << " of the radix character: "  
        << mpunct2.frac_digits ( ) << endl << endl;  
}  
```  
  
```Output  
German_Germany.1252 international grouping:  
 the 0th group to the left of the radix character is of size 3  
German_Germany.1252 international frac_digits  
 to the right of the radix character: 2  
  
German_Germany.1252 domestic grouping:  
 the 0th group to the left of the radix character is of size 3  
German_Germany.1252 domestic frac_digits  
 to the right of the radix character: 2  
```  
  
##  <a name="moneypunct"></a>  moneypunct::moneypunct  
 `moneypunct` 类型对象的构造函数。  
  
```  
explicit moneypunct(size_t _Refs = 0);
```  
  
### <a name="parameters"></a>参数  
 `_Refs`  
 用于指定对象的内存管理类型的整数值。  
  
### <a name="remarks"></a>备注  
 `_Refs` 参数可能的值及其含义：  
  
-   0：对象的生存期由包含该对象的区域设置管理。  
  
-   1：必须手动管理对象的生存期。  
  
-   \>1︰ 未定义这些值。  
  
 由于该析构函数受到保护，可能没有直接的示例。  
  
 构造函数通过 [locale::facet](../standard-library/locale-class.md#facet_class)(_ *Refs*) 初始化其基对象。  
  
##  <a name="neg_format"></a>  moneypunct::neg_format  
 返回一个区域设置特定规则，用于对包含负数的输出结果进行格式化。  
  
```  
pattern neg_format() const;
```  
  
### <a name="return-value"></a>返回值  
 用于格式化包含负数的输出结果的区域设置特定规则。  
  
### <a name="remarks"></a>备注  
 此成员函数返回 [do_neg_format](#do_neg_format)。  
  
### <a name="example"></a>示例  
  
```cpp  
// moneypunct_neg_format.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <sstream>  
  
using namespace std;  
  
int main( ) {  
   locale loc( "german_germany" );  
  
   const moneypunct <char, true> &mpunct =   
      use_facet <moneypunct <char, true > >(loc);  
   cout << loc.name( ) << " international negative number format: "  
        << mpunct.neg_format( ).field[0]   
        << mpunct.neg_format( ).field[1]   
        << mpunct.neg_format( ).field[2]   
        << mpunct.neg_format( ).field[3] << endl;  
  
   const moneypunct <char, false> &mpunct2 =   
      use_facet <moneypunct <char, false> >(loc);  
   cout << loc.name( ) << " domestic negative number format: "  
        << mpunct2.neg_format( ).field[0]   
        << mpunct2.neg_format( ).field[1]   
        << mpunct2.neg_format( ).field[2]   
        << mpunct2.neg_format( ).field[3] << endl;  
}  
```  
  
##  <a name="negative_sign"></a>  moneypunct::negative_sign  
 返回要用作负号符号的区域设置特定元素序列。  
  
```  
string_type negative_sign() const;
```  
  
### <a name="return-value"></a>返回值  
 返回要用作负号符号的区域设置特定元素序列。  
  
### <a name="remarks"></a>备注  
 此成员函数返回 [do_negative_sign](#do_negative_sign)。  
  
### <a name="example"></a>示例  
  
```cpp  
// moneypunct_neg_sign.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <sstream>  
  
using namespace std;  
  
int main( )  
{  
   locale loc( "german_germany" );  
  
   const moneypunct <char, true> &mpunct =   
      use_facet <moneypunct <char, true> >(loc);  
   cout << loc.name( ) << " international negative sign: "  
        << mpunct.negative_sign( ) << endl;  
  
   const moneypunct <char, false> &mpunct2 =   
      use_facet <moneypunct <char, false> >(loc);  
   cout << loc.name( ) << " domestic negative sign: "  
        << mpunct2.negative_sign( ) << endl;  
  
   locale loc2( "French" );  
  
   const moneypunct <char, true> &mpunct3 =   
      use_facet <moneypunct <char, true> >(loc2);  
   cout << loc2.name( ) << " international negative sign: "  
        << mpunct3.negative_sign( ) << endl;  
  
   const moneypunct <char, false> &mpunct4 =   
      use_facet <moneypunct <char, false> >(loc2);  
   cout << loc2.name( ) << " domestic negative sign: "  
        << mpunct4.negative_sign( ) << endl;  
};  
```  
  
```Output  
German_Germany.1252 international negative sign: -  
German_Germany.1252 domestic negative sign: -  
French_France.1252 international negative sign: -  
French_France.1252 domestic negative sign: -  
```  
  
##  <a name="pos_format"></a>  moneypunct::pos_format  
 返回一个区域设置特定规则，用于对包含正数的输出结果进行格式化。  
  
```  
pattern pos_format() const;
```  
  
### <a name="return-value"></a>返回值  
 用于格式化包含正数的输出结果的区域设置特定规则。  
  
### <a name="remarks"></a>备注  
 此成员函数返回 [do_pos_format](#do_pos_format)。  
  
### <a name="example"></a>示例  
  
```cpp  
// moneypunct_pos_format.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <sstream>  
  
using namespace std;  
  
int main() {  
   locale loc( "german_germany" );  
  
   const moneypunct <char, true> &mpunct =   
      use_facet <moneypunct <char, true> >(loc);  
   cout << loc.name( ) << " international positive number format: "  
        << mpunct.pos_format( ).field[0]   
        << mpunct.pos_format( ).field[1]   
        << mpunct.pos_format( ).field[2]   
        << mpunct.pos_format( ).field[3] << endl;  
  
   const moneypunct <char, false> &mpunct2 =   
      use_facet <moneypunct <char, false> >(loc);  
   cout << loc.name( ) << " domestic positive number format: "  
        << mpunct2.pos_format( ).field[0]   
        << mpunct2.pos_format( ).field[1]   
        << mpunct2.pos_format( ).field[2]   
        << mpunct2.pos_format( ).field[3] << endl;  
}  
```  
  
##  <a name="positive_sign"></a>  moneypunct::positive_sign  
 返回要用作正号符号的区域设置特定元素序列。  
  
```  
string_type positive_sign() const;
```  
  
### <a name="return-value"></a>返回值  
 要用作正号符号的区域设置特定元素序列。  
  
### <a name="remarks"></a>备注  
 此成员函数返回 [do_positive_sign](#do_positive_sign)。  
  
### <a name="example"></a>示例  
  
```cpp  
// moneypunct_pos_sign.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <sstream>  
  
using namespace std;  
  
int main( )  
{  
   locale loc( "german_germany" );  
  
   const moneypunct <char, true> &mpunct =   
      use_facet <moneypunct <char, true > >(loc);  
   cout << loc.name( ) << " international positive sign:"  
        << mpunct.positive_sign( ) << endl;  
  
   const moneypunct <char, false> &mpunct2 =   
      use_facet <moneypunct <char, false> >(loc);  
   cout << loc.name( ) << " domestic positive sign:"  
        << mpunct2.positive_sign( ) << endl;  
  
   locale loc2( "French" );  
  
   const moneypunct <char, true> &mpunct3 =   
      use_facet <moneypunct <char, true> >(loc2);  
   cout << loc2.name( ) << " international positive sign:"  
        << mpunct3.positive_sign( ) << endl;  
  
   const moneypunct <char, false> &mpunct4 =   
      use_facet <moneypunct <char, false> >(loc2);  
   cout << loc2.name( ) << " domestic positive sign:"  
        << mpunct4.positive_sign( ) << endl;  
};  
```  
  
```Output  
German_Germany.1252 international positive sign:  
German_Germany.1252 domestic positive sign:  
French_France.1252 international positive sign:  
French_France.1252 domestic positive sign:  
```  
  
##  <a name="string_type"></a>  moneypunct::string_type  
 一种类型，此类型描述包含 **CharType** 类型字符的字符串。  
  
```  
typedef basic_string<CharType, Traits, Allocator> string_type;  
```  
  
### <a name="remarks"></a>备注  
 此类型描述 [basic_string](../standard-library/basic-string-class.md) 模板类的专用化，该模板类的对象可存储标点序列的副本。  
  
##  <a name="thousands_sep"></a>  moneypunct::thousands_sep  
 返回要用作千位分隔符号的区域设置特定元素序列。  
  
```  
CharType thousands_sep() const;
```  
  
### <a name="return-value"></a>返回值  
 要用作千位分隔符的区域设置特定元素序列  
  
### <a name="remarks"></a>备注  
 此成员函数返回 [do_thousands_sep](#do_thousands_sep)。  
  
### <a name="example"></a>示例  
  
```cpp  
// moneypunct_thou_sep.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <sstream>  
using namespace std;  
int main( )  
{  
   locale loc( "german_germany" );  
  
   const moneypunct <char, true> &mpunct =   
       use_facet <moneypunct <char, true > >(loc);  
   cout << loc.name( ) << " international thousands separator: "  
        << mpunct.thousands_sep( ) << endl;  
  
   const moneypunct <char, false> &mpunct2 =   
      use_facet <moneypunct <char, false> >(loc);  
   cout << loc.name( ) << " domestic thousands separator: "  
        << mpunct2.thousands_sep( ) << endl << endl;  
  
   locale loc2( "english_canada" );  
  
   const moneypunct <char, true> &mpunct3 =   
       use_facet <moneypunct <char, true> >(loc2);  
   cout << loc2.name( ) << " international thousands separator: "  
        << mpunct3.thousands_sep( ) << endl;  
  
   const moneypunct <char, false> &mpunct4 =   
      use_facet <moneypunct <char, false> >(loc2);  
   cout << loc2.name( ) << " domestic thousands separator: "  
        << mpunct4.thousands_sep( ) << endl;  
}  
```  
  
```Output  
German_Germany.1252 international thousands separator: .  
German_Germany.1252 domestic thousands separator: .  
  
English_Canada.1252 international thousands separator: ,  
English_Canada.1252 domestic thousands separator: ,  
```  
  
## <a name="see-also"></a>另请参阅  
 [\<locale>](../standard-library/locale.md)   
 [C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)



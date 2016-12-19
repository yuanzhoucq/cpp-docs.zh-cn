---
title: "money_get 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "xlocmon/std::money_get"
  - "money_get"
  - "std.money_get"
  - "std::money_get"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "money_get 类"
ms.assetid: 692d3374-3fe7-4b46-8aeb-f8d91ed66b2e
caps.latest.revision: 18
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# money_get 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此模板类描述可用作区域设置 facet 的对象，此对象用于控制 `CharType` 类型序列到货币值的转换。  
  
## <a name="syntax"></a>语法  
  
```
template <class CharType, class InputIterator = istreambuf_iterator<CharType>>  
class money_get : public locale::facet;
```  
  
#### <a name="parameters"></a>参数  
 `CharType`  
 在程序中用于对区域设置中的字符进行编码的类型。  
  
 `InputIterator`  
 获取函数从中读取其输入的迭代器类型。  
  
## <a name="remarks"></a>备注  
 对于任何区域设置 facet，静态对象 ID 的初始存储值为零。 第一次尝试访问其存储的值中存储唯一正值中的 **id。**  
  
### <a name="constructors"></a>构造函数  
  
|||  
|-|-|  
|[money_get](#money_get__money_get)|用于从表示货币值的序列中提取数值的 `money_get` 类型对象的构造函数。|  
  
### <a name="typedefs"></a>Typedef  
  
|||  
|-|-|  
|[char_type](#money_get__char_type)|一种类型，此类型用于描述区域设置使用的字符。|  
|[iter_type](#money_get__iter_type)|一种类型，此类型描述输入迭代器。|  
|[string_type](#money_get__string_type)|一种类型，此类型描述包含 `CharType` 类型字符的字符串。|  
  
### <a name="member-functions"></a>成员函数  
  
|||  
|-|-|  
|[do_get](#money_get__do_get)|一种虚拟函数，通过调用此函数可从表示货币值的字符序列提取数值。|  
|[获取](#money_get__get)|从表示货币值的字符序列提取数值。|  
  
## <a name="requirements"></a>要求  
 **标头︰** \< 区域设置>  
  
 **命名空间：** std  
  
##  <a name="a-namemoneygetchartypea-moneygetchartype"></a><a name="money_get__char_type"></a>  money_get:: char_type  
 一种类型，此类型用于描述区域设置使用的字符。  
  
```
typedef CharType char_type;
```  
  
### <a name="remarks"></a>备注  
 类型是模板参数的同义词 **CharType**。  
  
##  <a name="a-namemoneygetdogeta-moneygetdoget"></a><a name="money_get__do_get"></a>  money_get:: do_get  
 虚函数调用以从表示货币值的字符序列提取数值。  
  
```
virtual iter_type do_get(iter_type first,
    iter_type last,
    bool _Intl,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long double& val) const virtual iter_type do_get(iter_type first,
    iter_type last,
    bool _Intl,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    string_type& val) const
```  
  
### <a name="parameters"></a>参数  
 `first`  
 发现会在待转换的序列开头的输入迭代器。  
  
 `last`  
 输入迭代器定址要转换的序列的末尾。  
  
 `_Intl`  
 一个布尔值，该值指示在序列中预期的货币符号的类型︰ **true** 如果国际， **false** 如果国内。  
  
 `_Iosbase`  
 一种格式标志的时设定，表示货币符号是可选的;否则，它是必需的。  
  
 `_State`  
 设置用于根据操作成功与否的流状态的相应位掩码元素。  
  
 `val`  
 一个字符串，存储的已转换的序列。  
  
### <a name="return-value"></a>返回值  
 发现超出货币输入字段的第一个元素的输入迭代器。  
  
### <a name="remarks"></a>备注  
 第一个受保护的虚拟成员函数会尝试匹配序列中的第一个位置开始的连续元素 [ `first`, ，`last`) 之前就已经取得了一套完整，nonempty 货币输入字段。 如果成功，它将转换此字段为一系列的一个或多个十进制数字，跟负号 （可选） ( `–`)，用于表示量，并将存储中的结果 [string_type](#money_get__string_type) 对象 `val`。 它将返回指定货币输入字段之外的第一个元素的迭代器。 否则，该函数存储在一个空序列 `val` 并设置 `ios_base::failbit` 中 `_State`。 它将返回指定任何前缀的有效货币输入字段之外的第一个元素的迭代器。 在任一情况下，如果返回的值等于 `last`, ，该函数设置 `ios_base::eofbit` 中 `_State`。  
  
 第二个受保护的虚拟成员函数的行为与第一个相同之处在于如果成功转换为类型的值 （可选） 有符号的数字序列 `long double` ，并将存储中的对应值 `val`。  
  
 货币输入字段的格式由 [区域设置 facet，](../standard-library/locale-class.md#facet_class)**预计完成成本** 有效调用所返回 [use_facet](../Topic/%3Clocale%3E%20functions.md#use_facet) < [moneypunct](../standard-library/moneypunct-class.md)\< **CharType**, ，**intl**>> ( **iosbase**。 [getloc](../standard-library/ios-base-class.md#ios_base__getloc))。  
  
 尤其是在下列情况下：  
  
- **预计完成成本**。 [neg_format](../standard-library/moneypunct-class.md#moneypunct__neg_format) 确定字段的组件发生的顺序。  
  
- **预计完成成本**。 [curr_symbol](../standard-library/moneypunct-class.md#moneypunct__curr_symbol) 确定构成货币符号的元素序列。  
  
- **预计完成成本**。 [positive_sign](../standard-library/moneypunct-class.md#moneypunct__positive_sign) 确定构成一个正号的元素序列。  
  
- **预计完成成本**。 [negative_sign](../standard-library/moneypunct-class.md#moneypunct__negative_sign) 确定构成负号的元素序列。  
  
- **预计完成成本**。 [分组](../standard-library/moneypunct-class.md#moneypunct__grouping) 确定位数如何分组到任何小数点左侧。  
  
- **预计完成成本**。 [thousands_sep](../standard-library/moneypunct-class.md#moneypunct__thousands_sep) 确定任何小数点左边数字进行分组的元素。  
  
- **预计完成成本**。 [decimal_point](../standard-library/moneypunct-class.md#moneypunct__decimal_point) 确定将整数位与小数位分隔的元素。  
  
- **预计完成成本**。 [frac_digits](../standard-library/moneypunct-class.md#moneypunct__frac_digits) 确定任何小数点右侧的相当多数字个数。 分析多个小数位数不是为调用与货币金额时 `frac_digits`, ，`do_get` 将停止分析后最多占用 `frac_digits` 字符。  
  
 如果登录字符串 ( **预计完成成本**。 `negative_sign` 或 **预计完成成本**。 `positive_sign`) 具有多个元素，只将第一个元素，其中匹配等于元素 **money_base::sign** 将出现在格式模式 ( **预计完成成本**。 `neg_format`). 剩余的所有元素相都匹配货币输入字段的末尾。 如果两个字符串包含货币输入字段中的下一个元素匹配的第一个元素，登录字符串均为空，并且符号为正。  
  
 如果 **iosbase**。 [标志](../standard-library/ios-base-class.md#ios_base__flags) & [showbase](../Topic/%3Cios%3E%20functions.md#showbase) 不为零，该字符串 **预计完成成本**。 `curr_symbol` 必须匹配 where 等于元素 **money_base::symbol** 将出现在格式模式。 否则为如果 **money_base::symbol** 出现在格式模式中，结束和签名字符串的任何元素都将不保留要匹配，如果未找到匹配的货币符号。 否则，（可选） 匹配的货币符号。  
  
 如果没有实例 **预计完成成本**。 `thousands_sep` 发生货币输入字段的值部分中 (其中等于元素 **money_base::value** 将出现在格式模式)，没有分组限制。 否则，任何分组约束强加 **预计完成成本**。 **分组** 强制执行。 请注意，所产生的数字序列表示一个整数，其低序位 **预计完成成本**。 `frac_digits` 小数位数是小数点右侧。  
  
 匹配任意空白区域，等于元素 **money_base::space** 出现在格式模式中，如果出现以外的格式模式的末尾。 否则，不匹配任何内部空格。 元素 *ch* 被视为空白区域，如果 [use_facet](../Topic/%3Clocale%3E%20functions.md#use_facet) < [ctype](../standard-library/ctype-class.md)\< **CharType**>> ( **iosbase**。 [getloc](../standard-library/ios-base-class.md#ios_base__getloc))。 [是](../standard-library/ctype-class.md#ctype__is)( **ctype_base::space**, ，*ch*) 是 **true**。  
  
### <a name="example"></a>示例  
  请参阅示例 [获取](#money_get__get), ，后者调用 `do_get`。  
  
##  <a name="a-namemoneygetgeta-moneygetget"></a><a name="money_get__get"></a>  money_get:: get  
 从表示货币值的字符序列提取数值。  
  
```
iter_type get(iter_type first,
    iter_type last,
    bool _Intl,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long double& val) const;

iter_type get(iter_type first,
    iter_type last,
    bool _Intl,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    string_type& val) const;
```  
  
### <a name="parameters"></a>参数  
 `first`  
 发现会在待转换的序列开头的输入迭代器。  
  
 `last`  
 输入迭代器定址要转换的序列的末尾。  
  
 `_Intl`  
 一个布尔值，该值指示在序列中预期的货币符号的类型︰ **true** 如果国际， **false** 如果国内。  
  
 `_Iosbase`  
 一种格式标志的时设定，表示货币符号是可选的;否则，它是必需  
  
 `_State`  
 设置用于根据操作是否成功的流状态的相应位掩码元素。  
  
 `val`  
 一个字符串，存储的已转换的序列。  
  
### <a name="return-value"></a>返回值  
 发现超出货币输入字段的第一个元素的输入迭代器。  
  
### <a name="remarks"></a>备注  
 两个成员函数返回 [do_get](#money_get__do_get)( `first``,` `last``,` `_Intl`, ，`_Iosbase`, ，`_State`, ，`val`)。  
  
### <a name="example"></a>示例  
  
```  
// money_get_get.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <sstream>  
using namespace std;  
  
int main( )  
{  
   locale loc( "german_germany" );  
  
   basic_stringstream< char > psz;  
   psz << use_facet<moneypunct<char, 1> >(loc).curr_symbol() << "-1.000,56";  
   basic_stringstream< char > psz2;  
   psz2 << "-100056" << use_facet<moneypunct<char, 1> >(loc).curr_symbol();  
  
   ios_base::iostate st = 0;  
   long double fVal;  
  
   psz.flags( psz.flags( )|ios_base::showbase );   
   // Which forced the READING the currency symbol  
   psz.imbue(loc);  
   use_facet < money_get < char > >( loc ).  
      get( basic_istream<char>::_Iter( psz.rdbuf( ) ),     
           basic_istream<char>::_Iter( 0 ), true, psz, st, fVal );  
  
   if ( st & ios_base::failbit )  
      cout << "money_get(" << psz.str( ) << ", intl = 1) FAILED"  
           << endl;  
   else  
      cout << "money_get(" << psz.str( ) << ", intl = 1) = "   
           << fVal/100.0 << endl;  
  
   use_facet < money_get < char > >( loc ).  
      get(basic_istream<char>::_Iter(psz2.rdbuf( )),     
          basic_istream<char>::_Iter(0), false, psz2, st, fVal);  
  
   if ( st & ios_base::failbit )  
      cout << "money_get(" << psz2.str( ) << ", intl = 0) FAILED"   
           << endl;  
   else  
      cout << "money_get(" << psz2.str( ) << ", intl = 0) = "   
           << fVal/100.0 << endl;  
};  
```  
  
##  <a name="a-namemoneygetitertypea-moneygetitertype"></a><a name="money_get__iter_type"></a>  money_get:: iter_type  
 一种类型，此类型描述输入迭代器。  
  
```
typedef InputIterator iter_type;
```  
  
### <a name="remarks"></a>备注  
 类型是模板参数的同义词 **InputIterator**。  
  
##  <a name="a-namemoneygetmoneygeta-moneygetmoneyget"></a><a name="money_get__money_get"></a>  money_get:: money_get  
 用于从表示货币值的序列中提取数值的 `money_get` 类型对象的构造函数。  
  
```
explicit money_get(size_t _Refs = 0);
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
  
 构造函数初始化与与其基对象 **区域设置::**[方面](../standard-library/locale-class.md#facet_class)( **_***Refs*)。  
  
##  <a name="a-namemoneygetstringtypea-moneygetstringtype"></a><a name="money_get__string_type"></a>  money_get:: string_type  
 该类型描述包含类型的字符的字符串 **CharType**。  
  
```
typedef basic_string<CharType, Traits, Allocator> string_type;
```  
  
### <a name="remarks"></a>备注  
 此类型描述模板类的专用化 [basic_string](../standard-library/basic-string-class.md)。  
  
## <a name="see-also"></a>另请参阅  
 [\< 区域设置>](../standard-library/locale.md)   
 [facet 类](../standard-library/locale-class.md#facet_class)   
 [C + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)




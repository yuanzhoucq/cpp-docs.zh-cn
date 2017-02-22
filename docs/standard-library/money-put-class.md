---
title: "money_put 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::money_put"
  - "xlocmon/std::money_put"
  - "money_put"
  - "std.money_put"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "money_put 类"
ms.assetid: f439fd56-c9b1-414c-95e1-66c918c6eee6
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# money_put 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此模板类描述一个对象来充当区域设置 facet，以便控制货币值向 `CharType` 类型序列的转换。  
  
## <a name="syntax"></a>语法  
  
```  
template <class CharType,  
    class OutputIterator = ostreambuf_iterator<CharType>>  
class money_put : public locale::facet;  
```  
  
#### <a name="parameters"></a>参数  
 `CharType`  
 在程序中用于对区域设置中的字符进行编码的类型。  
  
 `OutputIterator`  
 供货币放置函数写入其输出结果的迭代器类型。  
  
## <a name="remarks"></a>备注  
 对于任何区域设置 facet，静态对象 ID 的初始存储值为零。 第一次尝试访问其存储的值中存储唯一正值中的 **id。**  
  
### <a name="constructors"></a>构造函数  
  
|||  
|-|-|  
|[money_put](#money_put__money_put)|`money_put` 类型的对象的构造函数。|  
  
### <a name="typedefs"></a>Typedef  
  
|||  
|-|-|  
|[char_type](#money_put__char_type)|一种类型，此类型用于描述区域设置使用的字符。|  
|[iter_type](#money_put__iter_type)|一种类型，此类型描述输出迭代器。|  
|[string_type](#money_put__string_type)|一种类型，此类型描述包含 `CharType` 类型字符的字符串。|  
  
### <a name="member-functions"></a>成员函数  
  
|||  
|-|-|  
|[do_put](#money_put__do_put)|一种虚拟函数，通过调用此函数可将数字或字符串转换为表示货币值的字符序列。|  
|[放置](#money_put__put)|将数字或字符串转换为表示货币值的字符序列。|  
  
## <a name="requirements"></a>要求  
 **标头︰** \< 区域设置>  
  
 **命名空间：** std  
  
##  <a name="a-namemoneyputchartypea-moneyputchartype"></a><a name="money_put__char_type"></a>  money_put:: char_type  
 一种类型，此类型用于描述区域设置使用的字符。  
  
```  
typedef CharType char_type;  
```  
  
### <a name="remarks"></a>备注  
 类型是模板参数的同义词 **CharType**。  
  
##  <a name="a-namemoneyputdoputa-moneyputdoput"></a><a name="money_put__do_put"></a>  money_put:: do_put  
 一种虚拟函数，通过调用此函数可将数字或字符串转换为表示货币值的字符序列。  
  
```  
virtual iter_type do_put(
    iter_type next,   
    bool _Intl,   
    ios_base& _Iosbase,  
    CharType _Fill,   
    const string_type& val) const;

 
virtual iter_type do_put(
    iter_type next,   
    bool _Intl,   
    ios_base& _Iosbase,  
    CharType _Fill,  
    long double val) const;
```  
  
### <a name="parameters"></a>参数  
 ` next`  
 发现插入的字符串的第一个元素的迭代器。  
  
 `_Intl`  
 一个布尔值，该值指示在序列中预期的货币符号的类型︰ **true** 如果国际， **false** 如果国内。  
  
 `_Iosbase`  
 一种格式标志的时设定，表示货币符号是可选的;否则，它是必需  
  
 `_Fill`  
 出现用于调整间距的字符。  
  
 ` val`  
 要转换的字符串对象。  
  
### <a name="return-value"></a>返回值  
 输出迭代器的地址超出最后一个元素的位置生成。  
  
### <a name="remarks"></a>备注  
 第一个受保护的虚拟成员函数生成开始的连续元素 ` next` 以生成从货币输出字段 [string_type](#money_put__string_type) 对象 ` val`。 通过控制的序列 ` val` 必须以一个或多个十进制数字，跟表示的工作量负号 （-），（可选）。 该函数返回指定生成的货币输出字段之外的第一个元素的迭代器。  
  
 第二个受保护的虚拟成员函数的行为与第一个相同除非它有效地第一个转换 ` val` 到序列中的十进制数，再跟一个减号，（可选） 然后，将序列转换为更高版本。  
  
 货币输出字段的格式由 [区域设置 facet，](../standard-library/locale-class.md#facet_class) （有效） 的调用所返回的预计完成成本 [use_facet](../Topic/%3Clocale%3E%20functions.md#use_facet) < [moneypunct](../standard-library/moneypunct-class.md)\< **CharType**, ，**intl**>> ( **iosbase**。 [getloc](../standard-library/ios-base-class.md#ios_base__getloc))。  
  
 尤其是在下列情况下：  
  
- **预计完成成本**。 [pos_format](../standard-library/moneypunct-class.md#moneypunct__pos_format) 确定在其中的字段的组件生成的非负数值的顺序。  
  
- **预计完成成本**。 [neg_format](../standard-library/moneypunct-class.md#moneypunct__neg_format) 确定在其中的字段的组件生成的值为负的顺序。  
  
- **预计完成成本**。 [curr_symbol](../standard-library/moneypunct-class.md#moneypunct__curr_symbol) 确定要生成的货币符号的元素序列。  
  
- **预计完成成本**。 [positive_sign](../standard-library/moneypunct-class.md#moneypunct__positive_sign) 确定要为正号生成的元素序列。  
  
- **预计完成成本**。 [negative_sign](../standard-library/moneypunct-class.md#moneypunct__negative_sign) 确定要为负号生成的元素序列。  
  
- **预计完成成本**。 [分组](../standard-library/moneypunct-class.md#moneypunct__grouping) 确定位数如何分组到任何小数点左侧。  
  
- **预计完成成本**。 [thousands_sep](../standard-library/moneypunct-class.md#moneypunct__thousands_sep) 确定任何小数点左边数字进行分组的元素。  
  
- **预计完成成本**。 [decimal_point](../standard-library/moneypunct-class.md#moneypunct__decimal_point) 确定将整数位与任何小数位分隔的元素。  
  
- **预计完成成本**。 [frac_digits](../standard-library/moneypunct-class.md#moneypunct__frac_digits) 确定任何小数点右侧的相当多数字个数。  
  
 如果登录字符串 ( **预计完成成本**。 `negative_sign` 或 **预计完成成本**。 `positive_sign`) 具有多个元素，只将第一个元素位置生成等于元素 **money_base::sign** 将出现在格式模式 ( **预计完成成本**。 `neg_format` 或 **预计完成成本**。 `pos_format`). 剩余的所有元素将都生成在货币输出字段的末尾。  
  
 如果 **iosbase**。 [标志](../standard-library/ios-base-class.md#ios_base__flags) & [showbase](../Topic/%3Cios%3E%20functions.md#showbase) 不为零，该字符串 **预计完成成本**。 `curr_symbol` 其中生成该元素等同于 **money_base::symbol** 将出现在格式模式。 否则，将生成不带货币符号。  
  
 如果没有分组约束所规定的 **预计完成成本**。 **分组** （其第一个元素具有值 CHAR_MAX），然后没有实例 **预计完成成本**。 `thousands_sep` 在货币输出字段的值部分中生成 (其中等于元素 **money_base::value** 将出现在格式模式)。 如果 **预计完成成本**。 `frac_digits` 是零，则不实例 **预计完成成本**。 `decimal_point` 将生成后的十进制数字。 否则，生成的货币输出字段将置于低序位 **预计完成成本**。 `frac_digits` 小数点右侧的十进制数字。  
  
 对于任何数字输出字段，但是如果发生填充 **iosbase**。 **标志** & **iosbase**。 [内部](../Topic/%3Cios%3E%20functions.md#internal) 为非零、 所有内部填充其中生成等于元素 **money_base::space** 如果出现该对话框将出现在格式模式。 否则，内部填充发生之前生成的序列。 填充字符是 **填充**。  
  
 函数调用 **iosbase**。 **宽度**(0) 可将字段宽度重置为零。  
  
### <a name="example"></a>示例  
  请参阅示例 [放](#money_put__put), ，其中的虚拟成员函数将由 **放**。  
  
##  <a name="a-namemoneyputitertypea-moneyputitertype"></a><a name="money_put__iter_type"></a>  money_put:: iter_type  
 一种类型，此类型描述输出迭代器。  
  
```  
typedef OutputIterator iter_type;  
```  
  
### <a name="remarks"></a>备注  
 类型是模板参数的同义词 **OutputIterator。**  
  
##  <a name="a-namemoneyputmoneyputa-moneyputmoneyput"></a><a name="money_put__money_put"></a>  money_put:: money_put  
 `money_put` 类型的对象的构造函数。  
  
```  
explicit money_put(size_t _Refs = 0);
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
  
##  <a name="a-namemoneyputputa-moneyputput"></a><a name="money_put__put"></a>  money_put:: put  
 将数字或字符串转换为表示货币值的字符序列。  
  
```  
iter_type put(
    iter_type next,   
    bool _Intl,   
    ios_base& _Iosbase,  
    CharType _Fill,   
    const string_type& val) const;

 
iter_type put(
    iter_type next,   
    bool _Intl,   
    ios_base& _Iosbase,  
    CharType _Fill,  
    long double val) const;
```  
  
### <a name="parameters"></a>参数  
 ` next`  
 发现插入的字符串的第一个元素的迭代器。  
  
 `_Intl`  
 一个布尔值，该值指示在序列中预期的货币符号的类型︰ **true** 如果国际， **false** 如果国内。  
  
 `_Iosbase`  
 一种格式标志的时设定，表示货币符号是可选的;否则，它是必需  
  
 `_Fill`  
 出现用于调整间距的字符。  
  
 ` val`  
 要转换的字符串对象。  
  
### <a name="return-value"></a>返回值  
 输出迭代器的地址超出最后一个元素的位置生成。  
  
### <a name="remarks"></a>备注  
 两个成员函数返回 [do_put](#money_put__do_put)( ` next`, ，`_Intl`, ，`_Iosbase`, ，`_Fill`, ，` val`)。  
  
### <a name="example"></a>示例  
  
```  
// money_put_put.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <sstream>  
using namespace std;  
int main( )  
{  
//   locale loc( "german_germany" );  
   locale loc( "english_canada" );  
   basic_stringstream<char> psz, psz2;  
   ios_base::iostate st = 0;  
  
   psz2.imbue( loc );  
   psz2.flags( psz2.flags( )|ios_base::showbase ); // force the printing of the currency symbol  
   use_facet < money_put < char > >(loc).put(basic_ostream<char>::_Iter( psz2.rdbuf( ) ), true, psz2, st, 100012);  
   if (st & ios_base::failbit)  
      cout << "money_put( ) FAILED" << endl;  
   else  
      cout << "money_put( ) = \"" << psz2.rdbuf( )->str( ) <<"\""<< endl;     
  
   st = 0;  
};  
```  
  
```Output  
money_put( ) = "CAD1,000.12"  
```  
  
##  <a name="a-namemoneyputstringtypea-moneyputstringtype"></a><a name="money_put__string_type"></a>  money_put:: string_type  
 该类型描述包含类型的字符的字符串 **CharType**。  
  
```  
typedef basic_string<CharType, Traits, Allocator> string_type;  
```  
  
### <a name="remarks"></a>备注  
 此类型描述模板类的专用化 [basic_string](../standard-library/basic-string-class.md) 其对象可存储的源序列中的元素序列。  
  
## <a name="see-also"></a>另请参阅  
 [\< 区域设置>](../standard-library/locale.md)   
 [facet 类](../standard-library/locale-class.md#facet_class)   
 [C + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)


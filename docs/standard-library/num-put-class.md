---
title: "num_put 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::num_put"
  - "xlocnum/std::num_put"
  - "num_put"
  - "std.num_put"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "num_put 类"
ms.assetid: 36c5bffc-8283-4201-8ed4-78c4d81f8a17
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# num_put 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

一种模板类，用于描述一个对象来充当区域设置 facet，以便控制数值向 `CharType` 类序列的转换。  
  
## <a name="syntax"></a>语法  
  
```  
template <class CharType,  
    class OutputIterator = ostreambuf_iterator<CharType>>  
class num_put : public locale::facet;  
```  
  
#### <a name="parameters"></a>参数  
 `CharType`  
 在程序中用于对区域设置中的字符进行编码的类型。  
  
 `OutputIterator`  
 数值输出函数将其输出写入到的迭代器的类型。  
  
## <a name="remarks"></a>备注  
 对于任何区域设置 facet，静态对象 ID 的初始存储值为零。 第一次尝试访问其存储的值中存储唯一正值中的 **id。**  
  
### <a name="constructors"></a>构造函数  
  
|||  
|-|-|  
|[num_put](#num_put__num_put)|`num_put` 类型的对象的构造函数。|  
  
### <a name="typedefs"></a>Typedef  
  
|||  
|-|-|  
|[char_type](#num_put__char_type)|一种类型，此类型用于描述区域设置使用的字符。|  
|[iter_type](#num_put__iter_type)|一种类型，此类型描述输出迭代器。|  
  
### <a name="member-functions"></a>成员函数  
  
|||  
|-|-|  
|[do_put](#num_put__do_put)|一种虚拟函数，通过调用此函数可将数字转换为 `CharType` 序列以表示针对给定区域设置而设置格式的数字。|  
|[放置](#num_put__put)|将数字转换为 `CharType` 序列以表示针对给定区域设置而设置格式的数字。|  
  
## <a name="requirements"></a>要求  
 **标头︰** \< 区域设置>  
  
 **命名空间：** std  
  
##  <a name="a-namenumputchartypea-numputchartype"></a><a name="num_put__char_type"></a>  num_put:: char_type  
 一种类型，此类型用于描述区域设置使用的字符。  
  
```  
typedef CharType char_type;  
```  
  
### <a name="remarks"></a>备注  
 类型是模板参数的同义词 **CharType**。  
  
##  <a name="a-namenumputdoputa-numputdoput"></a><a name="num_put__do_put"></a>  num_put:: do_put  
 虚函数调用以将数字转换为一个序列的 **CharType**s 表示数字格式，以便按照给定区域设置。  
  
```  
virtual iter_type do_put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    bool val) const;

 
virtual iter_type do_put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    long val) const;

 
virtual iter_type do_put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    unsigned long val) const;

 
virtual iter_type do_put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    double val) const;

 
virtual iter_type do_put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    long double val) const;

 
virtual iter_type do_put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    const void* val) const;

 
virtual iter_type do_put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    const long long val) const;

virtual iter_type do_put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    const unsigned long long val) const;
```  
  
### <a name="parameters"></a>参数  
 ` next`  
 发现插入的字符串的第一个元素的迭代器。  
  
 `_Iosbase`  
 指定与用于放下输出并设置输出格式标志 numpunct 方面包含区域设置的流。  
  
 `_Fill`  
 一个用于调整间距的字符。  
  
 ` val`  
 数字或布尔值将是输出的类型。  
  
### <a name="return-value"></a>返回值  
 输出迭代器的地址超出最后一个元素的位置生成。  
  
### <a name="remarks"></a>备注  
 第一个受保护的虚拟成员函数生成开始的连续元素 ` next` 以生成整数输出字段的值从 ` val`。 该函数返回指定的下一个位置的迭代器插入一个元素之外生成的整数输出字段。  
  
 打印功能用于生成一系列的相同规则生成整数输出字段 `char` 到文件的元素。 假定每个这样的 char 元素映射到等效类型的元素 **CharType** 由简单的一对一映射。 如果打印功能来填充一个字段用空格或数字 0，但是， `do_put` 改为使用 **填充**。 确定等效的打印转换规格，如下所示︰  
  
-   如果 **iosbase**。 [标志](../standard-library/ios-base-class.md#ios_base__flags) & `ios_base::basefield` == `ios_base::`[oct](../Topic/%3Cios%3E%20functions.md#oct), ，转换规格是 **lo**。  
  
-   如果 **iosbase.flags** & **ios_base::basefield** == `ios_base::`[十六进制](../Topic/%3Cios%3E%20functions.md#hex), ，转换规格是 **lx**。  
  
-   否则，转换规格是 **ld**。  
  
 如果 **iosbase**。 [宽度](../standard-library/ios-base-class.md#ios_base__width) 为非零值，此值的字段宽度预置。 然后，该函数调用 **iosbase**。 **宽度**(0) 可将字段宽度重置为零。  
  
 填充时才出现的最小的元素数 *N* 必须以指定的输出字段小于 **iosbase**。 [宽度](../standard-library/ios-base-class.md#ios_base__width)。 此类填充由一系列的 *N* – **宽度** 份 **填充**。 然后填充出现，如下所示︰  
  
-   如果 **iosbase**。 **标志** & `ios_base::adjustfield` == `ios_base::`[左](../Topic/%3Cios%3E%20functions.md#left), ，该标志 **–** 预置。 （填充在生成的文本后发生。）  
  
-   如果 **iosbase.flags** & **ios_base::adjustfield** == `ios_base::`[内部](../Topic/%3Cios%3E%20functions.md#internal), ，该标志 **0** 预置。 （对于数值输出字段，填充进行打印的功能以 0 填充的位置。）  
  
-   否则，不预先任何其他标志。 （填充在生成的序列之前发生。）  
  
 最后︰  
  
-   如果 **iosbase**。 **标志** & `ios_base::`[showpos](../Topic/%3Cios%3E%20functions.md#showpos) 不为零，该标志 **+** 预置到转换规格。  
  
-   如果 **iosbase**。 **标志** & **ios_base::**[showbase](../Topic/%3Cios%3E%20functions.md#showbase) 不为零，该标志 **#** 预置到转换规格。  
  
 一个整数的格式输出字段进一步由 [区域设置 facet，](../standard-library/locale-class.md#facet_class)**预计完成成本** 调用所返回 [use_facet](../Topic/%3Clocale%3E%20functions.md#use_facet) < [numpunct](../standard-library/numpunct-class.md)\< **Elem**> ( **iosbase**。 [getloc](../standard-library/ios-base-class.md#ios_base__getloc))。 尤其是在下列情况下：  
  
- **预计完成成本**。 [分组](../standard-library/numpunct-class.md#numpunct__grouping) 确定位数如何分组到任何小数点左边  
  
- **预计完成成本**。 [thousands_sep](../standard-library/numpunct-class.md#numpunct__thousands_sep) 确定任何小数点左边数字进行分组的序列  
  
 如果没有分组约束所规定的 **预计完成成本**。 **分组** （其第一个元素具有值 CHAR_MAX），然后没有实例 **预计完成成本**。 `thousands_sep` 在输出字段中生成。 否则，插入一个分隔符后进行打印的转换。  
  
 第二个受保护的虚拟成员函数︰  
  
```  
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,  
    CharType _Fill,
    unsigned long val) const;
```  
  
 行为与第一个相同，只不过它将替换为转换规格的 **ld** 与 **lu**。  
  
 第三个受保护的虚拟成员函数中︰  
  
```  
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,  
    CharType _Fill,
    double val) const;
```  
  
 行为与第一个相同，只不过它将生成一个从值的浮点输出字段 **val**。 **预计完成成本**。 [decimal_point](../standard-library/numpunct-class.md#numpunct__decimal_point) 确定将整数位与小数位分隔的序列。 确定等效的打印转换规格，如下所示︰  
  
-   如果 **iosbase**。 **标志** & `ios_base::floatfield` == `ios_base::`[固定](../Topic/%3Cios%3E%20functions.md#fixed), ，转换规格是 **lf**。  
  
-   如果 **iosbase**。 **标志** & **ios_base::floatfield** == `ios_base::`[科学记数法](../Topic/%3Cios%3E%20functions.md#scientific), ，转换规格是 `le`。 如果 **iosbase**。 **标志** & `ios_base::`[大写](../Topic/%3Cios%3E%20functions.md#uppercase) 不为零， **e** 将替换为 **E**。  
  
-   否则，转换规格是 **lg**。 如果 **iosbase**。 **标志** & **ios_base::uppercase** 不为零， **g** 将替换为 **G**。  
  
 如果 **iosbase**。 **标志** & **ios_base::fixed** 不为零或者，如果 **iosbase**。 [精度](../standard-library/ios-base-class.md#ios_base__precision) 是大于零，具有值的精度 **iosbase**。 **精度** 预置到转换规格。 任何填充的行为与整数输出字段相同。 填充字符是 **填充**。 最后︰  
  
-   如果 **iosbase**。 **标志** & `ios_base::`[showpos](../Topic/%3Cios%3E%20functions.md#showpos) 不为零，该标志 **+** 预置到转换规格。  
  
-   如果 **iosbase**。 **标志** & `ios_base::`[showpoint](../Topic/%3Cios%3E%20functions.md#showpoint) 不为零，该标志 **#** 预置到转换规格。  
  
 第四个受保护的虚拟成员函数︰  
  
```  
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,  
    CharType _Fill,
    long double val) const;
```  
  
 具有相同的行为第三个不同之处在于该限定符 **l** 在转换过程中替换规范 **L**。  
  
 第五个的受保护的虚拟成员函数︰  
  
```  
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,  
    CharType _Fill,
    const void* val) const;
```  
  
 唯一的差别在于转换规格的行为相同第一、 `p`**,，** 加上指定填充所需的任何限定符。  
  
 第六个受保护的虚拟成员函数︰  
  
```  
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,  
    CharType _Fill,
    bool val) const;
```  
  
 之处在于它会生成一个从的布尔值的输出字段的行为与第一个相同 ` val`。  
  
 一个布尔值的输出字段采用两种形式之一。 如果 **iosbase**。 **标志** & `ios_base::`[boolalpha](../Topic/%3Cios%3E%20functions.md#boolalpha) 是 **false**, ，成员函数将返回 `do_put`(_ *下一步*, ，\_ *Iosbase*, ，\_ *填充*, ，( **长**) ` val`)，这通常产生生成的序列的任一 0 (对于 **false**) 或 1 (为 **，则返回 true**)。 否则，生成的序列是 **预计完成成本**。 [falsename](../standard-library/numpunct-class.md#numpunct__falsename)`)` (对于 **false**)，或 **预计完成成本**。 [truename](../standard-library/numpunct-class.md#numpunct__truename) (对于 **true**)。  
  
 第七个受保护的虚拟成员函数︰  
  
```  
virtual iter_type do_put(iter_type next,
    ios_base& iosbase,  
    Elem fill,
    long long val) const;
```  
  
 行为与第一个相同，只不过它将替换为转换规格的 **ld** 与 **lld**。  
  
 第八个受保护的虚拟成员函数︰  
  
```  
virtual iter_type do_put(iter_type next,
    ios_base& iosbase,  
    Elem fill,
    unsigned long long val) const;
```  
  
 行为与第一个相同，只不过它将替换为转换规格的 `ld` 与 `llu`。  
  
### <a name="example"></a>示例  
  请参阅示例 [放](#num_put__put), ，后者调用 `do_put`。  
  
##  <a name="a-namenumputitertypea-numputitertype"></a><a name="num_put__iter_type"></a>  num_put:: iter_type  
 一种类型，此类型描述输出迭代器。  
  
```  
typedef OutputIterator iter_type;  
```  
  
### <a name="remarks"></a>备注  
 类型是模板参数的同义词 **OutputIterator。**  
  
##  <a name="a-namenumputnumputa-numputnumput"></a><a name="num_put__num_put"></a>  num_put:: num_put  
 `num_put` 类型的对象的构造函数。  
  
```  
explicit num_put(size_t _Refs = 0);
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
  
 构造函数初始化与与其基对象 **区域设置::**[方面](../standard-library/locale-class.md#facet_class)(_ *Refs*)。  
  
##  <a name="a-namenumputputa-numputput"></a><a name="num_put__put"></a>  num_put:: put  
 将数字转换为一个序列的 **CharType**s 表示数字格式，以便按照给定区域设置。  
  
```  
iter_type put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    bool val) const;

 
iter_type put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    long val) const;

 
iter_type put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    unsigned long val) const;

 
iter_type put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    Long long val) const;

 
iter_type put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    Unsigned long long val) const;

 
 
iter_type put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    double val) const;

 
iter_type put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    long double val) const;

 
iter_type put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    const void* val) const;
```  
  
### <a name="parameters"></a>参数  
 ` dest`  
 发现插入的字符串的第一个元素的迭代器。  
  
 `_Iosbase`  
 指定与用于放下输出并设置输出格式标志 numpunct 方面包含区域设置的流。  
  
 `_Fill`  
 一个用于调整间距的字符。  
  
 ` val`  
 数字或布尔值将是输出的类型。  
  
### <a name="return-value"></a>返回值  
 输出迭代器的地址超出最后一个元素的位置生成。  
  
### <a name="remarks"></a>备注  
 所有成员函数都返回 [do_put](#num_put__do_put)( ` next`, ，`_Iosbase`, ，`_Fill`, ，` val`)。  
  
### <a name="example"></a>示例  
  
```  
// num_put_put.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <sstream>  
using namespace std;  
int main( )  
{  
   locale loc( "german_germany" );  
   basic_stringstream<char> psz2;  
   ios_base::iostate st = 0;  
   long double fVal;  
   cout << "The thousands separator is: "   
        << use_facet < numpunct <char> >(loc).thousands_sep( )   
        << endl;  
  
   psz2.imbue( loc );  
   use_facet < num_put < char > >  
      ( loc ).put(basic_ostream<char>::_Iter(psz2.rdbuf( ) ),  
                    psz2, ' ', fVal=1000.67);  
  
   if ( st & ios_base::failbit )  
      cout << "num_put( ) FAILED" << endl;  
   else  
      cout << "num_put( ) = " << psz2.rdbuf( )->str( ) << endl;  
}  
```  
  
```Output  
The thousands separator is: .  
num_put( ) = 1.000,67  
```  
  
## <a name="see-also"></a>另请参阅  
 [\< 区域设置>](../standard-library/locale.md)   
 [facet 类](../standard-library/locale-class.md#facet_class)   
 [C + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)


---
title: "num_put 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- xlocnum/std::num_put
- locale/std::num_put::char_type
- locale/std::num_put::iter_type
- locale/std::num_put::do_put
- locale/std::num_put::put
dev_langs: C++
helpviewer_keywords:
- std::num_put [C++]
- std::num_put [C++], char_type
- std::num_put [C++], iter_type
- std::num_put [C++], do_put
- std::num_put [C++], put
ms.assetid: 36c5bffc-8283-4201-8ed4-78c4d81f8a17
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d3870564e7374d4e3faba9bc2055f04e9d2f4b63
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="numput-class"></a>num_put 类
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
 对于任何区域设置 facet，静态对象 ID 的初始存储值为零。 首次尝试访问其存储值后，将在 **ID** 中存储唯一正值。  
  
### <a name="constructors"></a>构造函数  
  
|||  
|-|-|  
|[num_put](#num_put)|`num_put` 类型的对象的构造函数。|  
  
### <a name="typedefs"></a>Typedef  
  
|||  
|-|-|  
|[char_type](#char_type)|一种类型，此类型用于描述区域设置使用的字符。|  
|[iter_type](#iter_type)|一种类型，此类型描述输出迭代器。|  
  
### <a name="member-functions"></a>成员函数  
  
|||  
|-|-|  
|[do_put](#do_put)|一种虚拟函数，通过调用此函数可将数字转换为 `CharType` 序列以表示针对给定区域设置而设置格式的数字。|  
|[put](#put)|将数字转换为 `CharType` 序列以表示针对给定区域设置而设置格式的数字。|  
  
## <a name="requirements"></a>要求  
 **标头：**\<locale>  
  
 **命名空间：** std  
  
##  <a name="char_type"></a>  num_put::char_type  
 一种类型，此类型用于描述区域设置使用的字符。  
  
```  
typedef CharType char_type;  
```  
  
### <a name="remarks"></a>备注  
 该类型是模板参数 **CharType** 的同义词。  
  
##  <a name="do_put"></a>  num_put::do_put  
 一种虚拟函数，通过调用此函数可将数字转换为 **CharType** 序列以表示针对给定区域设置而设置格式的数字。  
  
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
 `next`  
 发现插入的字符串中第一个元素的迭代器。  
  
 `_Iosbase`  
 指定包含区域设置的流，以及用于向输出和标志加标点以便对输出进行格式设置的 numpunct facet。  
  
 `_Fill`  
 用于调整间距的字符。  
  
 `val`  
 将输出的数字或布尔类型。  
  
### <a name="return-value"></a>返回值  
 发现超出生成的最后一个元素的位置的输出迭代器。  
  
### <a name="remarks"></a>备注  
 第一个受保护的虚拟成员函数生成以 `next` 开始的连续元素，以便从 `val` 的值生成整数输出字段。 该函数返回一个迭代器，指定生成的整数输出字段外下一个要插入元素的位置。  
  
 使用 print 函数在文件中生成一系列 `char` 元素所用的规则来生成整数输入字段。 假定将每个这样的 char 元素通过简单的、一对一的映射映射到 **CharType** 类型的等效元素。 其中 print 函数使用空格或数字 0 来填充字段，但是，`do_put` 将代替使用 **fill**。 确定等效的打印转换规格，如下所示：  
  
-   如果 **iosbase**. [flags](../standard-library/ios-base-class.md#flags) & `ios_base::basefield` == `ios_base::`[oct](../standard-library/ios-functions.md#oct)，则转换规格为 **lo**。  
  
-   如果 **iosbase.flags** & **ios_base::basefield** == `ios_base::`[hex](../standard-library/ios-functions.md#hex)，则转换规格为 **lx**。  
  
-   否则，转换规格为 **ld**。  
  
 如果 **iosbase**. [width](../standard-library/ios-base-class.md#width) 为非零值，则将预置此值的字段宽度。 然后，该函数将调用 **iosbase**. **width**(0) 以便将字段宽度重置为零。  
  
 发生填充的条件仅限于指定输出字段所需的元素 *N* 的最小数小于 **iosbase**. [width](../standard-library/ios-base-class.md#width)。 此类填充的序列组成*N* - **宽度**份**填充**。 然后将出现填充，如下所示：  
  
-   如果 **iosbase**. **标志** & `ios_base::adjustfield` == `ios_base::`[左](../standard-library/ios-functions.md#left)，标志 **-** 前面预置。 （将在生成的文本后出现填充。）  
  
-   如果 **iosbase.flags** & **ios_base::adjustfield** == `ios_base::`[internal](../standard-library/ios-functions.md#internal)，则将预置标志 **0**。 （对于数值输出字段，将在以 0 填充 print 函数的位置出现填充。）  
  
-   否则，不会预置任何其他标志。 （在生成的序列之前出现填充。）  
  
 最后：  
  
-   如果 **iosbase**. **flags** & `ios_base::`[showpos](../standard-library/ios-functions.md#showpos) 不为零，则将标志 **+** 预置到转换规格。  
  
-   如果 **iosbase**. **flags** & **ios_base::**[showbase](../standard-library/ios-functions.md#showbase) 不为零，则将标志 **#** 预置到转换规格。  
  
 整数输出字段的格式由 [locale facet](../standard-library/locale-class.md#facet_class)**fac** 进一步确定，后者又由调用 [use_facet](../standard-library/locale-functions.md#use_facet) < [numpunct](../standard-library/numpunct-class.md)\< **Elem**>( **iosbase**. [getloc](../standard-library/ios-base-class.md#getloc)) 返回。 尤其是在下列情况下：  
  
- **fac**. [grouping](../standard-library/numpunct-class.md#grouping) 确定如何对任何小数点左侧的数字进行分组  
  
- **fac**. [thousands_sep](../standard-library/numpunct-class.md#thousands_sep) 确定将任何小数点左侧的数字进行分组的序列  
  
 如果 **fac**. **grouping** 未采用任何分组约束（其首个元素具有值 CHAR_MAX），则 **fac**. `thousands_sep` 的任何实例都不会在输出字段中生成。 否则，将在出现打印转换后插入分隔符。  
  
 第二个受保护的虚拟成员函数：  
  
```  
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,  
    CharType _Fill,
    unsigned long val) const;
```  
  
 行为与第一个相同，只不过它将转换规格 **ld** 替换为 **lu**。  
  
 第三个受保护的虚拟成员函数：  
  
```  
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,  
    CharType _Fill,
    double val) const;
```  
  
 行为与第一个相同，只不过它从 **val** 值生成一个浮点输出字段。 **fac**. [decimal_point](../standard-library/numpunct-class.md#decimal_point) 确定从小数位分隔整数位的序列。 确定等效的打印转换规格，如下所示：  
  
-   如果 **iosbase**. **flags** & `ios_base::floatfield` == `ios_base::`[fixed](../standard-library/ios-functions.md#fixed)，则转换规格为 **lf**。  
  
-   如果 **iosbase**. **flags** & **ios_base::floatfield** == `ios_base::`[scientific](../standard-library/ios-functions.md#scientific)，则转换规格为 `le`。 如果 **iosbase**. **flags** & `ios_base::`[uppercase](../standard-library/ios-functions.md#uppercase) 不为零，则 **e** 将被替换为 **E**。  
  
-   否则，转换规格为 **lg**。 如果 **iosbase**. **flags** & **ios_base::uppercase** 不为零，则 **g** 将被替换为 **G**。  
  
 如果 **iosbase**. **flags** & **ios_base::fixed** 不为零或者如果 **iosbase**. [precision](../standard-library/ios-base-class.md#precision) 大于零，则具有值 **iosbase**. **precision** 的精度将被预置到转换规格。 任何填充行为与整数输出字段的填充行为相同。 填充字符为 **fill**。 最后：  
  
-   如果 **iosbase**. **flags** & `ios_base::`[showpos](../standard-library/ios-functions.md#showpos) 不为零，则将标志 **+** 预置到转换规格。  
  
-   如果 **iosbase**. **flags** & `ios_base::`[showpoint](../standard-library/ios-functions.md#showpoint) 不为零，则将标志 **#** 预置到转换规格。  
  
 第四个受保护的虚拟成员函数：  
  
```  
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,  
    CharType _Fill,
    long double val) const;
```  
  
 与第三个函数的行为相同，除了将转换规格中的限定符 **l** 替换为 **L**。  
  
 第五个受保护的虚拟成员函数：  
  
```  
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,  
    CharType _Fill,
    const void* val) const;
```  
  
 与第一个函数的行为相同，除了转换规格为 `p`**,** 加上指定填充所需的任何限定符。  
  
 第六个受保护的虚拟成员函数：  
  
```  
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,  
    CharType _Fill,
    bool val) const;
```  
  
 与第一个函数的行为相同，除了它会从 `val` 生成一个布尔输出字段。  
  
 布尔输出字段采用以下两种形式之一。 如果 **iosbase**. **flags** & `ios_base::`[boolalpha](../standard-library/ios-functions.md#boolalpha) 为 **false**，则该成员函数将返回 `do_put`(_ *Next*, \_ *Iosbase*, \_ *Fill*, ( **long**) `val`)，这通常将产生生成的序列 0（若为**false**）或 1（若为 **true**）。 否则，生成的序列为 **fac**. [falsename](../standard-library/numpunct-class.md#falsename)`)`（若为 **false**）或 **fac**. [truename](../standard-library/numpunct-class.md#truename)（若为**true**）。  
  
 第七个受保护的虚拟成员函数：  
  
```  
virtual iter_type do_put(iter_type next,
    ios_base& iosbase,  
    Elem fill,
    long long val) const;
```  
  
 行为与第一个相同，只不过它将 **ld** 的转换规格替换为 **lld**。  
  
 第八个受保护的虚拟成员函数：  
  
```  
virtual iter_type do_put(iter_type next,
    ios_base& iosbase,  
    Elem fill,
    unsigned long long val) const;
```  
  
 行为与第一个相同，只不过它将转换规格 `ld` 替换为 `llu`。  
  
### <a name="example"></a>示例  
  请参阅 [put](#put) 的示例，它调用 `do_put`。  
  
##  <a name="iter_type"></a>  num_put::iter_type  
 一种类型，此类型描述输出迭代器。  
  
```  
typedef OutputIterator iter_type;  
```  
  
### <a name="remarks"></a>备注  
 该类型是模板参数 **OutputIterator** 的同义词。  
  
##  <a name="num_put"></a>  num_put::num_put  
 `num_put` 类型的对象的构造函数。  
  
```  
explicit num_put(size_t _Refs = 0);
```  
  
### <a name="parameters"></a>参数  
 `_Refs`  
 用于指定对象的内存管理类型的整数值。  
  
### <a name="remarks"></a>备注  
 `_Refs` 参数可能的值及其含义：  
  
-   0：对象的生存期由包含该对象的区域设置管理。  
  
-   1：必须手动管理对象的生存期。  
  
-   \>1： 未定义这些值。  
  
 由于该析构函数受到保护，可能没有直接的示例。  
  
 构造函数通过 **locale::**[facet](../standard-library/locale-class.md#facet_class)(_ *Refs*) 初始化其基对象。  
  
##  <a name="put"></a>  num_put::put  
 将数字转换为 **CharType** 序列以表示针对给定区域设置而设置格式的数字。  
  
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
 `dest`  
 发现插入的字符串中第一个元素的迭代器。  
  
 `_Iosbase`  
 指定包含区域设置的流，以及用于向输出和标志加标点以便对输出进行格式设置的 numpunct facet。  
  
 `_Fill`  
 用于调整间距的字符。  
  
 `val`  
 将输出的数字或布尔类型。  
  
### <a name="return-value"></a>返回值  
 发现超出生成的最后一个元素的位置的输出迭代器。  
  
### <a name="remarks"></a>备注  
 所有成员函数都返回 [do_put](#do_put)( `next`, `_Iosbase`, `_Fill`, `val`)。  
  
### <a name="example"></a>示例  
  
```cpp  
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
 [\<区域设置>](../standard-library/locale.md)   
 [facet 类](../standard-library/locale-class.md#facet_class)   
 [C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)


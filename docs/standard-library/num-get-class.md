---
title: "num_get 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- num_get
- xlocnum/std::num_get
- locale/std::num_get::char_type
- locale/std::num_get::iter_type
- locale/std::num_get::do_get
- locale/std::num_get::get
dev_langs:
- C++
helpviewer_keywords:
- num_get class
ms.assetid: 9933735d-3918-4b17-abad-5fca2adc62d7
caps.latest.revision: 18
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
ms.openlocfilehash: f8595909a294775034c3e1b725d37bfe0f846a93
ms.contentlocale: zh-cn
ms.lasthandoff: 04/29/2017

---
# <a name="numget-class"></a>num_get 类
一种模板类，用于描述一个对象来充当区域设置 facet，以便控制 `CharType` 类型的序列向数值的转换。  
  
## <a name="syntax"></a>语法  
  
```
template <class CharType, class InputIterator = istreambuf_iterator<CharType>>  
class num_get : public locale::facet;
```  
  
#### <a name="parameters"></a>参数  
 `CharType`  
 在程序中用于对区域设置中的字符进行编码的类型。  
  
 `InputIterator`  
 数值获取函数从中读取其输入的迭代器类型。  
  
## <a name="remarks"></a>备注  
 对于任何区域设置 facet，静态对象 ID 的初始存储值为零。 首次尝试访问其存储值后，将在 **ID** 中存储唯一正值。  
  
### <a name="constructors"></a>构造函数  
  
|||  
|-|-|  
|[num_get](#num_get)|用于从序列提取数值的 `num_get` 类型对象的构造函数。|  
  
### <a name="typedefs"></a>Typedef  
  
|||  
|-|-|  
|[char_type](#char_type)|一种类型，此类型用于描述区域设置使用的字符。|  
|[iter_type](#iter_type)|一种类型，此类型描述输入迭代器。|  
  
### <a name="member-functions"></a>成员函数  
  
|||  
|-|-|  
|[do_get](#do_get)|为从字符序列提取数值或布尔值而调用的虚拟函数。|  
|[get](#get)|从字符序列提取数值或布尔值。|  
  
## <a name="requirements"></a>要求  
 **标头：**\<locale>  
  
 **命名空间：** std  
  
##  <a name="char_type"></a>  num_get::char_type  
 一种类型，此类型用于描述区域设置使用的字符。  
  
```
typedef CharType char_type;
```  
  
### <a name="remarks"></a>备注  
 该类型是模板参数 **CharType** 的同义词。  
  
##  <a name="do_get"></a>  num_get::do_get  
 为从字符序列提取数值或布尔值而调用的虚拟函数。  
  
```
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long& val) const;
    
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned short& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned int& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    float& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    double& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long double& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    void *& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    bool& val) const;
```  
  
### <a name="parameters"></a>参数  
 `first`  
 从其中读取数字的字符范围的起始处。  
  
 `last`  
 从其中读取数字的字符范围的末尾处。  
  
 `_Iosbase`  
 [Ios_base](../standard-library/ios-base-class.md)，其标志由转换使用。  
  
 `_State`  
 发生故障时向其添加 failbit（请参阅 [ios_base::iostate](../standard-library/ios-base-class.md#iostate)）的状态。  
  
 `val`  
 读取的值。  
  
### <a name="return-value"></a>返回值  
 读取值后的迭代器。  
  
### <a name="remarks"></a>备注  
 第一个受保护的虚拟成员函数，  
  
```  
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long& val) const;
```  
  
 匹配位置开始的连续元素`first`序列中`[first, last)`非空整数已识别的完整，直到输入字段。 如果成功，它将转换此字段为其等效的值类型作为`long`，并将存储中的结果`val`。 它将返回一个迭代器，指定第一个超出数字输入字段的元素。 否则，函数将不在 `val` 中存储任何内容，并在 `state` 中设置 `ios_base::failbit`。 它将返回一个迭代器，指定第一个超出有效整数输入字段的任何前缀的元素。 在任一情况下，如果返回的值等于 `last`，该函数在 `state` 中设置 `ios_base::eofbit`。  
  
 使用 scan 函数匹配和转换文件中一系列 `char` 元素所用的规则来转换整数输入字段。 （假定将每个这样的 `char` 元素通过简单的、一对一的映射映射到 `Elem` 类型的等效元素。）确定等效的扫描转换规格，如下所示：  
  
 如果 `iosbase.`[ios_base::flags](../standard-library/ios-base-class.md#flags)`() & ios_base::basefield == ios_base::`[oct](../standard-library/ios-functions.md#oct)，则转换规格为 `lo`。  
  
 如果 `iosbase.flags() & ios_base::basefield == ios_base::`[hex](../standard-library/ios-functions.md#hex)，则转换规格为 `lx`。  
  
 如果 `iosbase.flags() & ios_base::basefield == 0`，则转换规格为 `li`。  
  
 否则，转换规格为 `ld`。  
  
 调用 [use_facet](../standard-library/locale-functions.md#use_facet) `<`[numpunct](../standard-library/numpunct-class.md)`<Elem>(iosbase.` [ios_base::getloc](../standard-library/ios-base-class.md#getloc)`())` 返回的 [locale facet](../standard-library/locale-class.md#facet_class)`fac` 进一步确定整数输入字段的格式。 尤其是在下列情况下：  
  
 `fac.` [numpunct::grouping](../standard-library/numpunct-class.md#grouping) `()` 确定如何对任何小数点左侧的数字进行分组  
  
 `fac.` [numpunct::thousands_sep](../standard-library/numpunct-class.md#thousands_sep) `()` 确定将任何小数点左侧的数字进行分组的序列。  
  
 如果数字输入字段中没有出现 `fac.thousands_sep()` 的任何实例，则不会采用应用分组约束。 否则，会强制执行 `fac.grouping()` 采用的分组约束，并在扫描转换发生之前删除分隔符。  
  
 第四个受保护的虚拟成员函数：  
  
```  
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long& val) const;
```  
  
 行为与第一个相同，只不过它将转换规格 `ld` 替换为 `lu`。 如果成功，它会将数字输入字段转换为 `unsigned long` 类型的值，并将该值存储于 `val`。  
  
 第五个受保护的虚拟成员函数：  
  
```
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long long& val) const;
```  
  
 行为与第一个相同，只不过它将转换规格 `ld` 替换为 `lld`。 如果成功，它会将数字输入字段转换为 `long long` 类型的值，并将该值存储于 `val`。  
  
 第六个受保护的虚拟成员函数：  
  
```  
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long long& val) const;
```  

 行为与第一个相同，只不过它将转换规格 `ld` 替换为 `llu`。 如果成功，它会将数字输入字段转换为 `unsigned long long` 类型的值，并将该值存储于 `val`。  
  
 第七个受保护的虚拟成员函数：  
  
```
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    float& val) const;
```  
  
 行为与第一个相同，只不过它旨在匹配完整的非空浮点输入字段。 `fac.`[numpunct::decimal_point](../standard-library/numpunct-class.md#decimal_point)`()` 确定从小数位分隔整数位的序列。 等效的扫描转换说明符是 `lf`。  
  
 第八个受保护的虚拟成员函数：  
  
```  
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    double& val) const;
```  
  
 行为与第一个相同，只不过它旨在匹配完整的非空浮点输入字段。 `fac.`[numpunct::decimal_point](../standard-library/numpunct-class.md#decimal_point)`()` 确定从小数位分隔整数位的序列。 等效的扫描转换说明符是 `lf`。  
  
 第九个受保护的虚拟成员函数：  
  
```  
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long double& val) const;
```  
  
 行为与第八个相同，只不过等效的扫描转换说明符为 `Lf`。  
  
 第十个的受保护的虚拟成员函数︰  
  
```  
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    void *& val) const;
```  
  
 行为与第一个相同，只不过等效的扫描转换说明符为 `p`。  
  
 最后一个（第十一个）受保护的虚拟成员函数：  
  
```  
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    bool& val) const;
```  
  
 行为与第一个相同，只不过它旨在匹配完整的非空布尔输入字段。 如果成功，它会将布尔输入字段转换为 `bool` 类型的值，并将该值存储于 `val`。  
  
 布尔输入字段采用以下两种形式之一。 如果 `iosbase.flags() & ios_base::`[boolalpha](../standard-library/ios-functions.md#boolalpha) 为 false，则它与整数输入字段相同，只不过转换的值必须为 0（若为 false）或 1（若为 true）。 否则，该序列必须匹配 `fac.`[numpunct::falsename](../standard-library/numpunct-class.md#falsename)`()`（若为 false）或 `fac.`[numpunct::truename](../standard-library/numpunct-class.md#truename)`()`（若为 true）。  
  
### <a name="example"></a>示例  
  请参阅 [get](#get) 的示例，其中虚拟成员函数由 `do_get` 调用。  
  
##  <a name="get"></a>  num_get::get  
 从字符序列提取数值或布尔值。  
  
```
iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    bool& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned short& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned int& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    float& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    double& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long double& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    void *& val) const;
```  
  
### <a name="parameters"></a>参数  
 `first`  
 从其中读取数字的字符范围的起始处。  
  
 `last`  
 从其中读取数字的字符范围的末尾处。  
  
 `_Iosbase`  
 [Ios_base](../standard-library/ios-base-class.md)，其标志由转换使用。  
  
 `_State`  
 发生故障时向其添加 failbit（请参阅 [ios_base::iostate](../standard-library/ios-base-class.md#iostate)）的状态。  
  
 `val`  
 读取的值。  
  
### <a name="return-value"></a>返回值  
 读取值后的迭代器。  
  
### <a name="remarks"></a>备注  
 所有成员函数都返回 [do_get](#do_get)( `first`, `last`, `_Iosbase`, `_State`, `val`)。  
  
 第一个受保护的虚拟成员函数首先会在序列 [ `first`, `last`) 中尝试匹配序列连续元素，直到识别到完整的非空整数输入字段。 如果成功，它会将此字段转换为与其等效的值作为类型 **long**，并将结果存储在 `val`。 它将返回一个迭代器，指定第一个超出数字输入字段的元素。 否则，函数将不在 `val` 中存储任何内容，并在 _ *State* 中设置 `ios_base::failbit`。 它将返回一个迭代器，指定第一个超出有效整数输入字段的任何前缀的元素。 在任一情况下，如果返回的值等于 **last**，该函数在 `_State` 中设置 `ios_base::eofbit`。  
  
 使用 scan 函数匹配和转换文件中一系列 `char` 元素所用的规则来转换整数输入字段。 假定将每个这样的 `char` 元素通过简单的、一对一的映射映射到 **CharType** 类型的等效元素。 确定等效的扫描转换规格，如下所示：  
  
-   如果 **iosbase**. [flags](../standard-library/ios-base-class.md#flags) & `ios_base::basefield` == `ios_base::`[oct](../standard-library/ios-functions.md#oct)，则转换规格为 **lo**。  
  
-   如果 **iosbase.flags** & **ios_base::basefield** == `ios_base::`[hex](../standard-library/ios-functions.md#hex)，则转换规格为 **lx**。  
  
-   如果 **iosbase.flags** & **ios_base::basefield** == 0，则转换规格为 `li`。  
  
-   否则，转换规格为 **ld**。  
  
 整数输入字段的格式由 [locale facet](../standard-library/locale-class.md#facet_class)**fac** 进一步确定，后者又由调用 [use_facet](../standard-library/locale-functions.md#use_facet) < [numpunct](../standard-library/numpunct-class.md)\< **Elem**>( **iosbase**. [getloc](../standard-library/ios-base-class.md#getloc)) 返回。 尤其是在下列情况下：  
  
- **fac**. [grouping](../standard-library/numpunct-class.md#grouping) 确定如何对任何小数点左侧的数字进行分组。  
  
- **fac**. [thousands_sep](../standard-library/numpunct-class.md#thousands_sep) 确定将任何小数点左侧的数字进行分组的序列。  
  
 如果 **fac**. `thousands_sep` 的实例都未出现在数字输入字段中，则不会采用分组约束。 否则，会强制执行 **fac**. **grouping** 采用的任何分组约束，并在扫描转换发生之前删除分隔符。  
  
 第二个受保护的虚拟成员函数：  
  
```
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long& val) const;
```  
  
 行为与第一个相同，只不过它将转换规格 **ld** 替换为 **lu**。 如果成功，它会将数字输入字段转换为 `unsigned long` 类型的值，并将该值存储于 `val`。  
  
 第三个受保护的虚拟成员函数：  
  
```
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    double& val) const;
```  
  
 行为与第一个相同，只不过它尝试匹配完整的非空浮点输入字段。 **fac**. [decimal_point](../standard-library/numpunct-class.md#decimal_point) 确定从小数位分隔整数位的序列。 等效的扫描转换说明符是 **lf**。  
  
 第四个受保护的虚拟成员函数：  
  
```
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long double& val) const;
```  
  
 行为与第三个相同，只不过等效的扫描转换说明符为 **Lf**。  
  
 第五个受保护的虚拟成员函数：  
  
```
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    void *& val) const;
```  
  
 行为与第一个相同，只不过等效的扫描转换说明符为 **p**。  
  
 第六个受保护的虚拟成员函数：  
  
```
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    bool& val) const;
```  
  
 行为与第一个相同，只不过它尝试匹配完整的非空布尔输入字段。 如果成功，它会将布尔输入字段转换为 `bool` 类型的值，并将该值存储于 `val`。  
  
 布尔输入字段采用以下两种形式之一。 如果 **iosbase**. **flags** & `ios_base::`[boolalpha](../standard-library/ios-functions.md#boolalpha) 为 **false**，则它与整数输入字段相同，只不过转换的值必须为 0（若为 **false**）或 1（若为 **true**）。 否则，该序列必须匹配 **fac**. [falsename](../standard-library/numpunct-class.md#falsename)（若为 **false**）或 **fac**. [truename](../standard-library/numpunct-class.md#truename)（若为**true**）。  
  
### <a name="example"></a>示例  
  
```cpp  
// num_get_get.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <sstream>  
using namespace std;  
int main( )  
{  
   locale loc( "german_germany" );  
  
   basic_stringstream<char> psz, psz2;  
   psz << "-1000,56";  
  
   ios_base::iostate st = 0;  
   long double fVal;  
   cout << use_facet <numpunct <char> >(loc).thousands_sep( ) << endl;  
  
   psz.imbue( loc );  
   use_facet <num_get <char> >  
   (loc).get( basic_istream<char>::_Iter( psz.rdbuf( ) ),  
           basic_istream<char>::_Iter(0), psz, st, fVal );  
  
   if ( st & ios_base::failbit )  
      cout << "money_get( ) FAILED" << endl;  
   else  
      cout << "money_get( ) = " << fVal << endl;  
}  
```  
  
##  <a name="iter_type"></a>  num_get::iter_type  
 一种类型，此类型描述输入迭代器。  
  
```
typedef InputIterator iter_type;
```  
  
### <a name="remarks"></a>备注  
 该类型是模板参数 **InputIterator** 的同义词。  
  
##  <a name="num_get"></a>  num_get::num_get  
 用于从序列提取数值的 `num_get` 类型对象的构造函数。  
  
```
explicit num_get(size_t _Refs = 0);
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
  
 构造函数通过 **locale::**[facet](../standard-library/locale-class.md#facet_class)( `_Refs`) 初始化其基对象。  
  
## <a name="see-also"></a>另请参阅  
 [\<区域设置>](../standard-library/locale.md)   
 [facet 类](../standard-library/locale-class.md#facet_class)   
 [C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)





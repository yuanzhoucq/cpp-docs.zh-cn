---
title: "num_get 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "num_get"
  - "std::num_get"
  - "std.num_get"
  - "xlocnum/std::num_get"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "num_get 类"
ms.assetid: 9933735d-3918-4b17-abad-5fca2adc62d7
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# num_get 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

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
 对于任何区域设置 facet，静态对象 ID 的初始存储值为零。 第一次尝试访问其存储的值中存储唯一正值中的 **id。**  
  
### <a name="constructors"></a>构造函数  
  
|||  
|-|-|  
|[num_get](#num_get__num_get)|用于从序列提取数值的 `num_get` 类型对象的构造函数。|  
  
### <a name="typedefs"></a>Typedef  
  
|||  
|-|-|  
|[char_type](#num_get__char_type)|一种类型，此类型用于描述区域设置使用的字符。|  
|[iter_type](#num_get__iter_type)|一种类型，此类型描述输入迭代器。|  
  
### <a name="member-functions"></a>成员函数  
  
|||  
|-|-|  
|[do_get](#num_get__do_get)|为从字符序列提取数值或布尔值而调用的虚拟函数。|  
|[获取](#num_get__get)|从字符序列提取数值或布尔值。|  
  
## <a name="requirements"></a>要求  
 **标头︰** \< 区域设置>  
  
 **命名空间：** std  
  
##  <a name="a-namenumgetchartypea-numgetchartype"></a><a name="num_get__char_type"></a>  num_get:: char_type  
 一种类型，此类型用于描述区域设置使用的字符。  
  
```
typedef CharType char_type;
```  
  
### <a name="remarks"></a>备注  
 类型是模板参数的同义词 **CharType**。  
  
##  <a name="a-namenumgetdogeta-numgetdoget"></a><a name="num_get__do_get"></a>  num_get:: do_get  
 为从字符序列提取数值或布尔值而调用的虚拟函数。  
  
```
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long& val) const;virtual iter_type do_get(
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
 从其读取数量的字符范围的起始处。  
  
 `last`  
 从其读取数量的字符范围的末尾。  
  
 `_Iosbase`  
  [Ios_base](../standard-library/ios-base-class.md) 由转换使用其标志。  
  
 `_State`  
 到哪些 failbit 的状态 (请参阅 [ios_base:: iostate](../standard-library/ios-base-class.md#ios_base__iostate)) 发生故障时添加。  
  
 `val`  
 读取的值。  
  
### <a name="return-value"></a>返回值  
 迭代器后读取的值。  
  
### <a name="remarks"></a>备注  
 第一个受保护的虚拟成员函数，  
  
 `virtual iter_type do_get(`  
  
 `iter_type first,`  
  
 `iter_type last,`  
  
 `ios_base& _Iosbase,`  
  
 `ios_base::iostate& _State,`  
  
 `long& val`  
  
 `) const;`  
  
 与顺序元素处开始匹配 `first` 序列中 `[``first``,` `last``)` 之前就已经取得了一套完整，非空整数输入字段。 如果成功，它将转换此字段为其等效的值作为类型 `long``,` ，并将存储中的结果 `val`。 它将返回指定数字的输入字段之外的第一个元素的迭代器。 否则，函数将存储在中为 nothing `val` 并设置 `ios_base::failbit` 中 `state`。 它将返回指定有效的整数的输入任何的字段前缀之外的第一个元素的迭代器。 在任一情况下，如果返回的值等于 `last`, ，该函数设置 `ios_base::eofbit` 中 `state`。  
  
 用于匹配和转换的一系列使用扫描函数的相同规则来转换整数输入的字段 `char` 文件中的元素。 (每个此类 `char` 元素假定要映射到等效类型的元素 `Elem` 由简单一对一映射。)确定等效扫描转换规格，如下所示︰  
  
 如果 `iosbase.`[ios_base:: flags](../standard-library/ios-base-class.md#ios_base__flags)`() & ios_base::basefield == ios_base::`[oct](../Topic/%3Cios%3E%20functions.md#oct), ，转换规格是 `lo`。  
  
 如果 `iosbase.flags() & ios_base::basefield == ios_base::`[十六进制](../Topic/%3Cios%3E%20functions.md#hex), ，转换规格是 `lx`。  
  
 如果 `iosbase.flags() & ios_base::basefield == 0`, ，转换规格是 `li`。  
  
 否则，转换规格是 `ld`。  
  
 整数输入字段的格式进一步由 [区域设置 facet，](../standard-library/locale-class.md#facet_class)`fac` 调用所返回 [use_facet](../Topic/%3Clocale%3E%20functions.md#use_facet) `<`[numpunct](../standard-library/numpunct-class.md)`<Elem>(iosbase.` [ios_base:: getloc](../standard-library/ios-base-class.md#ios_base__getloc)`())`。 尤其是在下列情况下：  
  
 `fac.` [numpunct:: grouping](../standard-library/numpunct-class.md#numpunct__grouping) `()` 确定对任何小数点左边数字进行分组  
  
 `fac.` [numpunct:: thousands_sep](../standard-library/numpunct-class.md#numpunct__thousands_sep) `()` 确定任何小数点左边数字进行分组的序列。  
  
 如果没有实例 `fac.thousands_sep()` 出现在数字输入字段中，没有分组限制。 否则，任何分组约束强加 `fac.grouping()` 会强制执行和扫描转换发生之前，将删除分隔符。  
  
 第四个受保护的虚拟成员函数︰  
  
 `virtual iter_type do_get(`  
  
 `iter_type first,`  
  
 `iter_type last,`  
  
 `ios_base& _Iosbase,`  
  
 `ios_base::iostate& _State,`  
  
 `unsigned long& val`  
  
 `) const;`  
  
 行为与第一个相同，只不过它将替换为转换规格的 `ld` 与 `lu`。 如果成功它将转换输入的数字字段转换为类型值 `unsigned long` ，并将存储中的对应值 `val`。  
  
 第五个的受保护的虚拟成员函数︰  
  
 `virtual iter_type do_get(`  
  
 `iter_type first,`  
  
 `iter_type last,`  
  
 `ios_base& _Iosbase,`  
  
 `ios_base::iostate& _State,`  
  
 `long long& val`  
  
 `) const;`  
  
 行为与第一个相同，只不过它将替换为转换规格的 `ld` 与 `lld`。 如果成功它将转换输入的数字字段转换为类型值 `long long` ，并将存储中的对应值 `val`。  
  
 第六个受保护的虚拟成员函数︰  
  
 `virtual iter_type do_get(`  
  
 `iter_type first,`  
  
 `iter_type last,`  
  
 `ios_base& _Iosbase,`  
  
 `ios_base::iostate& _State,`  
  
 `unsigned long long& val`  
  
 `) const;`  
  
 行为与第一个相同，只不过它将替换为转换规格的 `ld` 与 `llu`。 如果成功它将转换输入的数字字段转换为类型值 `unsigned long long` ，并将存储中的对应值 `val`。  
  
 第七个受保护的虚拟成员函数︰  
  
 `virtual iter_type do_get(`  
  
 `iter_type first,`  
  
 `iter_type last,`  
  
 `ios_base& _Iosbase,`  
  
 `ios_base::iostate& _State,`  
  
 `float& val`  
  
 `) const;`  
  
 行为与第一个相同之处在于它致力于使完整、 非空浮点的输入的字段相匹配。 `fac.`[numpunct:: decimal_point](../standard-library/numpunct-class.md#numpunct__decimal_point)`()` 确定将整数位与小数位分隔的序列。 等效扫描转换说明符是 `lf`。  
  
 第八个受保护的虚拟成员函数︰  
  
 `virtual iter_type do_get(`  
  
 `iter_type first,`  
  
 `iter_type last,`  
  
 `ios_base& _Iosbase,`  
  
 `ios_base::iostate& _State,`  
  
 `double& val`  
  
 `) const;`  
  
 行为与第一个相同之处在于它致力于使完整、 非空浮点的输入的字段相匹配。 `fac.`[numpunct:: decimal_point](../standard-library/numpunct-class.md#numpunct__decimal_point)`()` 确定将整数位与小数位分隔的序列。 等效扫描转换说明符是 `lf`。  
  
 第九个受保护的虚拟成员函数︰  
  
 `virtual iter_type do_get(`  
  
 `iter_type first,`  
  
 `iter_type last,`  
  
 `ios_base& _Iosbase,`  
  
 `ios_base::iostate& _State,`  
  
 `long double& val`  
  
 `) const;`  
  
 唯一的差别在于等效扫描转换说明符的行为与第八、 相同 `Lf`。  
  
 第九个受保护的虚拟成员函数︰  
  
 `virtual iter_type do_get(`  
  
 `iter_type first,`  
  
 `iter_type last,`  
  
 `ios_base& _Iosbase,`  
  
 `ios_base::iostate& _State,`  
  
 `void *& val`  
  
 `) const;`  
  
 唯一的差别在于等效扫描转换说明符的行为相同第一、 `p`。  
  
 最后一个的受保护的 （第十一个） 虚拟成员函数︰  
  
 `virtual iter_type do_get(`  
  
 `iter_type first,`  
  
 `iter_type last,`  
  
 `ios_base& _Iosbase,`  
  
 `ios_base::iostate& _State,`  
  
 `bool& val`  
  
 `) const;`  
  
 行为与第一个相同之处在于它致力于使完整、 非空布尔值的输入的字段相匹配。 如果成功它将转换的布尔值的输入的字段转换为类型值 `bool` ，并将存储中的对应值 `val`。  
  
 布尔值的输入的字段采用两种形式之一。 如果 `iosbase.flags() & ios_base::`[boolalpha](../Topic/%3Cios%3E%20functions.md#boolalpha) 为 false，它等同于一个整数输入字段，只不过转换后的值必须为 0 (false) 或 1 (true)。 否则，该序列必须与任一条件匹配 `fac.`[numpunct:: falsename](../standard-library/numpunct-class.md#numpunct__falsename)`()` （对于 false)，或 `fac.`[numpunct:: truename](../standard-library/numpunct-class.md#numpunct__truename)`()` （表示 true)。  
  
### <a name="example"></a>示例  
  请参阅示例 [获取](#num_get__get), ，其中的虚拟成员函数将由 `do_get`。  
  
##  <a name="a-namenumgetgeta-numgetget"></a><a name="num_get__get"></a>  num_get:: get  
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
 从其读取数量的字符范围的起始处。  
  
 `last`  
 从其读取数量的字符范围的末尾。  
  
 `_Iosbase`  
  [Ios_base](../standard-library/ios-base-class.md) 由转换使用其标志。  
  
 `_State`  
 到哪些 failbit 的状态 (请参阅 [ios_base:: iostate](../standard-library/ios-base-class.md#ios_base__iostate)) 发生故障时添加。  
  
 `val`  
 读取的值。  
  
### <a name="return-value"></a>返回值  
 迭代器后读取的值。  
  
### <a name="remarks"></a>备注  
 所有成员函数都返回 [do_get](#num_get__do_get)( `first`, ，`last`, ，`_Iosbase`, ，`_State`, ，`val`)。  
  
 第一个受保护的虚拟成员函数会尝试匹配序列中的第一个位置开始的连续元素 [ `first`, ，`last`) 之前就已经取得了一套完整，非空整数输入字段。 如果成功，它将转换此字段为其等效的值作为类型 **长** ，并将存储中的结果 `val`。 它将返回指定数字的输入字段之外的第一个元素的迭代器。 否则，函数将存储在中为 nothing `val` 并设置 `ios_base::failbit` 中 _ *状态*。 它将返回指定有效的整数的输入任何的字段前缀之外的第一个元素的迭代器。 在任一情况下，如果返回的值等于 **最后一个**, ，该函数设置 `ios_base::eofbit` 中 `_State`。  
  
 用于匹配和转换的一系列使用扫描函数的相同规则来转换整数输入的字段 `char` 文件中的元素。 每个此类 `char` 元素假定要映射到等效类型的元素 **CharType** 由简单的一对一映射。 确定等效扫描转换规格，如下所示︰  
  
-   如果 **iosbase**。 [标志](../standard-library/ios-base-class.md#ios_base__flags) & `ios_base::basefield` == `ios_base::`[oct](../Topic/%3Cios%3E%20functions.md#oct), ，转换规格是 **lo**。  
  
-   如果 **iosbase.flags** & **ios_base::basefield** == `ios_base::`[十六进制](../Topic/%3Cios%3E%20functions.md#hex), ，转换规格是 **lx**。  
  
-   如果 **iosbase.flags** & **ios_base::basefield** = = 0，转换规格是 `li`。  
  
-   否则，转换规格是 **ld**。  
  
 整数输入字段的格式进一步由 [区域设置 facet，](../standard-library/locale-class.md#facet_class)**预计完成成本** 调用所返回 [use_facet](../Topic/%3Clocale%3E%20functions.md#use_facet) < [numpunct](../standard-library/numpunct-class.md)\< **Elem**> ( **iosbase**。 [getloc](../standard-library/ios-base-class.md#ios_base__getloc))。 尤其是在下列情况下：  
  
- **预计完成成本**。 [分组](../standard-library/numpunct-class.md#numpunct__grouping) 确定位数如何分组到任何小数点左侧。  
  
- **预计完成成本**。 [thousands_sep](../standard-library/numpunct-class.md#numpunct__thousands_sep) 确定任何小数点左边数字进行分组的序列。  
  
 如果没有实例 **预计完成成本**。 `thousands_sep` 数值输入字段中会出现，任何分组限制。 否则，任何分组约束强加 **预计完成成本**。 **分组** 强制执行和扫描转换发生之前，将删除分隔符。  
  
 第二个受保护的虚拟成员函数︰  
  
```
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long& val) const;
```  
  
 行为与第一个相同，只不过它将替换为转换规格的 **ld** 与 **lu**。 如果成功，它将转换输入的数字字段转换为类型值 `unsigned long` ，并将存储中的对应值 `val`。  
  
 第三个受保护的虚拟成员函数中︰  
  
```
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    double& val) const;
```  
  
 之处在于它会尝试匹配完整、 非空浮点的输入的字段的行为与第一个相同。 **预计完成成本**。 [decimal_point](../standard-library/numpunct-class.md#numpunct__decimal_point) 确定将整数位与小数位分隔的序列。 等效扫描转换说明符是 **lf**。  
  
 第四个受保护的虚拟成员函数︰  
  
```
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long double& val) const;
```  
  
 行为相同第三个、 唯一的差别在于等效扫描转换说明符 **Lf**。  
  
 第五个的受保护的虚拟成员函数︰  
  
```
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    void *& val) const;
```  
  
 唯一的差别在于等效扫描转换说明符的行为相同第一、 **p**。  
  
 第六个受保护的虚拟成员函数︰  
  
```
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    bool& val) const;
```  
  
 之处在于它会尝试匹配完整、 非空布尔值的输入的字段的行为与第一个相同。 如果成功它将转换的布尔值的输入的字段转换为类型值 `bool` ，并将存储中的对应值 `val`。  
  
 布尔值的输入的字段采用两种形式之一。 如果 **iosbase**。 **标志** & `ios_base::`[boolalpha](../Topic/%3Cios%3E%20functions.md#boolalpha) 是 **false**, ，它等同于一个整数输入字段，只不过转换后的值必须是 0 (对于 **false**) 或 1 (对于 **true**)。 否则，该序列必须与任一条件匹配 **预计完成成本**。 [falsename](../standard-library/numpunct-class.md#numpunct__falsename) (对于 **false**)，或 **预计完成成本**。 [truename](../standard-library/numpunct-class.md#numpunct__truename) (对于 **true**)。  
  
### <a name="example"></a>示例  
  
```  
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
  
##  <a name="a-namenumgetitertypea-numgetitertype"></a><a name="num_get__iter_type"></a>  num_get:: iter_type  
 一种类型，此类型描述输入迭代器。  
  
```
typedef InputIterator iter_type;
```  
  
### <a name="remarks"></a>备注  
 类型是模板参数的同义词 **InputIterator**。  
  
##  <a name="a-namenumgetnumgeta-numgetnumget"></a><a name="num_get__num_get"></a>  num_get:: num_get  
 用于从序列提取数值的 `num_get` 类型对象的构造函数。  
  
```
explicit num_get(size_t _Refs = 0);
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
  
## <a name="see-also"></a>另请参阅  
 [\< 区域设置>](../standard-library/locale.md)   
 [facet 类](../standard-library/locale-class.md#facet_class)   
 [C + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)




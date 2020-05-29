---
title: money_get 类
ms.date: 11/04/2016
f1_keywords:
- xlocmon/std::money_get
- xlocmon/std::money_get::char_type
- xlocmon/std::money_get::iter_type
- xlocmon/std::money_get::string_type
- xlocmon/std::money_get::do_get
- xlocmon/std::money_get::get
helpviewer_keywords:
- std::money_get [C++]
- std::money_get [C++], char_type
- std::money_get [C++], iter_type
- std::money_get [C++], string_type
- std::money_get [C++], do_get
- std::money_get [C++], get
ms.assetid: 692d3374-3fe7-4b46-8aeb-f8d91ed66b2e
ms.openlocfilehash: ac85e99bfb834fd970a804269f25ec9f20960a23
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375900"
---
# <a name="money_get-class"></a>money_get 类

类模板描述一个对象，该对象可用作区域设置，用于控制类型`CharType`序列转换为货币值。

## <a name="syntax"></a>语法

```cpp
template <class CharType, class InputIterator = istreambuf_iterator<CharType>>
class money_get : public locale::facet;
```

### <a name="parameters"></a>参数

*字符类型*\
在程序中用于对区域设置中的字符进行编码的类型。

*输入迭代器*\
获取函数从中读取其输入的迭代器类型。

## <a name="remarks"></a>备注

对于任何区域设置 facet，静态对象 ID 的初始存储值为零。 首次尝试访问其存储值后，将在 **ID** 中存储唯一正值。

### <a name="constructors"></a>构造函数

|构造函数|说明|
|-|-|
|[money_get](#money_get)|用于从表示货币值的序列中提取数值的 `money_get` 类型对象的构造函数。|

### <a name="typedefs"></a>Typedef

|类型名称|说明|
|-|-|
|[char_type](#char_type)|一种类型，此类型用于描述区域设置使用的字符。|
|[iter_type](#iter_type)|一种类型，此类型描述输入迭代器。|
|[string_type](#string_type)|一种类型，此类型描述包含 `CharType` 类型字符的字符串。|

### <a name="member-functions"></a>成员职能

|成员函数|说明|
|-|-|
|[do_get](#do_get)|一种虚拟函数，通过调用此函数可从表示货币值的字符序列提取数值。|
|[get](#get)|从表示货币值的字符序列提取数值。|

## <a name="requirements"></a>要求

**标头：** \<locale>

**命名空间:** std

## <a name="money_getchar_type"></a><a name="char_type"></a>money_get：char_type

一种类型，此类型用于描述区域设置使用的字符。

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>备注

该类型是模板参数 *CharType* 的同义词。

## <a name="money_getdo_get"></a><a name="do_get"></a>money_get：:d

一种虚拟函数，通过调用此函数可从表示货币值的字符序列提取数值。

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    bool Intl,
    ios_base& Iosbase,
    ios_base::iostate& State,
    long double& val) const virtual iter_type do_get(iter_type first,
    iter_type last,
    bool Intl,
    ios_base& Iosbase,
    ios_base::iostate& State,
    string_type& val) const
```

### <a name="parameters"></a>参数

*第一*\
确定待转换序列开头位置的输入迭代器。

*最后*\
确定待转换序列末尾位置的输入迭代器。

*国际*\
一个布尔值，该值指示在序列中预期的货币符号的类型：如果为国际，则为 **true**，如果为国内，则为 **false**。

*约斯基地*\
一种格式标志，设定时表示货币符号是可选项；否则，它是必需项。

*状态*\
根据操作是否成功，设置流状态的相应位掩码元素。

*瓦尔*\
存储已转换序列的字符串。

### <a name="return-value"></a>返回值

发现第一个超出货币输入字段的元素的输入迭代器。

### <a name="remarks"></a>备注

第一个受保护的虚拟成员函数首先会在序列 [ `first`, `last`) 中尝试匹配序列连续元素，直到识别到完整的非空货币输入字段。 如果成功，它将此字段转换为一个或多个十进制数字序列，选项前面有一个减号 （），`-`以表示金额并将结果存储在[string_type](#string_type)对象*val*中。 它将返回一个迭代器，指定第一个超出货币输入字段的元素。 否则，函数将空序列存储在*val*中，`ios_base::failbit`并在*状态*中设置。 它将返回一个迭代器，指定第一个超出有效货币输入字段的任何前缀的元素。 在任一情况下，如果返回的值等于 `last`，该函数在 `State` 中设置 `ios_base::eofbit`。

第二个虚拟受保护成员函数的表示行为与第一个函数相同，但成功时，它将可选签名的数字序列转换为**长双**型值，并将该值存储在*val*。

货币输入字段的格式由[区域设置 facet](../standard-library/locale-class.md#facet_class)**fac** 决定，而后者又有有效调用 [use_facet](../standard-library/locale-functions.md#use_facet) < [moneypunct](../standard-library/moneypunct-class.md)\< **CharType**, **intl**>>( **iosbase**. [getloc](../standard-library/ios-base-class.md#getloc)）。

具体来说：

- **fac**. [neg_format](../standard-library/moneypunct-class.md#neg_format) 确定字段的组件出现的顺序。

- **fac**. [curr_symbol](../standard-library/moneypunct-class.md#curr_symbol) 确定构成货币符号的元素的序列。

- **fac**. [positive_sign](../standard-library/moneypunct-class.md#positive_sign) 确定构成正号的元素的序列。

- **fac**. [negative_sign](../standard-library/moneypunct-class.md#negative_sign) 确定构成负号的元素的序列。

- **fac**. [grouping](../standard-library/moneypunct-class.md#grouping) 确定如何对任何小数点左侧的数字进行分组。

- **fac**. [thousands_sep](../standard-library/moneypunct-class.md#thousands_sep) 确定将任何小数点左侧的数字进行分组的元素。

- **fac**. [decimal_point](../standard-library/moneypunct-class.md#decimal_point) 确定从小数位分隔整数位的元素。

- **fac**. [frac_digits](../standard-library/moneypunct-class.md#frac_digits) 确定任何小数点右侧的有效位数。 分析货币金额时，若其小数位比 `frac_digits` 调用的小数位还多，`do_get` 将在占用最多 `frac_digits` 字符后停止分析。

如果符号字符串（**fac**. `negative_sign` 或 **fac**. `positive_sign`）具有多个元素，仅第一个元素会在等于 **money_base::sign** 的元素在 ( **fac**. `neg_format`). 剩余所有元素在货币输入字段的末尾匹配。 如果两个字符串都没有第一个元素匹配货币输入字段中的下一个元素，则将符号字符串视为空，且符号为正。

如果 **iosbase**. [标志](../standard-library/ios-base-class.md#flags) & [显示库](../standard-library/ios-functions.md#showbase)是非零的，字符串**fac**。 `curr_symbol` 必须在等于 **money_base::symbol** 的元素在此格式模式中出现的位置匹配。 否则，如果 **money_base::symbol** 出现在此格式模式末尾，或如果没有符号字符串的元素要进行匹配，则不会匹配货币符号。 否则，将选择性地匹配货币符号。

如果 **fac**. `thousands_sep` 的任何实例都不出现在货币输入字段的值部分（等于 **money_base::value** 的元素在格式模式中出现的位置），则不会采用分组约束。 否则，会强制执行 **fac**. **grouping** 采用的任何分组约束。 请注意，所产生的数字序列表示一个整数，其低位 **fac**. `frac_digits` 十进制数字应位于小数点右侧。

如果等于 **money_base::space** 的元素未在格式模式的末尾出现，而是在格式模式中出现，则匹配任意空格。 否则，不匹配任何内部空格。 将元素 *ch* 视为空格，前提是 [use_facet](../standard-library/locale-functions.md#use_facet) < [ctype](../standard-library/ctype-class.md)\< **CharType**> >( **iosbase**. [getloc](../standard-library/ios-base-class.md#getloc)）。 [is](../standard-library/ctype-class.md#is)( **ctype_base::space**, *ch*) 为 **true**）。

### <a name="example"></a>示例

请参阅 [get](#get) 的示例，它调用 `do_get`。

## <a name="money_getget"></a><a name="get"></a>money_get：获取

从表示货币值的字符序列提取数值。

```cpp
iter_type get(iter_type first,
    iter_type last,
    bool Intl,
    ios_base& Iosbase,
    ios_base::iostate& State,
    long double& val) const;

iter_type get(iter_type first,
    iter_type last,
    bool Intl,
    ios_base& Iosbase,
    ios_base::iostate& State,
    string_type& val) const;
```

### <a name="parameters"></a>参数

*第一*\
确定待转换序列开头位置的输入迭代器。

*最后*\
确定待转换序列末尾位置的输入迭代器。

*国际*\
一个布尔值，该值指示在序列中预期的货币符号的类型：如果为国际，则为 **true**，如果为国内，则为 **false**。

*约斯基地*\
一种格式标志，设定时表示货币符号是可选项；否则，它是必需项

*状态*\
根据操作是否成功，设置流状态的相应位掩码元素。

*瓦尔*\
存储已转换序列的字符串。

### <a name="return-value"></a>返回值

发现第一个超出货币输入字段的元素的输入迭代器。

### <a name="remarks"></a>备注

两个成员函数都返回[do_get](#do_get)`(first, last, Intl, Iosbase, State, val)`。

### <a name="example"></a>示例

```cpp
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

## <a name="money_getiter_type"></a><a name="iter_type"></a>money_get：iter_type

一种类型，此类型描述输入迭代器。

```cpp
typedef InputIterator iter_type;
```

### <a name="remarks"></a>备注

该类型是模板参数 **InputIterator** 的同义词。

## <a name="money_getmoney_get"></a><a name="money_get"></a>money_get：money_get

用于从表示货币值的序列中提取数值的 `money_get` 类型对象的构造函数。

```cpp
explicit money_get(size_t _Refs = 0);
```

### <a name="parameters"></a>参数

*_Refs*\
用于指定对象的内存管理类型的整数值。

### <a name="remarks"></a>备注

*_Refs*参数的可能值及其显著性为：

- 0：对象的生存期由包含该对象的区域设置管理。

- 1：必须手动管理对象的生存期。

- \>1： 未定义这些值。

由于该析构函数受到保护，可能没有直接的示例。

构造函数用区域设置初始化其基本对象 **：：**[分](../standard-library/locale-class.md#facet_class)*面（_Refs*）。

## <a name="money_getstring_type"></a><a name="string_type"></a>money_get：string_type

一种类型，此类型描述包含 **CharType** 类型字符的字符串。

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>备注

该类型描述了类模板的专门化[basic_string。](../standard-library/basic-string-class.md)

## <a name="see-also"></a>另请参阅

[\<区域设置>](../standard-library/locale.md)\
[分面类](../standard-library/locale-class.md#facet_class)\
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)

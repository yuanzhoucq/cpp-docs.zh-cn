---
title: money_get 类 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xlocmon/std::money_get
- xlocmon/std::money_get::char_type
- xlocmon/std::money_get::iter_type
- xlocmon/std::money_get::string_type
- xlocmon/std::money_get::do_get
- xlocmon/std::money_get::get
dev_langs:
- C++
helpviewer_keywords:
- std::money_get [C++]
- std::money_get [C++], char_type
- std::money_get [C++], iter_type
- std::money_get [C++], string_type
- std::money_get [C++], do_get
- std::money_get [C++], get
ms.assetid: 692d3374-3fe7-4b46-8aeb-f8d91ed66b2e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1e3059a4291d21e11304fdf571d2e12828df26fb
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33861696"
---
# <a name="moneyget-class"></a>money_get 类

此模板类描述可用作区域设置 facet 的对象，此对象用于控制 `CharType` 类型序列到货币值的转换。

## <a name="syntax"></a>语法

```cpp
template <class CharType, class InputIterator = istreambuf_iterator<CharType>>
class money_get : public locale::facet;
```

### <a name="parameters"></a>参数

`CharType` 在程序内所使用的区域设置中的字符进行编码的类型。

`InputIterator` 获取函数从中读取其输入的迭代器的类型。

## <a name="remarks"></a>备注

对于任何区域设置 facet，静态对象 ID 的初始存储值为零。 首次尝试访问其存储值后，将在 **ID** 中存储唯一正值。

### <a name="constructors"></a>构造函数

|构造函数|描述|
|-|-|
|[money_get](#money_get)|用于从表示货币值的序列中提取数值的 `money_get` 类型对象的构造函数。|

### <a name="typedefs"></a>Typedef

|类型名称|描述|
|-|-|
|[char_type](#char_type)|一种类型，此类型用于描述区域设置使用的字符。|
|[iter_type](#iter_type)|一种类型，此类型描述输入迭代器。|
|[string_type](#string_type)|一种类型，此类型描述包含 `CharType` 类型字符的字符串。|

### <a name="member-functions"></a>成员函数

|成员函数|描述|
|-|-|
|[do_get](#do_get)|一种虚拟函数，通过调用此函数可从表示货币值的字符序列提取数值。|
|[get](#get)|从表示货币值的字符序列提取数值。|

## <a name="requirements"></a>要求

**标头：** \<locale>

**命名空间：** std

## <a name="char_type"></a>  money_get::char_type

一种类型，此类型用于描述区域设置使用的字符。

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>备注

该类型是模板参数 **CharType** 的同义词。

## <a name="do_get"></a>money_get::do_get

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

`first` 发现要转换的序列的开头的输入迭代器。

`last` 发现要转换的序列的末尾的输入迭代器。

`Intl` 一个布尔值，该值指示序列中预期的货币符号的类型： **true**如果国际， **false**如果国内。

`Iosbase` 一种格式标志的时设定，表示货币符号是可选的;否则，它是必需的。

`State` 设置根据操作成功与否的流状态的相应位掩码元素。

`val` 一个字符串，它存储转换后的序列。

### <a name="return-value"></a>返回值

发现第一个超出货币输入字段的元素的输入迭代器。

### <a name="remarks"></a>备注

第一个受保护的虚拟成员函数首先会在序列 [ `first`, `last`) 中尝试匹配序列连续元素，直到识别到完整的非空货币输入字段。 如果成功，它会将此字段转换为一个包含一个或多个十进制数字的序列（数字前可带负号 ( `-`)），以表示数额，并将结果存储于 [string_type](#string_type) 对象 `val`。 它将返回一个迭代器，指定第一个超出货币输入字段的元素。 否则，函数将在 `val` 中存储空的序列，并在 `State` 中设置 `ios_base::failbit`。 它将返回一个迭代器，指定第一个超出有效货币输入字段的任何前缀的元素。 在任一情况下，如果返回的值等于 `last`，该函数在 `State` 中设置 `ios_base::eofbit`。

第二个受保护的虚拟成员函数的行为与第一个相同，只不过如果成功，它会将选择性签名的数字序列转换为 `long double` 类型的值，并将该值存储于 `val`。

货币输入字段的格式由[区域设置 facet](../standard-library/locale-class.md#facet_class)**fac** 决定，而后者又有有效调用 [use_facet](../standard-library/locale-functions.md#use_facet) < [moneypunct](../standard-library/moneypunct-class.md)\< **CharType**, **intl**>>( **iosbase**. [getloc](../standard-library/ios-base-class.md#getloc)) 返回。

尤其是在下列情况下：

- **fac**. [neg_format](../standard-library/moneypunct-class.md#neg_format) 确定字段的组件出现的顺序。

- **fac**. [curr_symbol](../standard-library/moneypunct-class.md#curr_symbol) 确定构成货币符号的元素的序列。

- **fac**. [positive_sign](../standard-library/moneypunct-class.md#positive_sign) 确定构成正号的元素的序列。

- **fac**. [negative_sign](../standard-library/moneypunct-class.md#negative_sign) 确定构成负号的元素的序列。

- **fac**. [grouping](../standard-library/moneypunct-class.md#grouping) 确定如何对任何小数点左侧的数字进行分组。

- **fac**. [thousands_sep](../standard-library/moneypunct-class.md#thousands_sep) 确定将任何小数点左侧的数字进行分组的元素。

- **fac**. [decimal_point](../standard-library/moneypunct-class.md#decimal_point) 确定从小数位分隔整数位的元素。

- **fac**. [frac_digits](../standard-library/moneypunct-class.md#frac_digits) 确定任何小数点右侧的有效位数。 分析货币金额时，若其小数位比 `frac_digits` 调用的小数位还多，`do_get` 将在占用最多 `frac_digits` 字符后停止分析。

如果符号字符串（**fac**. `negative_sign` 或 **fac**. `positive_sign`）具有多个元素，仅第一个元素会在等于 **money_base::sign** 的元素在 ( **fac**. `neg_format`) 格式模式中出现的位置匹配。 剩余所有元素在货币输入字段的末尾匹配。 如果两个字符串都没有第一个元素匹配货币输入字段中的下一个元素，则将符号字符串视为空，且符号为正。

如果 **iosbase**. [flags](../standard-library/ios-base-class.md#flags) & [showbase](../standard-library/ios-functions.md#showbase) 不为零，则字符串 **fac**. `curr_symbol` 必须在等于 **money_base::symbol** 的元素在此格式模式中出现的位置匹配。 否则，如果 **money_base::symbol** 出现在此格式模式末尾，或如果没有符号字符串的元素要进行匹配，则不会匹配货币符号。 否则，将选择性地匹配货币符号。

如果 **fac**. `thousands_sep` 的任何实例都不出现在货币输入字段的值部分（等于 **money_base::value** 的元素在格式模式中出现的位置），则不会采用分组约束。 否则，会强制执行 **fac**. **grouping** 采用的任何分组约束。 请注意，所产生的数字序列表示一个整数，其低位 **fac**. `frac_digits` 十进制数字应位于小数点右侧。

如果等于 **money_base::space** 的元素未在格式模式的末尾出现，而是在格式模式中出现，则匹配任意空格。 否则，不匹配任何内部空格。 将元素 *ch* 视为空格，前提是 [use_facet](../standard-library/locale-functions.md#use_facet) < [ctype](../standard-library/ctype-class.md)\< **CharType**> >( **iosbase**. [getloc](../standard-library/ios-base-class.md#getloc))。 [is](../standard-library/ctype-class.md#is)( **ctype_base::space**, *ch*) 为 **true**）。

### <a name="example"></a>示例

请参阅 [get](#get) 的示例，它调用 `do_get`。

## <a name="get"></a>money_get::get

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

`first` 发现要转换的序列的开头的输入迭代器。

`last` 发现要转换的序列的末尾的输入迭代器。

`Intl` 一个布尔值，该值指示序列中预期的货币符号的类型： **true**如果国际， **false**如果国内。

`Iosbase` 一种格式标志的时设定，表示货币符号是可选的;否则，它是必需

`State` 设置根据操作是否成功的流状态的相应位掩码元素。

`val` 一个字符串，它存储转换后的序列。

### <a name="return-value"></a>返回值

发现第一个超出货币输入字段的元素的输入迭代器。

### <a name="remarks"></a>备注

两个成员函数返回[do_get](#do_get)`(first, last, Intl, Iosbase, State, val)`。

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

## <a name="iter_type"></a>money_get::iter_type

一种类型，此类型描述输入迭代器。

```cpp
typedef InputIterator iter_type;
```

### <a name="remarks"></a>备注

该类型是模板参数 **InputIterator** 的同义词。

## <a name="money_get"></a>money_get::money_get

用于从表示货币值的序列中提取数值的 `money_get` 类型对象的构造函数。

```cpp
explicit money_get(size_t _Refs = 0);
```

### <a name="parameters"></a>参数

`_Refs` 用于指定类型的对象的内存管理的整数值。

### <a name="remarks"></a>备注

`_Refs` 参数可能的值及其含义：

- 0：对象的生存期由包含该对象的区域设置管理。

- 1：必须手动管理对象的生存期。

- \> 1： 未定义这些值。

由于该析构函数受到保护，可能没有直接的示例。

构造函数初始化与与其基对象**区域设置::**[方面](../standard-library/locale-class.md#facet_class)(**_ * * * Refs*)。

## <a name="string_type"></a>  money_get::string_type

一种类型，此类型描述包含 **CharType** 类型字符的字符串。

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>备注

此类型描述 [basic_string](../standard-library/basic-string-class.md) 模板类专用化。

## <a name="see-also"></a>请参阅

[\<locale>](../standard-library/locale.md)<br/>
[facet 类](../standard-library/locale-class.md#facet_class)<br/>
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>

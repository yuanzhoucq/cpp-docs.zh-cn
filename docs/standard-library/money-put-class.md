---
title: money_put 类
ms.date: 11/01/2018
f1_keywords:
- xlocmon/std::money_put
- xlocmon/std::money_put::char_type
- xlocmon/std::money_put::iter_type
- xlocmon/std::money_put::string_type
- xlocmon/std::money_put::do_put
- xlocmon/std::money_put::put
helpviewer_keywords:
- std::money_put [C++]
- std::money_put [C++], char_type
- std::money_put [C++], iter_type
- std::money_put [C++], string_type
- std::money_put [C++], do_put
- std::money_put [C++], put
ms.assetid: f439fd56-c9b1-414c-95e1-66c918c6eee6
ms.openlocfilehash: 035cc4e7b9cfac262979509bf7b4570e2c55336c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377426"
---
# <a name="money_put-class"></a>money_put 类

类模板描述一个对象，该对象可用作区域设置，用于控制货币值转换为类型`CharType`序列的对象。

## <a name="syntax"></a>语法

```cpp
template <class CharType,
    class OutputIterator = ostreambuf_iterator<CharType>>
class money_put : public locale::facet;
```

### <a name="parameters"></a>参数

*字符类型*\
在程序中用于对区域设置中的字符进行编码的类型。

*输出迭代器*\
供货币放置函数写入其输出结果的迭代器类型。

## <a name="remarks"></a>备注

对于任何区域设置 facet，静态对象 ID 的初始存储值为零。 首次尝试访问其存储值后，将在 **ID** 中存储唯一正值。

### <a name="constructors"></a>构造函数

|构造函数|说明|
|-|-|
|[money_put](#money_put)|`money_put` 类型的对象的构造函数。|

### <a name="typedefs"></a>Typedef

|类型名称|说明|
|-|-|
|[char_type](#char_type)|一种类型，此类型用于描述区域设置使用的字符。|
|[iter_type](#iter_type)|一种类型，此类型描述输出迭代器。|
|[string_type](#string_type)|一种类型，此类型描述包含 `CharType` 类型字符的字符串。|

### <a name="member-functions"></a>成员职能

|成员函数|说明|
|-|-|
|[do_put](#do_put)|一种虚拟函数，通过调用此函数可将数字或字符串转换为表示货币值的字符序列。|
|[把](#put)|将数字或字符串转换为表示货币值的字符序列。|

## <a name="requirements"></a>要求

**标头：** \<locale>

**命名空间:** std

## <a name="money_putchar_type"></a><a name="char_type"></a>money_put：char_type

一种类型，此类型用于描述区域设置使用的字符。

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>备注

该类型是模板参数 **CharType** 的同义词。

## <a name="money_putdo_put"></a><a name="do_put"></a>money_put：:d

一种虚拟函数，通过调用此函数可将数字或字符串转换为表示货币值的字符序列。

```cpp
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

*下一个*\
发现插入的字符串中第一个元素的迭代器。

*_Intl*\
一个布尔值，该值指示在序列中预期的货币符号的类型：如果为国际，则为 **true**，如果为国内，则为 **false**。

*_Iosbase*\
一种格式标志，设定时表示货币符号是可选项；否则，它是必需项

*_Fill*\
用于调整间距的字符。

*瓦尔*\
要转换的字符串对象。

### <a name="return-value"></a>返回值

发现超出生成的最后一个元素的位置的输出迭代器。

### <a name="remarks"></a>备注

第一个虚拟受保护成员函数生成顺序元素，从*下一个*开始，从[string_type](#string_type)对象*val*生成货币输出字段。 由*val*控制的序列必须以一个或多个小数位数开头，可选前面有一个表示金额的减号 （-）。 该函数返回一个迭代器，指定超出生成货币输出字段的第一个元素。

第二个虚拟受保护成员函数的表示与第一个函数相同，只不过它首先有效地将*val*转换为小数位数序列，选项前面有减号，然后按上述顺序转换该序列。

货币输出字段的格式由[区域设置 facet](../standard-library/locale-class.md#facet_class) fac 决定，而后者又由（有效）调用 [use_facet](../standard-library/locale-functions.md#use_facet) < [moneypunct](../standard-library/moneypunct-class.md)\< **CharType**, **intl**> >( **iosbase**. [getloc](../standard-library/ios-base-class.md#getloc)）。

具体来说：

- **fac**. [pos_format](../standard-library/moneypunct-class.md#pos_format) 确定生成非负数值的字段组件所采用的顺序。

- **fac**. [neg_format](../standard-library/moneypunct-class.md#neg_format) 确定生成负数值的字段组件所采用的顺序。

- **fac**. [curr_symbol](../standard-library/moneypunct-class.md#curr_symbol) 确定要生成的货币符号的元素序列。

- **fac**. [positive_sign](../standard-library/moneypunct-class.md#positive_sign) 确定要生成的正号的元素序列。

- **fac**. [negative_sign](../standard-library/moneypunct-class.md#negative_sign) 确定要生成的负号的元素序列。

- **fac**. [grouping](../standard-library/moneypunct-class.md#grouping) 确定如何对任何小数点左侧的数字进行分组。

- **fac**. [thousands_sep](../standard-library/moneypunct-class.md#thousands_sep) 确定将任何小数点左侧的数字进行分组的元素。

- **fac**. [decimal_point](../standard-library/moneypunct-class.md#decimal_point) 确定从任何小数位分隔整数位的元素。

- **fac**. [frac_digits](../standard-library/moneypunct-class.md#frac_digits) 确定任何小数点右侧的有效位数。

如果符号字符串（**fac**. `negative_sign` 或 **fac**. `positive_sign`具有多个元素，则第一个元素会在等于 **money_base::sign** 的元素在 ( **fac**. `neg_format` 或 **fac**. `pos_format`). 剩余所有元素在货币输出字段的末尾生成。

如果 **iosbase**. [标志](../standard-library/ios-base-class.md#flags) & [显示库](../standard-library/ios-functions.md#showbase)是非零的，字符串**fac**。 `curr_symbol` 将在等于 **money_base::symbol** 的元素在此格式模式中出现的位置处生成。 否则，将不生成货币符号。

如果 **fac**. **grouping** 未采用任何分组约束（其首个元素具有值 CHAR_MAX），则 **fac**. `thousands_sep` 的任何实例都不会在货币输出字段的值部分（等于 **money_base::value** 的元素在格式模式中出现的位置）生成。 如果 **fac**. `frac_digits` 为零，则在十进制数字后不会生成 **fac**. `decimal_point` 的任何实例。 否则，生成的货币输出字段会将低位 **fac**. `frac_digits` 十进制数字置于小数点右侧。

对于任何数字输出字段，都会发生填充，除非 **iosbase**. **标志** & **iosbase**。 [internal](../standard-library/ios-functions.md#internal) 不为零；将在等于 **money_base::space** 的元素在此格式模式中出现的位置处生成任何内部填充（如果确实出现该元素）。 否则，将在生成的序列之前出现内部填充。 填充字符为 **fill**。

该函数将调用 **iosbase**. **width**(0) 以便将字段宽度重置为零。

### <a name="example"></a>示例

请参阅 [put](#put) 的示例，其中虚拟成员函数由 **put** 调用。

## <a name="money_putiter_type"></a><a name="iter_type"></a>money_put：iter_type

一种类型，此类型描述输出迭代器。

```cpp
typedef OutputIterator iter_type;
```

### <a name="remarks"></a>备注

该类型是模板参数 **OutputIterator** 的同义词。

## <a name="money_putmoney_put"></a><a name="money_put"></a>money_put：money_put

`money_put` 类型的对象的构造函数。

```cpp
explicit money_put(size_t _Refs = 0);
```

### <a name="parameters"></a>参数

*_Refs*\
用于指定对象的内存管理类型的整数值。

### <a name="remarks"></a>备注

*_Refs*参数的可能值及其显著性为：

- 0：对象的生存期由包含该对象的区域设置管理。

- 1：必须手动管理对象的生存期。

- \>1：这些值未定义。

由于该析构函数受到保护，可能没有直接的示例。

构造函数用区域设置初始化其基本对象 **：：**[分面](../standard-library/locale-class.md#facet_class)（ `_Refs`。

## <a name="money_putput"></a><a name="put"></a>money_put：:p乌特

将数字或字符串转换为表示货币值的字符序列。

```cpp
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

*下一个*\
发现插入的字符串中第一个元素的迭代器。

*_Intl*\
一个布尔值，该值指示在序列中预期的货币符号的类型：如果为国际，则为 **true**，如果为国内，则为 **false**。

*_Iosbase*\
一种格式标志，设定时表示货币符号是可选项；否则，它是必需项

*_Fill*\
用于调整间距的字符。

*瓦尔*\
要转换的字符串对象。

### <a name="return-value"></a>返回值

发现超出生成的最后一个元素的位置的输出迭代器。

### <a name="remarks"></a>备注

两个成员函数返回[do_put](#do_put) `next` `_Intl`（、 `_Iosbase` `_Fill`、 `val`、 、

### <a name="example"></a>示例

```cpp
// money_put_put.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>

int main()
{
    std::locale loc( "german_germany" );
    std::basic_stringstream<char> psz;

    psz.imbue(loc);
    psz.flags(psz.flags() | std::ios_base::showbase); // force the printing of the currency symbol
    std::use_facet<std::money_put<char> >(loc).put(std::basic_ostream<char>::_Iter(psz.rdbuf()), true, psz, ' ', 100012);
    if (psz.fail())
        std::cout << "money_put() FAILED" << std::endl;
    else
        std::cout << "money_put() = \"" << psz.rdbuf()->str() << "\"" << std::endl;
}
```

```Output
money_put() = "EUR1.000,12"
```

## <a name="money_putstring_type"></a><a name="string_type"></a>money_put：string_type

一种类型，此类型描述包含 `CharType` 类型字符的字符串。

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>备注

类型描述类模板的专门化[basic_string](../standard-library/basic-string-class.md)其对象可以存储源序列中的元素序列。

## <a name="see-also"></a>另请参阅

[\<区域设置>](../standard-library/locale.md)\
[分面类](../standard-library/locale-class.md#facet_class)\
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)

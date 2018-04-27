---
title: time_get 类 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- xloctime/std::time_get
- locale/std::time_get::char_type
- locale/std::time_get::iter_type
- locale/std::time_get::date_order
- locale/std::time_get::do_date_order
- locale/std::time_get::do_get
- locale/std::time_get::do_get_date
- locale/std::time_get::do_get_monthname
- locale/std::time_get::do_get_time
- locale/std::time_get::do_get_weekday
- locale/std::time_get::do_get_year
- locale/std::time_get::get
- locale/std::time_get::get_date
- locale/std::time_get::get_monthname
- locale/std::time_get::get_time
- locale/std::time_get::get_weekday
- locale/std::time_get::get_year
dev_langs:
- C++
helpviewer_keywords:
- std::time_get [C++]
- std::time_get [C++], char_type
- std::time_get [C++], iter_type
- std::time_get [C++], date_order
- std::time_get [C++], do_date_order
- std::time_get [C++], do_get
- std::time_get [C++], do_get_date
- std::time_get [C++], do_get_monthname
- std::time_get [C++], do_get_time
- std::time_get [C++], do_get_weekday
- std::time_get [C++], do_get_year
- std::time_get [C++], get
- std::time_get [C++], get_date
- std::time_get [C++], get_monthname
- std::time_get [C++], get_time
- std::time_get [C++], get_weekday
- std::time_get [C++], get_year
ms.assetid: 869d5f5b-dbab-4628-8333-bdea7e272023
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 45b0a4ea5f6197c52f0f8123d9eb3f1a40da4195
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="timeget-class"></a>time_get 类

此模板类描述可用作区域设置 facet 的对象，此对象用于控制 `CharType` 类型序列到时间值的转换。

## <a name="syntax"></a>语法

```cpp
template <class CharType,
    class InputIterator = istreambuf_iterator<CharType>>
class time_get : public time_base;
```

### <a name="parameters"></a>参数

`CharType` 用于在程序内的字符进行编码的类型。

`InputIterator` 从中读取时间值的迭代器。

## <a name="remarks"></a>备注

对于任何区域设置 facet，静态对象 ID 的初始存储值为零。 首次尝试访问其存储值后，将在 **ID** 中存储唯一正值。

### <a name="constructors"></a>构造函数

|构造函数|描述|
|-|-|
|[time_get](#time_get)|`time_get` 类型的对象的构造函数。|

### <a name="typedefs"></a>Typedef

|类型名称|描述|
|-|-|
|[char_type](#char_type)|一种类型，此类型用于描述区域设置使用的字符。|
|[iter_type](#iter_type)|一种类型，此类型描述输入迭代器。|

### <a name="member-functions"></a>成员函数

|成员函数|描述|
|-|-|
|[date_order](#date_order)|返回 facet 使用的日期顺序。|
|[do_date_order](#do_date_order)|为返回 facet 使用的日期顺序而调用的受保护虚拟成员函数。|
|[do_get](#do_get)|读取字符数据并转换为时间值。|
|[do_get_date](#do_get_date)|一种受保护的虚拟成员函数，通过调用此函数可分析作为 `x` 的 `strftime` 说明符所生成日期的字符串。|
|[do_get_monthname](#do_get_monthname)|为分析作为月份名称的字符串而调用的受保护虚拟函数。|
|[do_get_time](#do_get_time)|一种受保护的虚拟成员函数，通过调用此函数可分析作为 `X` 的 `strftime` 说明符所生成日期的字符串。|
|[do_get_weekday](#do_get_weekday)|为分析作为周日期名称的字符串而调用的受保护虚拟成员函数。|
|[do_get_year](#do_get_year)|为分析作为年份名称的字符串而调用的受保护虚拟成员函数。|
|[get](#get)|从字符数据源读取，并将此数据转换为存储在时间结构中的时间。|
|[get_date](#get_date)|分析作为 `x` 的 `strftime` 说明符所生成日期的字符串。|
|[get_monthname](#get_monthname)|分析作为月份名称的字符串。|
|[get_time](#get_time)|分析作为 `X` 的 `strftime` 说明符所生成日期的字符串。|
|[get_weekday](#get_weekday)|分析作为周日期名称的字符串。|
|[get_year](#get_year)|分析作为年份名称的字符串。|

## <a name="requirements"></a>要求

**标头：** \<locale>

**命名空间：** std

## <a name="char_type"></a>  time_get::char_type

一种类型，此类型用于描述区域设置使用的字符。

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>备注

该类型是模板参数 **CharType** 的同义词。

## <a name="date_order"></a>  time_get::date_order

返回 facet 使用的日期顺序。

```cpp
dateorder date_order() const;
```

### <a name="return-value"></a>返回值

facet 使用的日期顺序。

### <a name="remarks"></a>备注

此成员函数返回 [do_date_order](#do_date_order)。

### <a name="example"></a>示例

```cpp
// time_get_date_order.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
void po( char *p )
{
   locale loc( p );

   time_get <char>::dateorder order = use_facet <time_get <char> >( loc ).date_order ( );
   cout << loc.name( );
   switch (order){
      case time_base::dmy: cout << "(day, month, year)" << endl;
      break;
      case time_base::mdy: cout << "(month, day, year)" << endl;
      break;
      case time_base::ydm: cout << "(year, day, month)" << endl;
      break;
      case time_base::ymd: cout << "(year, month, day)"<< endl;
      break;
      case time_base::no_order: cout << "(no_order)"<< endl;
      break;
   }
}

int main( )
{
   po( "C" );
   po( "german" );
   po( "English_Britain" );
}
```

```Output
C(month, day, year)
German_Germany.1252(day, month, year)
English_United Kingdom.1252(day, month, year)
```

## <a name="do_date_order"></a>  time_get::do_date_order

为返回 facet 使用的日期顺序而调用的受保护虚拟成员函数。

```cpp
virtual dateorder do_date_order() const;
```

### <a name="return-value"></a>返回值

facet 使用的日期顺序。

### <a name="remarks"></a>备注

受保护的虚拟成员函数返回类型为 **time_base::dateorder** 的值，该值描述与 [do_get_date](#do_get_date) 匹配的日期组件的顺序。 在此实现中，值为 **time_base::mdy**，对应为 12 月 2 日，1979 年。

### <a name="example"></a>示例

请参阅 [date_order](#date_order) 示例，它调用 `do_date_order`。

## <a name="do_get"></a>  time_get::do_get

读取字符数据并转换为时间值。 接受一个转换说明符和修饰符。

```cpp
virtual iter_type
    do_get(
 iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm,
    char fmt,
    char mod) const;
```

### <a name="parameters"></a>参数

`first` 一个输入迭代器，指示要转换的序列的开头。

`last` 指示序列末尾的输入迭代器。

`iosbase` 一个流对象。

`state` Iosbase 中设置相应的位掩码元素来指示错误的字段。

`ptm` 指向要存储时间的时间结构的指针。

`fmt` 一个转换说明符字符。

`mod` 一个可选修饰符字符。

### <a name="return-value"></a>返回值

返回一个迭代器，该迭代器指定第一个未经转换的元素。 转换失败会在 `state` 中设置 `ios_base::failbit` 并返回 `first`。

### <a name="remarks"></a>备注

虚拟成员函数将转换并跳过一个或多个输入范围中的元素 [`first`， `last`) 来确定的一个或多个成员中存储的值`*pt`。 转换失败会在 `state` 中设置 `ios_base::failbit` 并返回 `first`。 否则，该函数返回指定第一个未转换元素的迭代器。

转换说明符是：

`'a'` 或 `'A'` - 与 [time_get::get_weekday](#get_weekday) 的行为相同。

`'b'`、`'B'` 或 `'h'` -- 与 [time_get::get_monthname](#get_monthname) 的行为相同。

`'c'` -- 与 `"%b %d %H : %M : %S %Y"` 的行为相同。

`'C'` -- 将 [0，99] 范围内的一个十进制输入字段转换为值 `val`，并将 `val * 100 - 1900` 存储在 `pt-&tm_year` 中。

`'d'` 或 `'e'` -- 转换 [1，31] 范围内的一个十进制输入字段，并且其将值存储在 `pt-&tm_mday` 中。

`'D'` -- 与 `"%m / %d / %y"` 的行为相同。

`'H'` -- 转换 [0，23] 范围内的一个十进制输入字段，并将其值存储在 `pt-&tm_hour` 中。

`'I'` -- 转换 [0，11] 范围内的一个十进制输入字段，并将其值存储在 `pt-&tm_hour` 中。

`'j'` -- 转换 [1，366] 范围内的一个十进制输入字段，并将其值存储在 `pt-&tm_yday` 中。

`'m'` -- 将 [1，12] 范围内的一个十进制输入字段转换为值 `val`，存储 `val - 1`，并将其值存储在 `pt-&tm_mon` 中。

`'M'` -- 转换 [0，59] 范围内的一个十进制输入字段，并将其值存储在 `pt-&tm_min` 中。

`'n'` 或 `'t'` -- 与 `" "` 的行为相同。

`'p'` -- 将“AM”或“am”转换为零，将“PM”或“pm”转换为 12，并将此值添加到 `pt-&tm_hour`。

`'r'` -- 与 `"%I : %M : %S %p"` 的行为相同。

`'R'` -- 与 `"%H %M"` 的行为相同。

`'S'` -- 转换 [0，59] 范围内的一个十进制输入字段，并将其值存储在 `pt-&tm_sec` 中。

`'T'` 或 `'X'` -- 与 `"%H : %M : S"` 的行为相同。

`'U'` -- 转换 [0，53] 范围内的一个十进制输入字段，并将其值存储在 `pt-&tm_yday` 中。

`'w'` -- 转换 [0，6] 范围内的一个十进制输入字段，并将其值存储在 `pt-&tm_wday` 中。

`'W'` -- 转换 [0，53] 范围内的一个十进制输入字段，并将其值存储在 `pt-&tm_yday` 中。

`'x'` -- 与 `"%d / %m / %y"` 的行为相同。

`'y'` -- 将 [0，99] 范围内的一个十进制输入字段转换为值 `val`，并将 `val < 69  val + 100 : val` 存储在 `pt-&tm_year` 中。

`'Y'` -- 与 [time_get::get_year](#get_year) 的行为相同。

任何其他转换说明符设置 `state` 中的 `ios_base::failbit` 并返回。 在此实现中，任何修饰符都无效。

## <a name="do_get_date"></a>  time_get::do_get_date

一种受保护的虚拟成员函数，通过调用此函数可分析作为 `strftime` 的 *x* 说明符所生成日期的字符串。

```cpp
virtual iter_type do_get_date(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>参数

`first` 发现要转换的序列的开头的输入迭代器。

`last` 发现要转换的序列的末尾的输入迭代器。

`iosbase` 一种格式标志的时设定，表示货币符号是可选的;否则，它是必需的。

`state` 设置根据操作是否成功的流状态的相应位掩码元素。

`ptm` 指向其中的日期信息是要存储的指针。

### <a name="return-value"></a>返回值

一个输入迭代器，确定第一个超出输入字段的元素位置。

### <a name="remarks"></a>备注

受保护的虚拟成员函数首先会在序列 [ `first`, `last`) 中尝试匹配有序元素，直到识别到完整的非空日期输入字段。 如果成功，它将转换此字段为其等效值的组件**tm::tm\_mon**， **tm::tm\_天**，和**tm::tm\_年**，并将存储中的结果`ptm->tm_mon`， `ptm->tm_day`，和`ptm->tm_year`分别。 它将返回一个迭代器，指定第一个超出日期输入字段的元素。 否则，该函数将设置`iosbase::failbit`中`state`。 它将返回一个迭代器，指定第一个超出有效日期输入字段的任何前缀的元素。 在任一情况下，如果返回的值等于 `last`，该函数在 `state` 中设置 `ios_base::eofbit`。

日期输入字段的格式依赖于区域设置。 对于默认区域设置，日期输入字段的格式为 MMM DD，YYYY，其中：

- MMM 通过调用 [get_monthname](#get_monthname) 得到，表示月份。

- DD 是十进制数字的序列，其对应的数值必须在 [1, 31] 范围内，表示月份中的天数。

- YYYY 通过调用 [get_year](#get_year) 得到，表示年份。

字面空格和逗号必须匹配输入序列中相应的元素。

### <a name="example"></a>示例

请参阅 [get_date](#get_date) 的示例，它调用 `do_get_date`。

## <a name="do_get_monthname"></a>  time_get::do_get_monthname

为分析作为月份名称的字符串而调用的受保护虚拟函数。

```cpp
virtual iter_type do_get_monthname(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>参数

`first` 发现要转换的序列的开头的输入迭代器。

`last` 发现要转换的序列的末尾的输入迭代器。

`iosbase` 未使用。

`state` 设置根据操作是否成功的流状态的相应位掩码元素一个输出参数。

`ptm` 指向月份信息其中是要存储的指针。

### <a name="return-value"></a>返回值

一个输入迭代器，确定第一个超出输入字段的元素位置。

### <a name="remarks"></a>备注

受保护的虚拟成员函数首先会在序列 [ `first`， `last`) 中尝试匹配有序元素，直到识别到完整的非空月份输入字段。 如果成功，它将转换此字段为其等效值作为组件**tm::tm\_mon**，并将存储中的结果`ptm->tm_mon`。 它将返回一个迭代器，指定第一个超出月份输入字段的元素。 否则，该函数将设置`ios_base::failbit`中*状态*。 它将返回一个迭代器，指定第一个超出月份输入字段的任何前缀的元素。 在任一情况下，如果返回的值等于`last`，函数集`ios_base::eofbit`中*状态*。

月份输入字段是匹配最长的一组特定于区域序列的序列，如 1 月、2 月、3 月、4 月等。 转换后的值是自 1 月份以来的月数。

### <a name="example"></a>示例

请参阅 [get_monthname](#get_monthname) 的示例，它调用 `do_get_monthname`。

## <a name="do_get_time"></a>  time_get::do_get_time

一种受保护的虚拟成员函数，通过调用此函数可分析作为 `strftime` 的 *X* 说明符所生成日期的字符串。

```cpp
virtual iter_type do_get_time(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>参数

`first` 发现要转换的序列的开头的输入迭代器。

`last` 发现要转换的序列的末尾的输入迭代器。

`iosbase` 未使用。

`state` 设置根据操作是否成功的流状态的相应位掩码元素。

`ptm` 指向其中的日期信息是要存储的指针。

### <a name="return-value"></a>返回值

一个输入迭代器，确定第一个超出输入字段的元素位置。

### <a name="remarks"></a>备注

受保护的虚拟成员函数首先会在序列 [ `first`， `last`) 中尝试匹配有序元素，直到识别到完整的非空时间输入字段。 如果成功，它将转换此字段为其等效值的组件**tm::tm_hour**， **tm::tm_min**，和**tm::tm_sec**，并将存储在结果`ptm->tm_hour`， `ptm->tm_min`，和`ptm->tm_sec`分别。 它将返回一个迭代器，指定第一个超出时间输入字段的元素。 否则，该函数将设置`ios_base::failbit`中*状态*。 它将返回一个迭代器，指定第一个超出时间输入字段的元素。 在任一情况下，如果返回的值等于`last`，函数集`ios_base::eofbit`中*状态*。

在此实现中，时间输入字段采用以下格式：HH:MM:SS，其中：

- HH 是十进制数字的序列，其对应的数值必须在 [0，24）范围内，表示小时。

- MM 是十进制数字的序列，其对应的数值必须在 [0，60）范围内，表示分钟。

- SS 是十进制数字的序列，其对应的数值必须在 [0，60）范围内，表示秒。

字面冒号必须匹配输入序列中相应的元素。

### <a name="example"></a>示例

请参阅 [get_time](#get_time) 的示例，它调用 `do_get_time`。

## <a name="do_get_weekday"></a>  time_get::do_get_weekday

为分析作为周日期名称的字符串而调用的受保护虚拟成员函数。

```cpp
virtual iter_type do_get_weekday(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>参数

`first` 发现要转换的序列的开头的输入迭代器。

`last` 发现要转换的序列的末尾的输入迭代器。

`iosbase` 一种格式标志的时设定，表示货币符号是可选的;否则，它是必需的。

`state` 设置根据操作是否成功的流状态的相应位掩码元素。

`ptm` 指向工作日信息其中是要存储的指针。

### <a name="return-value"></a>返回值

一个输入迭代器，确定第一个超出输入字段的元素位置。

### <a name="remarks"></a>备注

受保护的虚拟成员函数在序列 [`first`，`last`) 的 `first` 中尝试匹配有序元素，直到识别到完整的非空工作日输入字段。 如果成功，它将转换此字段为其等效值作为组件**tm::tm\_wday**，并将存储中的结果`ptm->tm_wday`。 它将返回一个迭代器，指定第一个超出工作日输入字段的元素。 否则，该函数将设置`ios_base::failbit`中*状态*。 它将返回一个迭代器，指定第一个超出有效工作日输入字段的任何前缀的元素。 在任一情况下，如果返回的值等于`last`，函数集`ios_base::eofbit`中*状态*。

工作日输入字段是匹配最长的一组特定于区域序列的序列，如周日（星期日）、周一（星期一）等。 转换后的值是自星期日以来的天数。

### <a name="example"></a>示例

请参阅 [get_weekday](#get_weekday) 的示例，它调用 `do_get_weekday`。

## <a name="do_get_year"></a>  time_get::do_get_year

为分析作为年份名称的字符串而调用的受保护虚拟成员函数。

```cpp
virtual iter_type do_get_year(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>参数

`first` 发现要转换的序列的开头的输入迭代器。

`last` 发现要转换的序列的末尾的输入迭代器。

`iosbase` 一种格式标志的时设定，表示货币符号是可选的;否则，它是必需的。

`state` 设置根据操作是否成功的流状态的相应位掩码元素。

`ptm` 指向其中年信息是要存储的指针。

### <a name="return-value"></a>返回值

一个输入迭代器，确定第一个超出输入字段的元素位置。

### <a name="remarks"></a>备注

受保护的虚拟成员函数在序列 [`first`，`last`) 的 `first` 中尝试匹配有序元素，直到识别到完整的非空年份输入字段。 如果成功，它将转换此字段为其等效值作为组件**tm::tm\_年**，并将存储中的结果`ptm->tm_year`。 它将返回一个迭代器，指定第一个超出年份输入字段的元素。 否则，该函数将设置`ios_base::failbit`中*状态*。 它将返回一个迭代器，指定第一个超出有效年份输入字段的元素。 在任一情况下，如果返回的值等于`last`，函数集`ios_base::eofbit`中*状态*。

年份输入字段是十进制数字的序列，其对应的数值必须在 [1900, 2036) 范围内。 存储的值为此值减去 1900。 在此实现中，值范围 [69, 136) 表示年份范围 [1969、2036）。 也可使用值范围 [0, 69)，但可能表示年份范围 [1900, 1969) 或 [2000, 2069)，具体取决于转换环境。

### <a name="example"></a>示例

请参阅 [get_year](#get_year) 的示例，它调用 `do_get_year`。

## <a name="get"></a>  time_get::get

从字符数据源读取，并将此数据转换为存储在时间结构中的时间。 第一个函数接受一个转换说明符和修饰符，而第二个接受多个。

```cpp
iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm,
    char fmt,
    char mod) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm,
    char_type* fmt_first,
    char_type* fmt_last) const;
```

### <a name="parameters"></a>参数

`first` 指示要转换的序列开始的位置的输入迭代器。

`last` 指示要转换的序列的末尾的输入迭代器。

`iosbase` 流。

`state` 相应的位掩码元素设置为流状态，以指示错误。

`ptm` 指向要存储时间的时间结构的指针。

`fmt` 一个转换说明符字符。

`mod` 一个可选修饰符字符。

`fmt_first` 指向格式指令开始的位置。

`fmt_last` 指向格式指令结束。

### <a name="return-value"></a>返回值

返回一个迭代器用于分配时间结构的数据后的第一个字符`*ptm`。

### <a name="remarks"></a>备注

第一个成员函数返回 `do_get(first, last, iosbase, state, ptm, fmt, mod)`。

第二个成员函数调用以 `[fmt_first, fmt_last)` 分隔的格式的控件下的 `do_get`。 它将格式视为一个字段序列，其中每个字段确定了以 `[first, last)` 分隔的 0 个或多个输入元素的转换。 它返回一个迭代器，指定第一个未转换的元素。 有三种类型的字段：

百分号 （%） 格式后, 跟一个可选修饰符`mod`集中 [EOQ #] 后, 跟一个转换说明符`fmt`，替换`first`返回的值与`do_get(first, last, iosbase, state, ptm, fmt, mod)`。 转换失败会在 `state` 中设置 `ios_base::failbit` 并进行返回。

格式中的空白元素会跳过零个或多个输入空白元素。

格式中的任何其他元素必须匹配下一个输入元素，它会被跳过。 匹配失败会在 `state` 中设置 `ios_base::failbit` 并进行返回。

## <a name="get_date"></a>  time_get::get_date

分析作为 `strftime` 的 *x* 说明符所生成日期的字符串。

```cpp
iter_type get_date(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>参数

`first` 发现要转换的序列的开头的输入迭代器。

`last` 发现要转换的序列的末尾的输入迭代器。

`iosbase` 一种格式标志的时设定，表示货币符号是可选的;否则，它是必需的。

`state` 设置根据操作是否成功的流状态的相应位掩码元素。

`ptm` 指向其中的日期信息是要存储的指针。

### <a name="return-value"></a>返回值

一个输入迭代器，确定第一个超出输入字段的元素位置。

### <a name="remarks"></a>备注

成员函数返回 [do_get_date](#do_get_date)( `first`、`last`、`iosbase`、`state` 和 `ptm`)。

请注意，月份从 0 到 11 进行计算。

### <a name="example"></a>示例

```cpp
// time_get_get_date.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
int main( )
{
   locale loc;
   basic_stringstream< char > pszGetF, pszPutF, pszGetI, pszPutI;
   ios_base::iostate st = 0;
   struct tm t;
   memset(&t, 0, sizeof(struct tm));

   pszGetF << "July 4, 2000";
   pszGetF.imbue( loc );
   basic_istream<char>::_Iter i = use_facet <time_get<char> >
   (loc).get_date(basic_istream<char>::_Iter(pszGetF.rdbuf( ) ),
            basic_istream<char>::_Iter(0), pszGetF, st, &t);

   if ( st & ios_base::failbit )
      cout << "time_get("<< pszGetF.rdbuf( )->str( )<< ") FAILED on char: " << *i << endl;
   else

      cout << "time_get("<< pszGetF.rdbuf( )->str( )<< ") ="
      << "\ntm_sec: " << t.tm_sec
      << "\ntm_min: " << t.tm_min
      << "\ntm_hour: " << t.tm_hour
      << "\ntm_mday: " << t.tm_mday
      << "\ntm_mon: " << t.tm_mon
      << "\ntm_year: " << t.tm_year
      << "\ntm_wday: " << t.tm_wday
      << "\ntm_yday: " << t.tm_yday
      << "\ntm_isdst: " << t.tm_isdst
      << endl;
}
```

```Output
time_get(July 4, 2000) =
tm_sec: 0
tm_min: 0
tm_hour: 0
tm_mday: 4
tm_mon: 6
tm_year: 100
tm_wday: 0
tm_yday: 0
tm_isdst: 0
```

## <a name="get_monthname"></a>  time_get::get_monthname

分析作为月份名称的字符串。

```cpp
iter_type get_monthname(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>参数

`first` 发现要转换的序列的开头的输入迭代器。

`last` 发现要转换的序列的末尾的输入迭代器。

`iosbase` 未使用。

`state` 设置根据操作是否成功的流状态的相应位掩码元素一个输出参数。

`ptm` 指向月份信息其中是要存储的指针。

### <a name="return-value"></a>返回值

一个输入迭代器，确定第一个超出输入字段的元素位置。

### <a name="remarks"></a>备注

成员函数返回 [do_get_monthname](#do_get_monthname)( `first`、`last`、`iosbase`、`state` 和 `ptm`)。

### <a name="example"></a>示例

```cpp
// time_get_get_monthname.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
int main( )
{
   locale loc ( "French" );
   basic_stringstream<char> pszGetF, pszPutF, pszGetI, pszPutI;
   ios_base::iostate st = 0;
   struct tm t;
   memset( &t, 0, sizeof( struct tm ) );

   pszGetF << "juillet";
   pszGetF.imbue( loc );
   basic_istream<char>::_Iter i = use_facet <time_get <char> >
   (loc).get_monthname(basic_istream<char>::_Iter(pszGetF.rdbuf( )),
              basic_istream<char>::_Iter(0), pszGetF, st, &t);

   if (st & ios_base::failbit)
      cout << "time_get("<< pszGetF.rdbuf( )->str( )<< ") FAILED on char: " << *i << endl;
   else

      cout << "time_get("<< pszGetF.rdbuf( )->str( )<< ") ="
      << "\ntm_sec: " << t.tm_sec
      << "\ntm_min: " << t.tm_min
      << "\ntm_hour: " << t.tm_hour
      << "\ntm_mday: " << t.tm_mday
      << "\ntm_mon: " << t.tm_mon
      << "\ntm_year: " << t.tm_year
      << "\ntm_wday: " << t.tm_wday
      << "\ntm_yday: " << t.tm_yday
      << "\ntm_isdst: " << t.tm_isdst
      << endl;
}
```

```Output
time_get(juillet) =
tm_sec: 0
tm_min: 0
tm_hour: 0
tm_mday: 0
tm_mon: 6
tm_year: 0
tm_wday: 0
tm_yday: 0
tm_isdst: 0
```

## <a name="get_time"></a>  time_get::get_time

分析作为 `strftime` 的 *X* 说明符所生成日期的字符串。

```cpp
iter_type get_time(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>参数

`first` 发现要转换的序列的开头的输入迭代器。

`last` 发现要转换的序列的末尾的输入迭代器。

`iosbase` 未使用。

`state` 设置根据操作是否成功的流状态的相应位掩码元素。

`ptm` 指向其中的日期信息是要存储的指针。

### <a name="return-value"></a>返回值

一个输入迭代器，确定第一个超出输入字段的元素位置。

### <a name="remarks"></a>备注

成员函数返回 [do_get_time](#do_get_time)( `first`、`last``iosbase``state` 和 `ptm`)。

### <a name="example"></a>示例

```cpp
// time_get_get_time.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
int main( )
{
   locale loc;
   basic_stringstream<char> pszGetF, pszPutF, pszGetI, pszPutI;
   ios_base::iostate st = 0;
   struct tm t;
   memset( &t, 0, sizeof( struct tm ) );

   pszGetF << "11:13:20";
   pszGetF.imbue( loc );
   basic_istream<char>::_Iter i = use_facet
      <time_get <char> >
      (loc).get_time(basic_istream<char>::_Iter(pszGetF.rdbuf( )),
               basic_istream<char>::_Iter(0), pszGetF, st, &t);

   if (st & ios_base::failbit)
      cout << "time_get::get_time("<< pszGetF.rdbuf( )->str( )<< ") FAILED on char: " << *i << endl;
   else

      cout << "time_get::get_time("<< pszGetF.rdbuf( )->str( )<< ") ="
      << "\ntm_sec: " << t.tm_sec
      << "\ntm_min: " << t.tm_min
      << "\ntm_hour: " << t.tm_hour
      << endl;
}
```

```Output
time_get::get_time(11:13:20) =
tm_sec: 20
tm_min: 13
tm_hour: 11
```

## <a name="get_weekday"></a>  time_get::get_weekday

分析作为周日期名称的字符串。

```cpp
iter_type get_weekday(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>参数

`first` 发现要转换的序列的开头的输入迭代器。

`last` 发现要转换的序列的末尾的输入迭代器。

`iosbase` 一种格式标志的时设定，表示货币符号是可选的;否则，它是必需的。

`state` 设置根据操作是否成功的流状态的相应位掩码元素。

`ptm` 指向工作日信息其中是要存储的指针。

### <a name="return-value"></a>返回值

一个输入迭代器，确定第一个超出输入字段的元素位置。

### <a name="remarks"></a>备注

成员函数返回 [do_get_weekday](#do_get_weekday)( `first`、`last``iosbase``state` 和 `ptm`)。

### <a name="example"></a>示例

```cpp
// time_get_get_weekday.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
int main( )
{
   locale loc ( "French" );
   basic_stringstream< char > pszGetF, pszPutF, pszGetI, pszPutI;
   ios_base::iostate st = 0;
   struct tm t;
   memset( &t, 0, sizeof( struct tm ) );

   pszGetF << "mercredi";
   pszGetF.imbue(loc);
   basic_istream<char>::_Iter i = use_facet
      <time_get<char> >
      (loc).get_weekday(basic_istream<char>::_Iter(pszGetF.rdbuf( )),
               basic_istream<char>::_Iter(0), pszGetF, st, &t);

   if (st & ios_base::failbit)
      cout << "time_get::get_time("<< pszGetF.rdbuf( )->str( )<< ") FAILED on char: " << *i << endl;
   else

      cout << "time_get::get_time("<< pszGetF.rdbuf( )->str( )<< ") ="
      << "\ntm_wday: " << t.tm_wday
      << endl;
}
```

```Output
time_get::get_time(mercredi) =
tm_wday: 3
```

## <a name="get_year"></a>  time_get::get_year

分析作为年份名称的字符串。

```cpp
iter_type get_year(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>参数

`first` 发现要转换的序列的开头的输入迭代器。

`last` 发现要转换的序列的末尾的输入迭代器。

`iosbase` 一种格式标志的时设定，表示货币符号是可选的;否则，它是必需的。

`state` 设置根据操作是否成功的流状态的相应位掩码元素。

`ptm` 指向其中年信息是要存储的指针。

### <a name="return-value"></a>返回值

一个输入迭代器，确定第一个超出输入字段的元素位置。

### <a name="remarks"></a>备注

成员函数返回 [do_get_year](#do_get_year)( `first`、`last``iosbase``state` 和 `ptm`)。

### <a name="example"></a>示例

```cpp
// time_get_get_year.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
int main( )
{
   locale loc;
   basic_stringstream<char> pszGetF, pszPutF, pszGetI, pszPutI;
   ios_base::iostate st = 0;
   struct tm t;
   memset( &t, 0, sizeof( struct tm ) );

   pszGetF << "1928";

   pszGetF.imbue( loc );
   basic_istream<char>::_Iter i = use_facet
      <time_get<char> >
      (loc).get_year(basic_istream<char>::_Iter(pszGetF.rdbuf( )),
               basic_istream<char>::_Iter(0), pszGetF, st, &t);

   if (st & ios_base::failbit)
      cout << "time_get::get_year("<< pszGetF.rdbuf( )->str( )<< ") FAILED on char: " << *i << endl;
   else

      cout << "time_get::get_year("<< pszGetF.rdbuf( )->str( )<< ") ="
      << "\ntm_year: " << t.tm_year
      << endl;
}
```

```Output
time_get::get_year(1928) =
tm_year: 28
```

## <a name="iter_type"></a>  time_get::iter_type

一种类型，此类型描述输入迭代器。

```cpp
typedef InputIterator iter_type;
```

### <a name="remarks"></a>备注

该类型是模板参数 **InputIterator** 的同义词。

## <a name="time_get"></a>  time_get::time_get

`time_get` 类型的对象的构造函数。

```cpp
explicit time_get(size_t refs = 0);
```

### <a name="parameters"></a>参数

`refs` 用于指定类型的对象的内存管理的整数值。

### <a name="remarks"></a>备注

`refs` 参数可能的值及其含义：

- 0：对象的生存期由包含该对象的区域设置管理。

- 1：必须手动管理对象的生存期。

- \> 1： 未定义这些值。

由于该析构函数受到保护，可能没有直接的示例。

构造函数通过 **locale::**[facet](../standard-library/locale-class.md#facet_class)( `refs`) 初始化其基对象。

## <a name="see-also"></a>请参阅

[\<locale>](../standard-library/locale.md)<br/>
[time_base 类](../standard-library/time-base-class.md)<br/>
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>

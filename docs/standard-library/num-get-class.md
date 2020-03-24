---
title: num_get 类
ms.date: 11/04/2016
f1_keywords:
- xlocnum/std::num_get
- locale/std::num_get::char_type
- locale/std::num_get::iter_type
- locale/std::num_get::do_get
- locale/std::num_get::get
helpviewer_keywords:
- std::num_get [C++]
- std::num_get [C++], char_type
- std::num_get [C++], iter_type
- std::num_get [C++], do_get
- std::num_get [C++], get
ms.assetid: 9933735d-3918-4b17-abad-5fca2adc62d7
ms.openlocfilehash: 58ff645a381fd55c591a2566b2e698f0e9821935
ms.sourcegitcommit: eff68e4e82be292a5664616b16a526df3e9d1cda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80150611"
---
# <a name="num_get-class"></a>num_get 类

一个类模板，用于描述一个对象，该对象可充当区域设置 facet，以控制 `CharType` 类型为数值的序列的转换。

## <a name="syntax"></a>语法

```cpp
template <class CharType, class InputIterator = istreambuf_iterator<CharType>>
class num_get : public locale::facet;
```

### <a name="parameters"></a>parameters

*CharType*\
在程序中用于对区域设置中的字符进行编码的类型。

*InputIterator*\
数值获取函数从中读取其输入的迭代器类型。

## <a name="remarks"></a>备注

对于任何区域设置 facet，静态对象 ID 的初始存储值为零。 首次尝试访问其存储值后，将在 **id** 中存储唯一的正值。

### <a name="constructors"></a>构造函数

|构造函数|说明|
|-|-|
|[num_get](#num_get)|用于从序列提取数值的 `num_get` 类型对象的构造函数。|

### <a name="typedefs"></a>Typedef

|类型名称|说明|
|-|-|
|[char_type](#char_type)|一种类型，此类型用于描述区域设置使用的字符。|
|[iter_type](#iter_type)|一种类型，此类型描述输入迭代器。|

### <a name="member-functions"></a>成员函数

|成员函数|说明|
|-|-|
|[do_get](#do_get)|为从字符序列提取数值或布尔值而调用的虚拟函数。|
|[get](#get)|从字符序列提取数值或布尔值。|

## <a name="requirements"></a>要求

**标头：** \<区域设置 >

**命名空间:** std

## <a name="num_getchar_type"></a><a name="char_type"></a>  num_get::char_type

一种类型，此类型用于描述区域设置使用的字符。

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>备注

该类型是模板参数 **CharType** 的同义词。

## <a name="num_getdo_get"></a><a name="do_get"></a>  num_get::do_get

为从字符序列提取数值或布尔值而调用的虚拟函数。

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned short& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned int& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    float& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    double& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long double& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    void *& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    bool& val) const;
```

### <a name="parameters"></a>parameters

*第一个*\
从其中读取数字的字符范围的起始处。

*最后*\
从其中读取数字的字符范围的末尾处。

*iosbase*\
[Ios_base](../standard-library/ios-base-class.md)，其标志由转换使用。

*状态*\
发生故障时向其添加 failbit（请参阅 [ios_base::iostate](../standard-library/ios-base-class.md#iostate)）的状态。

*val*\
读取的值。

### <a name="return-value"></a>返回值

读取值后的迭代器。

### <a name="remarks"></a>备注

第一个受保护的虚拟成员函数，

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long& val) const;
```

匹配序列中的*第一个*序列元素，`[first, last)` 直到它识别完整的非空整数输入字段。 如果成功，它会将此字段转换为其等效的值作为类型**long**，并将结果存储为*val*。 它将返回一个迭代器，指定第一个超出数字输入字段的元素。 否则，该函数在*val*中存储任何内容，并在 `state`中设置 `ios_base::failbit`。 它将返回一个迭代器，指定第一个超出有效整数输入字段的任何前缀的元素。 在任一情况下，如果返回的值等于 `last`，该函数在 `ios_base::eofbit` 中设置 `state`。

整数输入字段由扫描函数使用的相同规则进行转换，以便对文件中的一系列**char**元素进行匹配和转换。 （假定每个此类**char**元素都映射到一个由简单的一对一映射 `Elem` 的类型的等效元素。）确定等效的扫描转换规范，如下所示：

如果 `iosbase.`[ios_base::flags](../standard-library/ios-base-class.md#flags)`() & ios_base::basefield == ios_base::`[oct](../standard-library/ios-functions.md#oct)，则转换规格为 `lo`。

如果 `iosbase.flags() & ios_base::basefield == ios_base::`[hex](../standard-library/ios-functions.md#hex)，则转换规格为 `lx`。

如果 `iosbase.flags() & ios_base::basefield == 0`，则转换规格为 `li`。

否则，转换规格为 `ld`。

整数输入字段的格式由`fac` 调用[use_facet](../standard-library/locale-functions.md#use_facet) `<`[numpunct](../standard-library/numpunct-class.md)`<Elem>(iosbase.`[ios_base：： getloc](../standard-library/ios-base-class.md#getloc)`())`返回的[区域设置 facet](../standard-library/locale-class.md#facet_class)进一步决定。 具体来说：

`fac.`[numpunct::grouping](../standard-library/numpunct-class.md#grouping)`()` 确定如何对任何小数点左侧的数字进行分组

`fac.`[numpunct::thousands_sep](../standard-library/numpunct-class.md#thousands_sep)`()` 确定将任何小数点左侧的数字进行分组的序列。

如果数字输入字段中没有出现 `fac.thousands_sep()` 的任何实例，则不会采用应用分组约束。 否则，会强制执行 `fac.grouping()` 采用的分组约束，并在扫描转换发生之前删除分隔符。

第四个受保护的虚拟成员函数：

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long& val) const;
```

行为与第一个相同，只不过它将转换规格 `ld` 替换为 `lu`。 如果成功，它会将数字输入字段转换为类型为 "**无符号**" 的值，并将该值存储在*val*中。

第五个受保护的虚拟成员函数：

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long long& val) const;
```

行为与第一个相同，只不过它将转换规格 `ld` 替换为 `lld`。 如果成功，它会将数字输入字段转换为**long**类型的值，并将该值存储在*val*中。

第六个受保护的虚拟成员函数：

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long long& val) const;
```

行为与第一个相同，只不过它将转换规格 `ld` 替换为 `llu`。 如果成功，它会将数字输入字段转换为类型为**无符号长**的值，并将该值存储在*val*中。

第七个受保护的虚拟成员函数：

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    float& val) const;
```

行为与第一个相同，只不过它旨在匹配完整的非空浮点输入字段。 `fac.`[numpunct::decimal_point](../standard-library/numpunct-class.md#decimal_point)`()` 确定从小数位分隔整数位的序列。 等效的扫描转换说明符是 `lf`。

第八个受保护的虚拟成员函数：

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    double& val) const;
```

行为与第一个相同，只不过它旨在匹配完整的非空浮点输入字段。 `fac.`[numpunct::decimal_point](../standard-library/numpunct-class.md#decimal_point)`()` 确定从小数位分隔整数位的序列。 等效的扫描转换说明符是 `lf`。

第九个受保护的虚拟成员函数：

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long double& val) const;
```

行为与第八个相同，只不过等效的扫描转换说明符为 `Lf`。

第10个受保护的虚拟成员函数：

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    void *& val) const;
```

行为与第一个相同，只不过等效的扫描转换说明符为 `p`。

最后一个（第十一个）受保护的虚拟成员函数：

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    bool& val) const;
```

行为与第一个相同，只不过它旨在匹配完整的非空布尔输入字段。 如果成功，它会将布尔输入字段转换为**bool**类型的值，并将该值存储在*val*中。

布尔输入字段采用以下两种形式之一。 如果 `iosbase.flags() & ios_base::`[boolalpha](../standard-library/ios-functions.md#boolalpha) 为 false，则它与整数输入字段相同，只不过转换的值必须为 0（若为 false）或 1（若为 true）。 否则，该序列必须匹配 `fac.`[numpunct::falsename](../standard-library/numpunct-class.md#falsename)`()`（若为 false）或 `fac.`[numpunct::truename](../standard-library/numpunct-class.md#truename)`()`（若为 true）。

### <a name="example"></a>示例

请参阅 [get](#get) 的示例，其中虚拟成员函数由 `do_get` 调用。

## <a name="num_getget"></a><a name="get"></a>  num_get::get

从字符序列提取数值或布尔值。

```cpp
iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    bool& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned short& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned int& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    float& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    double& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long double& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    void *& val) const;
```

### <a name="parameters"></a>parameters

*第一个*\
从其中读取数字的字符范围的起始处。

*最后*\
从其中读取数字的字符范围的末尾处。

*iosbase*\
[Ios_base](../standard-library/ios-base-class.md)，其标志由转换使用。

*状态*\
发生故障时向其添加 failbit（请参阅 [ios_base::iostate](../standard-library/ios-base-class.md#iostate)）的状态。

*val*\
读取的值。

### <a name="return-value"></a>返回值

读取值后的迭代器。

### <a name="remarks"></a>备注

所有成员函数都返回[do_get](#do_get)`( first, last, iosbase, state, val)`。

第一个受保护的虚拟成员函数首先会在序列 [ `first`, `last`) 中尝试匹配序列连续元素，直到识别到完整的非空整数输入字段。 如果成功，它会将此字段转换为其等效的值作为类型**long** ，并将结果存储在*val*中。 它将返回一个迭代器，指定第一个超出数字输入字段的元素。 否则，该函数将不会存储任何内容 *，并将*`ios_base::failbit`*状态*。 它将返回一个迭代器，指定第一个超出有效整数输入字段的任何前缀的元素。 在任一情况下，如果返回值等于*last*，则函数将 `ios_base::eofbit`*状态*设置为。

整数输入字段由扫描函数使用的相同规则进行转换，以便对文件中的一系列**char**元素进行匹配和转换。 假定每个**char**元素都映射到一个由简单的一对一映射 `CharType` 的类型的等效元素。 确定等效的扫描转换规格，如下所示：

- 如果`& ios_base::basefield == ios_base::`[oct](../standard-library/ios-functions.md#oct)`iosbase.`[标志](../standard-library/ios-base-class.md#flags)，则将 `lo`转换规范。

- 如果 `iosbase.flags & ios_base::basefield == ios_base::`[hex](../standard-library/ios-functions.md#hex)，则转换规格为 `lx`。

- 如果 `iosbase.flags & ios_base::basefield == 0`，则转换规格为 `li`。

- 否则，转换规格为 `ld`。

整数输入字段的格式由调用[use_facet](../standard-library/locale-functions.md#use_facet)`<`[`numpunct`](../standard-library/numpunct-class.md)`<Elem>(iosbase.`[getloc](../standard-library/ios-base-class.md#getloc)`())`返回的[区域设置 `fac` facet](../standard-library/locale-class.md#facet_class)进一步决定。 具体来说：

- `fac.`[分组](../standard-library/numpunct-class.md#grouping)确定如何将位数分组到任何小数点左侧。

- `fac.`[thousands_sep](../standard-library/numpunct-class.md#thousands_sep)确定分隔任意小数点左边数字组的序列。

如果数字输入字段中没有出现 `fac.thousands_sep` 的任何实例，则不会采用应用分组约束。 否则，将强制实施 `fac.grouping` 施加的任何分组约束，并在扫描转换发生之前删除分隔符。

第二个受保护的虚拟成员函数：

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long& val) const;
```

行为与第一个相同，只不过它将转换规格 `ld` 替换为 `lu`。 如果成功，它会将数字输入字段转换为类型为 "**无符号**" 的值，并将该值存储在*val*中。

第三个受保护的虚拟成员函数：

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    double& val) const;
```

行为与第一个相同，只不过它尝试匹配完整的非空浮点输入字段。 `fac.`[decimal_point](../standard-library/numpunct-class.md#decimal_point)确定将整数位与小数位分隔的顺序。 等效的扫描转换说明符是 `lf`。

第四个受保护的虚拟成员函数：

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long double& val) const;
```

的行为与第三个相同，只不过等效的扫描转换说明符是 `Lf`的。

第五个受保护的虚拟成员函数：

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    void *& val) const;
```

行为与第一个相同，只不过等效的扫描转换说明符为 `p`。

第六个受保护的虚拟成员函数：

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    bool& val) const;
```

行为与第一个相同，只不过它尝试匹配完整的非空布尔输入字段。 如果成功，它会将布尔输入字段转换为**bool**类型的值，并将该值存储在*val*中。

布尔输入字段采用以下两种形式之一。 如果 `iosbase.flags & ios_base::`[boolalpha](../standard-library/ios-functions.md#boolalpha)为**false**，则它与整数输入字段相同，不同之处在于转换后的值必须是0（对于**false**）或1（对于**true**）。 否则，序列必须与 `fac.`[falsename](../standard-library/numpunct-class.md#falsename) （对于**false**）或 `fac.`[truename](../standard-library/numpunct-class.md#truename) （对于**true**）匹配。

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

## <a name="num_getiter_type"></a><a name="iter_type"></a>  num_get::iter_type

一种类型，此类型描述输入迭代器。

```cpp
typedef InputIterator iter_type;
```

### <a name="remarks"></a>备注

该类型是模板参数 `InputIterator`的同义词。

## <a name="num_getnum_get"></a><a name="num_get"></a>  num_get::num_get

用于从序列提取数值的 `num_get` 类型对象的构造函数。

```cpp
explicit num_get(size_t refs = 0);
```

### <a name="parameters"></a>parameters

*refs*\
用于指定对象的内存管理类型的整数值。

### <a name="remarks"></a>备注

*Refs*参数的可能值及其重要性为：

- 0：对象的生存期由包含该对象的区域设置管理。

- 1：必须手动管理对象的生存期。

- \> 1：未定义这些值。

由于该析构函数受到保护，可能没有直接的示例。

构造函数`(refs)``locale::`[方面](../standard-library/locale-class.md#facet_class)初始化其基对象。

## <a name="see-also"></a>另请参阅

[\<区域设置>](../standard-library/locale.md)\
[facet 类](../standard-library/locale-class.md#facet_class)\
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)

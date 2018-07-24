---
title: ctype 类 | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xlocale/std::ctype
- xlocale/std::ctype::char_type
- xlocale/std::ctype::do_is
- xlocale/std::ctype::do_narrow
- xlocale/std::ctype::do_scan_is
- xlocale/std::ctype::do_scan_not
- xlocale/std::ctype::do_tolower
- xlocale/std::ctype::do_toupper
- xlocale/std::ctype::do_widen
- xlocale/std::ctype::is
- xlocale/std::ctype::narrow
- xlocale/std::ctype::scan_is
- xlocale/std::ctype::scan_not
- xlocale/std::ctype::tolower
- xlocale/std::ctype::toupper
- xlocale/std::ctype::widen
dev_langs:
- C++
helpviewer_keywords:
- std::ctype [C++]
- std::ctype [C++], char_type
- std::ctype [C++], do_is
- std::ctype [C++], do_narrow
- std::ctype [C++], do_scan_is
- std::ctype [C++], do_scan_not
- std::ctype [C++], do_tolower
- std::ctype [C++], do_toupper
- std::ctype [C++], do_widen
- std::ctype [C++], is
- std::ctype [C++], narrow
- std::ctype [C++], scan_is
- std::ctype [C++], scan_not
- std::ctype [C++], tolower
- std::ctype [C++], toupper
- std::ctype [C++], widen
ms.assetid: 3627154c-49d9-47b5-b28f-5bbedee38e3b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5a65008b01262ad6252e9942444a4e80602d4292
ms.sourcegitcommit: 7eadb968405bcb92ffa505e3ad8ac73483e59685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2018
ms.locfileid: "39208632"
---
# <a name="ctype-class"></a>ctype 类

一种提供一个 facet 的类，此 facet 用于对字符进行分类、转换大写和小写以及在本机字符集与区域设置使用的字符集之间进行转换。

## <a name="syntax"></a>语法

```cpp
template <class CharType>
class ctype : public ctype_base;
```

### <a name="parameters"></a>参数

*CharType*在程序中用于对字符进行编码的类型。

## <a name="remarks"></a>备注

对于任何区域设置 facet，静态对象 ID 的初始存储值为零。 首次尝试访问其存储值后，将在 `id` 中存储唯一正值。 对基类 ctype_base 中的嵌套位掩码类型提供了分类条件。

C++ 标准库定义了此模板类的两个显式专用化：

- [ctype](../standard-library/ctype-char-class.md)< `char`>，此显式专用化的不同之处将单独说明。

- **ctype**<`wchar_t`>，将元素视为宽字符。

模板类 **ctype**\< **CharType**> 的其他专用化：

- 将值转换***ch***类型的`CharType`类型的值为**char**使用表达式 (`char`) **ch**。

- 将值转换***字节***类型的**char**类型的值为`CharType`与表达式**CharType** (**字节**)。

在执行所有其他操作**char**中的相同方式与显式专用化的值**ctype**<`char`>。

### <a name="constructors"></a>构造函数

|构造函数|描述|
|-|-|
|[ctype](#ctype)|`ctype` 类对象的构造函数，该类可用作字符的区域设置 facet。|

### <a name="typedefs"></a>Typedef

|类型名称|描述|
|-|-|
|[char_type](#char_type)|一种类型，此类型描述区域设置使用的字符。|

### <a name="member-functions"></a>成员函数

|成员函数|描述|
|-|-|
|[do_is](#do_is)|一种虚拟函数，通过调用此函数可测试单个字符是否具有特定属性，或者为某个范围内的每个字符的属性进行分类并将属性存储在数组中。|
|[do_narrow](#do_narrow)|调用类型的字符转换为虚拟函数`CharType`使用的类型的相应字符的区域设置**char**本机字符集中。|
|[do_scan_is](#do_scan_is)|一种虚拟函数，通过调用此函数可查找某个范围内与指定掩码匹配的第一个字符。|
|[do_scan_not](#do_scan_not)|一种虚拟函数，通过调用此函数可查找某个范围内与指定掩码不匹配的第一个字符。|
|[do_tolower](#do_tolower)|一种虚拟函数，通过调用此函数可将一个字符或一系列字符转换为小写。|
|[do_toupper](#do_toupper)|一种虚拟函数，通过调用此函数可将一个字符或一系列字符转换为大写。|
|[do_widen](#do_widen)|类型的字符转换为虚拟函数调用到**char**类型的相应字符本机字符集中`CharType`由区域设置。|
|[is](#is)|测试单个字符是否具有特定属性，或者对某个范围内的每个字符的属性进行分类并将属性存储在数组中。|
|[narrow](#narrow)|将区域设置使用的 `CharType` 类型的字符转换为本机字符集中 char 类型的相应字符。|
|[scan_is](#scan_is)|查找某个范围内与指定掩码匹配的第一个字符。|
|[scan_not](#scan_not)|查找某个范围内与指定掩码不匹配的第一个字符。|
|[tolower](#tolower)|将一个或一些列字符转换为小写。|
|[toupper](#toupper)|将一个或一些列字符转换为大写。|
|[widen](#widen)|类型的字符转换为**char**类型的相应字符本机字符集中`CharType`由区域设置。|

## <a name="requirements"></a>要求

**标头：** \<locale>

**命名空间：** std

## <a name="char_type"></a>  ctype::char_type

一种类型，此类型描述区域设置使用的字符。

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>备注

该类型是模板参数 *CharType* 的同义词。

### <a name="example"></a>示例

有关将 `char_type` 用作返回值的示例，请参阅成员函数 [widen](#widen)。

## <a name="ctype"></a>  ctype::ctype

ctype 类对象的构造函数，该类可用作字符的区域设置 facet。

```cpp
explicit ctype(size_t _Refs = 0);
```

### <a name="parameters"></a>参数

*_Refs*整数值，该值用于指定类型的对象的内存管理。

### <a name="remarks"></a>备注

可能的值 *_Refs*参数和其重要性：

- 0：对象的生存期由包含该对象的区域设置管理。

- 1：必须手动管理对象的生存期。

- \> 1： 未定义这些值。

由于该析构函数受到保护，可能没有直接的示例。

构造函数通过 **locale::**[facet](../standard-library/locale-class.md#facet_class)( `_Refs`) 初始化其 `locale::facet` 基对象。

## <a name="do_is"></a>  ctype::do_is

一种虚拟函数，通过调用此函数可测试单个字符是否具有特定属性，或者为某个范围内的每个字符的属性进行分类并将属性存储在数组中。

```cpp
virtual bool do_is(
    mask maskVal,
    CharType ch) const;


virtual const CharType *do_is(
    const CharType* first,
    const CharType* last,
    mask* dest) const;
```

### <a name="parameters"></a>参数

*maskVal*为要测试字符的掩码值。

*ch*其属性是要测试的字符。

*第一个*指向其属性进行分类的范围中的第一个字符的指针。

*最后一个*指向其属性进行分类的范围中最后一个字符之后紧跟的字符的指针。

*dest*描述的每个字符属性特征的掩码值的存储位置的数组的开头的指针。

### <a name="return-value"></a>返回值

第一个成员函数将返回一个布尔值，如果测试的字符具有掩码值描述的属性，则为 **true**；如果它不具有此属性，则为 **false**。

第二个成员函数返回一个数组，其中包含描述范围内每个字符属性特征的掩码值。

### <a name="remarks"></a>备注

[ctype_base](../standard-library/ctype-base-class.md) 类提供了对字符属性进行分类的掩码值，从中派生 ctype。 第一个成员函数可以接受其第一个参数的表达式，该参数被称为位掩码，由逻辑按位运算符 (&#124; , & , ^ , ~) 组成的掩码值构成。

### <a name="example"></a>示例

请参阅 [is](#is) 的示例，它调用 `do_is`。

## <a name="do_narrow"></a>  ctype::do_narrow

调用类型的字符转换为虚拟函数`CharType`使用的类型的相应字符的区域设置**char**本机字符集中。

```cpp
virtual char do_narrow(
    CharType ch,
    char default = '\0') const;


virtual const CharType* do_narrow(
    const CharType* first,
    const CharType* last,
    char default,
    char* dest) const;
```

### <a name="parameters"></a>参数

*ch*类型的字符`Chartype`由要转换的区域设置。

*默认值*到字符类型的成员函数分配的默认值`CharType`不具有的类型与字符**char**。

*第一个*指向要转换的字符范围内的第一个字符的指针。

*最后一个*指向要转换的字符范围中最后一个字符之后紧跟的字符的指针。

*dest*类型的第一个字符常量指针**char**目标范围存储经过转换的字符范围内。

### <a name="return-value"></a>返回值

第一个受保护的成员函数返回类型的参数字符对应的 char 类型的本机字符`CharType`或*默认*如果未不定义任何对应。

第二个受保护的成员函数返回一个指针，指向从 `CharType` 类型的字符转换的本机字符的目标范围。

### <a name="remarks"></a>备注

第二个受保护的成员模板函数存储在`dest`[ `I`] 值`do_narrow`( `first` [ `I`]， `default`)，为`I`间隔 [0， `last`  - `first`).

### <a name="example"></a>示例

请参阅 [narrow](#narrow) 的示例，它调用 `do_narrow`。

## <a name="do_scan_is"></a>ctype:: do_scan_is

一种虚拟函数，通过调用此函数可查找某个范围内与指定掩码匹配的第一个字符。

```cpp
virtual const CharType *do_scan_is(
    mask maskVal,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>参数

*maskVal*要通过字符匹配的掩码值。

*第一个*指向要扫描的范围内的第一个字符的指针。

*最后一个*指向要扫描的范围内最后一个字符之后紧跟的字符的指针。

### <a name="return-value"></a>返回值

指向某个范围内与指定掩码匹配的第一个字符的指针。 如果此类值不存在，该函数返回*最后一个*。

### <a name="remarks"></a>备注

受保护的成员函数返回最小的指针`ptr`范围内 [ `first`， `last`) 为其[do_is](#do_is)( `maskVal`， \* `ptr`) 为 true。

### <a name="example"></a>示例

请参阅 [scan_is](#scan_is) 的示例，它调用 `do_scan_is`。

## <a name="do_scan_not"></a>  ctype::do_scan_not

一种虚拟函数，通过调用此函数可查找某个范围内与指定掩码不匹配的第一个字符。

```cpp
virtual const CharType *do_scan_not(
    mask maskVal,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>参数

*maskVal*不要通过字符匹配的掩码值。

*第一个*指向要扫描的范围内的第一个字符的指针。

*最后一个*指向要扫描的范围内最后一个字符之后紧跟的字符的指针。

### <a name="return-value"></a>返回值

指向某个范围内与指定掩码不匹配的第一个字符的指针。 如果此类值不存在，该函数返回*最后一个*。

### <a name="remarks"></a>备注

受保护的成员函数返回最小的指针`ptr`范围内 [ `first`， `last`) 为其[do_is](#do_is)( `maskVal`， \* `ptr`) 为 false。

### <a name="example"></a>示例

请参阅 [scan_not](#scan_not) 的示例，它调用 `do_scan_not`。

## <a name="do_tolower"></a>ctype:: do_tolower

一种虚拟函数，通过调用此函数可将一个字符或一系列字符转换为小写。

```cpp
virtual CharType do_tolower(CharType ch) const;


virtual const CharType *do_tolower(
    CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>参数

*ch*要转换为小写的字符。

*第一个*指向字符的情况下是要转换的范围内的第一个字符的指针。

*最后一个*的要转换的字符范围中最后一个字符之后紧跟的字符的指针。

### <a name="return-value"></a>返回值

第一个受保护的成员函数返回参数的小写形式*ch*。 如果没有小写形式存在，它将返回*ch*。 第二个受保护成员函数返回*最后一个*。

### <a name="remarks"></a>备注

第二个受保护的成员模板函数将替换每个元素`first`[ `I`]，有关`I`间隔 [0， `last`  -  `first`)，与`do_tolower`( `first` [ `I`]).

### <a name="example"></a>示例

请参阅 [tolower](#tolower) 的示例，它调用 `do_tolower`。

## <a name="do_toupper"></a>ctype:: do_toupper

一种虚拟函数，通过调用此函数可将一个字符或一系列字符转换为大写。

```cpp
virtual CharType do_toupper(CharType ch) const;


virtual const CharType *do_toupper(
    CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>参数

*ch*要转换为大写的字符。

*第一个*指向字符的情况下是要转换的范围内的第一个字符的指针。

*最后一个*指向的要转换的字符范围中最后一个字符之后紧跟的字符的指针。

### <a name="return-value"></a>返回值

第一个受保护的成员函数返回参数的大写形式*ch*。 如果没有大写形式存在，它将返回*ch*。 第二个受保护成员函数返回*最后一个*。

### <a name="remarks"></a>备注

第二个受保护的成员模板函数将替换每个元素`first`[ `I`]，有关`I`间隔 [0， `last`  -  `first`)，与`do_toupper`( `first` [ `I`]).

### <a name="example"></a>示例

请参阅 [toupper](#toupper) 的示例，它调用 `do_toupper`。

## <a name="do_widen"></a>  ctype::do_widen

类型的字符转换为虚拟函数调用到**char**类型的相应字符本机字符集中`CharType`由区域设置。

```cpp
virtual CharType do_widen(char byte) const;


virtual const char *do_widen(
    const char* first,
    const char* last,
    CharType* dest) const;
```

### <a name="parameters"></a>参数

*字节*类型的字符**char**中设置要转换的本机字符。

*第一个*指向要转换的字符范围内的第一个字符的指针。

*最后一个*指向要转换的字符范围中最后一个字符之后紧跟的字符的指针。

*dest*类型的第一个字符的指针`CharType`目标范围存储经过转换的字符范围内。

### <a name="return-value"></a>返回值

第一个受保护的成员函数返回类型的字符`CharType`本机类型的参数字符对应**char**。

第二个受保护的成员函数返回一个指向目标范围的类型的字符`CharType`用来从本机字符类型的转换的区域设置**char**。

### <a name="remarks"></a>备注

第二个受保护的成员模板函数将 `I` 的值 `do_widen`( `first` [ `I`]) 存储在 `dest`[ `I`] 值 ，间隔为 [0, `last` - `first`)。

### <a name="example"></a>示例

请参阅 [widen](#widen) 的示例，它调用 `do_widen`。

## <a name="is"></a>  ctype::is

测试单个字符是否具有特定属性，或者对某个范围内的每个字符的属性进行分类并将属性存储在数组中。

```cpp
bool is(mask maskVal, CharType ch) const;


const CharType *is(
    const CharType* first,
    const CharType* last,
    mask* dest) const;
```

### <a name="parameters"></a>参数

*maskVal*为要测试字符的掩码值。

*ch*其属性是要测试的字符。

*第一个*指向其属性进行分类的范围中的第一个字符的指针。

*最后一个*指向其属性进行分类的范围中最后一个字符之后紧跟的字符的指针。

*dest*描述的每个字符属性特征的掩码值的存储位置的数组的开头的指针。

### <a name="return-value"></a>返回值

第一个成员函数返回 **，则返回 true**如果测试的字符具有掩码值; 所述的属性**false**如果它不具有该属性。

第二个成员函数返回一个指针，指向范围内要对其属性进行分类的最后一个字符。

### <a name="remarks"></a>备注

[ctype_base Class](../standard-library/ctype-base-class.md) 类提供了对字符属性进行分类的掩码值，从中派生 ctype。 第一个成员函数可以接受其第一个参数的表达式，该参数被称为位掩码，由逻辑按位运算符 (&#124; , & , ^ , ~) 组成的掩码值构成。

### <a name="example"></a>示例

```cpp
// ctype_is.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main() {
   locale loc1 ( "German_Germany" ), loc2 ( "English_Australia" );

   if (use_facet<ctype<char> > ( loc1 ).is( ctype_base::alpha, 'a' ))
      cout << "The character 'a' in locale loc1 is alphabetic."
           << endl;
   else
      cout << "The character 'a' in locale loc1 is not alphabetic."
           << endl;

   if (use_facet<ctype<char> > ( loc2 ).is( ctype_base::alpha, '!' ))
      cout << "The character '!' in locale loc2 is alphabetic."
           << endl;
   else
      cout << "The character '!' in locale loc2 is not alphabetic."
           << endl;

   char *string = "Hello, my name is John!";
   ctype<char>::mask maskarray[30];
   use_facet<ctype<char> > ( loc2 ).is(
      string, string + strlen(string), maskarray );
   for (unsigned int i = 0; i < strlen(string); i++) {
      cout << string[i] << ": "
           << (maskarray[i] & ctype_base::alpha  "alpha"
                                                : "not alpha")
           << endl;;
   };
}
```

## <a name="narrow"></a>  ctype::narrow

类型字符转换`CharType`使用的区域设置为相应类型的字符**char**本机字符集中。

```cpp
char narrow(CharType ch, char default = '\0') const;


const CharType* narrow(
    const CharType* first,
    const CharType* last,
    char default,
    char* dest) const;
```

### <a name="parameters"></a>参数

*ch*类型的字符`Chartype`由要转换的区域设置。

*默认值*到字符类型的成员函数分配的默认值`CharType`不具有的类型与字符**char**。

*第一个*指向要转换的字符范围内的第一个字符的指针。

*最后一个*指向要转换的字符范围中最后一个字符之后紧跟的字符的指针。

*dest*类型的第一个字符常量指针**char**目标范围存储经过转换的字符范围内。

### <a name="return-value"></a>返回值

第一个成员函数返回类型的本机字符**char**类型的参数字符对应`CharType default`如果未定义任何对应。

第二个成员函数返回一个指针，指向从 `CharType` 类型的字符转换的本机字符的目标范围。

### <a name="remarks"></a>备注

第一个成员函数返回[do_narrow](#do_narrow)(`ch`， `default`)。 第二个成员函数将返回[do_narrow](#do_narrow) (`first`， `last`， `default`， `dest`)。 只有基本的源字符才能保证在 `narrow` 之下存在唯一的反向映像 `CharType`。 对于这些基本的源字符，包含以下不变式：`narrow` ([widen](#widen) ( **c** ), 0 ) == **c**。

### <a name="example"></a>示例

```cpp
// ctype_narrow.cpp
// compile with: /EHsc /W3
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "english" );
   wchar_t *str1 = L"\x0392fhello everyone";
   char str2 [16];
   bool result1 = (use_facet<ctype<wchar_t> > ( loc1 ).narrow
      ( str1, str1 + wcslen(str1), 'X', &str2[0] ) != 0);  // C4996
   str2[wcslen(str1)] = '\0';
   wcout << str1 << endl;
   cout << &str2[0] << endl;
}
```

```Output
Xhello everyone
```

## <a name="scan_is"></a>  ctype::scan_is

查找某个范围内与指定掩码匹配的第一个字符。

```cpp
const CharType *scan_is(
    mask maskVal,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>参数

*maskVal*要通过字符匹配的掩码值。

*第一个*指向要扫描的范围内的第一个字符的指针。

*最后一个*指向要扫描的范围内最后一个字符之后紧跟的字符的指针。

### <a name="return-value"></a>返回值

指向某个范围内与指定掩码匹配的第一个字符的指针。 如果此类值不存在，该函数返回*最后一个*。

### <a name="remarks"></a>备注

此成员函数返回[do_scan_is](#do_scan_is)(`maskVal`， `first`， `last`)。

### <a name="example"></a>示例

```cpp
// ctype_scan_is.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "German_Germany" );

   char *string = "Hello, my name is John!";

   const char* i = use_facet<ctype<char> > ( loc1 ).scan_is
      ( ctype_base::punct, string, string + strlen(string) );
   cout << "The first punctuation is \"" << *i << "\" at position: "
      << i - string << endl;
}
```

```Output
The first punctuation is "," at position: 5
```

## <a name="scan_not"></a>  ctype::scan_not

查找某个范围内与指定掩码不匹配的第一个字符。

```cpp
const CharType *scan_not(
    mask maskVal,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>参数

*maskVal*不要通过字符匹配的掩码值。

*第一个*指向要扫描的范围内的第一个字符的指针。

*最后一个*指向要扫描的范围内最后一个字符之后紧跟的字符的指针。

### <a name="return-value"></a>返回值

指向某个范围内与指定掩码不匹配的第一个字符的指针。 如果此类值不存在，该函数返回*最后一个*。

### <a name="remarks"></a>备注

此成员函数返回[do_scan_not](#do_scan_not)(`maskVal`， `first`， `last`)。

### <a name="example"></a>示例

```cpp
// ctype_scan_not.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "German_Germany" );

   char *string = "Hello, my name is John!";

   const char* i = use_facet<ctype<char> > ( loc1 ).scan_not
      ( ctype_base::alpha, string, string + strlen(string) );
   cout << "First nonalpha character is \"" << *i << "\" at position: "
      << i - string << endl;
}
```

```Output
First nonalpha character is "," at position: 5
```

## <a name="tolower"></a>  ctype::tolower

将一个或一些列字符转换为小写。

```cpp
CharType tolower(CharType ch) const;


const CharType *tolower(CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>参数

*ch*要转换为小写的字符。

*第一个*指向字符的情况下是要转换的范围内的第一个字符的指针。

*最后一个*的要转换的字符范围中最后一个字符之后紧跟的字符的指针。

### <a name="return-value"></a>返回值

第一个成员函数返回参数的小写形式*ch*。 如果没有小写形式存在，它将返回*ch*。

第二个成员函数将返回*最后一个*。

### <a name="remarks"></a>备注

第一个成员函数返回[do_tolower](#do_tolower)(`ch`)。 第二个成员函数将返回[do_tolower](#do_tolower)(`first`， `last`)。

### <a name="example"></a>示例

```cpp
// ctype_tolower.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "German_Germany" );

   char string[] = "HELLO, MY NAME IS JOHN";

   use_facet<ctype<char> > ( loc1 ).tolower
      ( string, string + strlen(string) );
   cout << "The lowercase string is: " << string << endl;
}
```

```Output
The lowercase string is: hello, my name is john
```

## <a name="toupper"></a>  ctype::toupper

将一个或一些列字符转换为大写。

```cpp
CharType toupper(CharType ch) const;
const CharType *toupper(CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>参数

*ch*要转换为大写的字符。

*第一个*指向字符的情况下是要转换的范围内的第一个字符的指针。

*最后一个*的要转换的字符范围中最后一个字符之后紧跟的字符的指针。

### <a name="return-value"></a>返回值

第一个成员函数返回参数的大写形式*ch*。 如果没有大写形式存在，它将返回*ch*。

第二个成员函数将返回*最后一个*。

### <a name="remarks"></a>备注

第一个成员函数返回[do_toupper](#do_toupper)(`ch`)。 第二个成员函数返回 [do_toupper](#do_toupper)( `first`、`last`)。

### <a name="example"></a>示例

```cpp
// ctype_toupper.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "German_Germany" );

   char string[] = "Hello, my name is John";

   use_facet<ctype<char> > ( loc1 ).toupper
      ( string, string + strlen(string) );
   cout << "The uppercase string is: " << string << endl;
}
```

```Output
The uppercase string is: HELLO, MY NAME IS JOHN
```

## <a name="widen"></a>  ctype::widen

类型的字符转换为**char**类型的相应字符本机字符集中`CharType`由区域设置。

```cpp
CharType widen(char byte) const;
const char *widen(const char* first, const char* last, CharType* dest) const;
```

### <a name="parameters"></a>参数

*字节*本机字符集中 char 类型的字符设置要转换。

*第一个*指向要转换的字符范围内的第一个字符的指针。

*最后一个*指向要转换的字符范围中最后一个字符之后紧跟的字符的指针。

*dest*类型的第一个字符的指针`CharType`目标范围存储经过转换的字符范围内。

### <a name="return-value"></a>返回值

第一个成员函数返回类型的字符`CharType`本机类型的参数字符对应**char**。

第二个成员函数返回一个指向目标范围的类型的字符`CharType`用来从本机字符类型的转换的区域设置**char**。

### <a name="remarks"></a>备注

第一个成员函数返回[do_widen](#do_widen)(`byte`)。 第二个成员函数将返回[do_widen](#do_widen)(`first`， `last`， `dest`)。

### <a name="example"></a>示例

```cpp
// ctype_widen.cpp
// compile with: /EHsc /W3
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "English" );
   char *str1 = "Hello everyone!";
   wchar_t str2 [16];
   bool result1 = (use_facet<ctype<wchar_t> > ( loc1 ).widen
      ( str1, str1 + strlen(str1), &str2[0] ) != 0);  // C4996
   str2[strlen(str1)] = '\0';
   cout << str1 << endl;
   wcout << &str2[0] << endl;

   ctype<wchar_t>::char_type charT;
   charT = use_facet<ctype<char> > ( loc1 ).widen( 'a' );
}
```

```Output
Hello everyone!
Hello everyone!
```

## <a name="see-also"></a>请参阅

[\<locale>](../standard-library/locale.md)<br/>
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>

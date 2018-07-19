---
title: numpunct 类 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xlocnum/std::numpunct
- xlocnum/std::numpunct::char_type
- xlocnum/std::numpunct::string_type
- xlocnum/std::numpunct::decimal_point
- xlocnum/std::numpunct::do_decimal_point
- xlocnum/std::numpunct::do_falsename
- xlocnum/std::numpunct::do_grouping
- xlocnum/std::numpunct::do_thousands_sep
- xlocnum/std::numpunct::do_truename
- xlocnum/std::numpunct::falsename
- xlocnum/std::numpunct::grouping
- xlocnum/std::numpunct::thousands_sep
- xlocnum/std::numpunct::truename
dev_langs:
- C++
helpviewer_keywords:
- std::numpunct [C++]
- std::numpunct [C++], char_type
- std::numpunct [C++], string_type
- std::numpunct [C++], decimal_point
- std::numpunct [C++], do_decimal_point
- std::numpunct [C++], do_falsename
- std::numpunct [C++], do_grouping
- std::numpunct [C++], do_thousands_sep
- std::numpunct [C++], do_truename
- std::numpunct [C++], falsename
- std::numpunct [C++], grouping
- std::numpunct [C++], thousands_sep
- std::numpunct [C++], truename
ms.assetid: 73fb93cc-ac11-4c98-987c-bfa6267df596
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1ae2acae1664656883f4f2eba85c57c8e7725b26
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2018
ms.locfileid: "38965560"
---
# <a name="numpunct-class"></a>numpunct 类

一种模板类，用于描述一个对象来充当区域设置 facet，以便描述 `CharType` 类型的序列，后者用于表示与数字和布尔表达式的格式化及标点有关的信息。

## <a name="syntax"></a>语法

```cpp
template <class CharType>
class numpunct : public locale::facet;
```

### <a name="parameters"></a>参数

*CharType*在程序内使用的区域设置的字符进行编码的类型。

## <a name="remarks"></a>备注

对于任何区域设置 facet，静态对象 ID 的初始存储值为零。 首次尝试访问其存储值后，将在 **ID** 中存储唯一正值。

### <a name="constructors"></a>构造函数

|构造函数|描述|
|-|-|
|[numpunct](#numpunct)|`numpunct` 类型的对象的构造函数。|

### <a name="typedefs"></a>Typedef

|类型名称|描述|
|-|-|
|[char_type](#char_type)|一种类型，此类型用于描述区域设置使用的字符。|
|[string_type](#string_type)|一种类型，此类型描述包含 `CharType` 类型字符的字符串。|

### <a name="member-functions"></a>成员函数

|成员函数|描述|
|-|-|
|[decimal_point](#decimal_point)|返回要用作小数点的区域设置特定元素。|
|[do_decimal_point](#do_decimal_point)|一种受保护的虚拟成员函数，通过调用此函数可返回要用作小数点的区域设置特定元素。|
|[do_falsename](#do_falsename)|一种受保护虚拟成员函数调用以返回要用作值的文本表示形式的字符串**false**。|
|[do_grouping](#do_grouping)|一种受保护的虚拟成员函数，通过调用此函数可返回用于确定位数如何分组到任何小数点左边的区域设置特定规则。|
|[do_thousands_sep](#do_thousands_sep)|一种受保护的虚拟成员函数，通过调用此函数可返回要用作千位分隔符的区域设置特定元素。|
|[do_truename](#do_truename)|一种受保护的虚拟成员函数，通过调用此函数可返回要用作值 **true** 的文本表示形式的字符串。|
|[falsename](#falsename)|返回要用作值 **false** 的文本表示形式的字符串。|
|[grouping](#grouping)|返回用于确定位数如何分组到任何小数点左边的区域设置特定规则。|
|[thousands_sep](#thousands_sep)|返回要用作千位分隔符的区域设置特定元素。|
|[truename](#truename)|返回要用作值 **true** 的文本表示形式的字符串。|

## <a name="requirements"></a>要求

**标头：** \<locale>

**命名空间：** std

## <a name="char_type"></a>  numpunct::char_type

一种类型，此类型用于描述区域设置使用的字符。

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>备注

该类型是模板参数 **CharType** 的同义词。

## <a name="decimal_point"></a>  numpunct::decimal_point

返回要用作小数点的区域设置特定元素。

```cpp
CharType decimal_point() const;
```

### <a name="return-value"></a>返回值

要用作小数点的区域设置特定元素。

### <a name="remarks"></a>备注

此成员函数返回 [do_decimal_point](#do_decimal_point)。

### <a name="example"></a>示例

```cpp
// numpunct_decimal_point.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );

   const numpunct <char> &npunct =
   use_facet <numpunct <char> >( loc);
   cout << loc.name( ) << " decimal point "<<
   npunct.decimal_point( ) << endl;
   cout << loc.name( ) << " thousands separator "
   << npunct.thousands_sep( ) << endl;
};
```

```Output
German_Germany.1252 decimal point ,
German_Germany.1252 thousands separator .
```

## <a name="do_decimal_point"></a>  numpunct::do_decimal_point

一种受保护的虚拟成员函数，通过调用此函数可返回要用作小数点的区域设置特定元素。

```cpp
virtual CharType do_decimal_point() const;
```

### <a name="return-value"></a>返回值

要用作小数点的区域设置特定元素。

### <a name="example"></a>示例

请参阅 [decimal_point](#decimal_point) 的示例，其中虚拟成员函数由 `decimal_point` 调用。

## <a name="do_falsename"></a>  numpunct::do_falsename

受保护的虚拟成员函数将返回一个序列，以便用作值 **false** 的文本表示形式。

```cpp
virtual string_type do_falsename() const;
```

### <a name="return-value"></a>返回值

一个包含要用作值 **false** 的文本表示形式的序列的字符串。

### <a name="remarks"></a>备注

该成员函数将返回字符串“false”以表示所有区域设置中的值 **false**。

### <a name="example"></a>示例

请参阅 [falsename](#falsename) 的示例，其中虚拟成员函数由 `falsename` 调用。

## <a name="do_grouping"></a>  numpunct::do_grouping

一种受保护的虚拟成员函数，通过调用此函数可返回用于确定位数如何分组到任何小数点左边的区域设置特定规则。

```cpp
virtual string do_grouping() const;
```

### <a name="return-value"></a>返回值

用于确定如何对任何小数点左侧的数字进行分组的区域设置特定规则。

### <a name="remarks"></a>备注

此受保护的虚拟成员函数可返回一个区域设置特定规则，用于确定如何对任何小数点左侧的数字进行分组。 该编码与 **lconv::grouping** 的编码相同。

### <a name="example"></a>示例

有关示例，请参阅[分组](#grouping)，其中虚拟成员函数由调用`grouping`。

## <a name="do_thousands_sep"></a>  numpunct::do_thousands_sep

一种受保护的虚拟成员函数，通过调用此函数可返回要用作千位分隔符的区域设置特定元素。

```cpp
virtual CharType do_thousands_sep() const;
```

### <a name="return-value"></a>返回值

返回要用作千位分隔符的区域设置特定元素。

### <a name="remarks"></a>备注

受保护虚拟成员函数返回类型的区域设置特定元素`CharType`要用作任何小数点左侧的组分隔符。

### <a name="example"></a>示例

请参阅 [thousands_sep](#thousands_sep) 的示例，其中虚拟成员函数由 `thousands_sep` 调用。

## <a name="do_truename"></a>  numpunct::do_truename

一种受保护的虚拟成员函数，通过调用此函数可返回要用作值 **true** 的文本表示形式的字符串。

```cpp
virtual string_type do_truename() const;
```

### <a name="remarks"></a>备注

要用作值 **true** 的文本表示形式的字符串。

所有区域设置返回字符串“true”以表示值 **true**。

### <a name="example"></a>示例

请参阅 [truename](#truename) 的示例，其中虚拟成员函数由 `truename` 调用。

## <a name="falsename"></a>  numpunct::falsename

返回要用作值 **false** 的文本表示形式的字符串。

```cpp
string_type falsename() const;
```

### <a name="return-value"></a>返回值

一个包含一系列字符串`CharType`要用作值的文本表示形式**false**。

### <a name="remarks"></a>备注

该成员函数将返回字符串“false”以表示所有区域设置中的值 **false**。

此成员函数返回 [do_falsename](#do_falsename)。

### <a name="example"></a>示例

```cpp
// numpunct_falsename.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "English" );

   const numpunct <char> &npunct = use_facet <numpunct <char> >( loc );
   cout << loc.name( ) << " truename "<< npunct.truename( ) << endl;
   cout << loc.name( ) << " falsename "<< npunct.falsename( ) << endl;

   locale loc2( "French" );
   const numpunct <char> &npunct2 = use_facet <numpunct <char> >(loc2);
   cout << loc2.name( ) << " truename "<< npunct2.truename( ) << endl;
   cout << loc2.name( ) << " falsename "<< npunct2.falsename( ) << endl;
}
```

```Output
English_United States.1252 truename true
English_United States.1252 falsename false
French_France.1252 truename true
French_France.1252 falsename false
```

## <a name="grouping"></a>  numpunct::grouping

返回用于确定位数如何分组到任何小数点左边的区域设置特定规则。

```cpp
string grouping() const;
```

### <a name="return-value"></a>返回值

用于确定如何对任何小数点左侧的数字进行分组的区域设置特定规则。

### <a name="remarks"></a>备注

此成员函数返回 [do_grouping](#do_grouping)。

### <a name="example"></a>示例

```cpp
// numpunct_grouping.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany");

   const numpunct <char> &npunct =
       use_facet < numpunct <char> >( loc );
   for (unsigned int i = 0; i < npunct.grouping( ).length( ); i++)
   {
      cout << loc.name( ) << " international grouping:\n the "
           << i <<"th group to the left of the radix character "
           << "is of size " << (int)(npunct.grouping ( )[i])
           << endl;
   }
}
```

```Output
German_Germany.1252 international grouping:
 the 0th group to the left of the radix character is of size 3
```

## <a name="numpunct"></a>  numpunct::numpunct

`numpunct` 类型的对象的构造函数。

```cpp
explicit numpunct(size_t _Refs = 0);
```

### <a name="parameters"></a>参数

*_Refs*整数值，该值用于指定类型的对象的内存管理。

### <a name="remarks"></a>备注

可能的值 *_Refs*参数和其重要性：

- 0：对象的生存期由包含该对象的区域设置管理。

- 1：必须手动管理对象的生存期。

- \> 1： 未定义这些值。

由于该析构函数受到保护，可能没有直接的示例。

构造函数初始化其基对象与**区域设置::**[方面](../standard-library/locale-class.md#facet_class)(`_Refs`)。

## <a name="string_type"></a>  numpunct::string_type

一种类型，此类型描述包含 **CharType** 类型字符的字符串。

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>备注

此类型描述 [basic_string](../standard-library/basic-string-class.md) 模板类的专用化，该模板类的对象可存储标点序列的副本。

## <a name="thousands_sep"></a>  numpunct::thousands_sep

返回要用作千位分隔符的区域设置特定元素。

```cpp
CharType thousands_sep() const;
```

### <a name="return-value"></a>返回值

要用作千位分隔符的区域设置特定元素。

### <a name="remarks"></a>备注

此成员函数返回 [do_thousands_sep](#do_thousands_sep)。

### <a name="example"></a>示例

```cpp
// numpunct_thou_sep.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );

   const numpunct <char> &npunct =
   use_facet < numpunct < char > >( loc );
   cout << loc.name( ) << " decimal point "<<
   npunct.decimal_point( ) << endl;
   cout << loc.name( ) << " thousands separator "
   << npunct.thousands_sep( ) << endl;
};
```

```Output
German_Germany.1252 decimal point ,
German_Germany.1252 thousands separator .
```

## <a name="truename"></a>  numpunct::truename

返回要用作值 **true** 的文本表示形式的字符串。

```cpp
string_type falsename() const;
```

### <a name="return-value"></a>返回值

要用作值 **true** 的文本表示形式的字符串。

### <a name="remarks"></a>备注

此成员函数返回 [do_truename](#do_truename)。

所有区域设置返回字符串“true”以表示值 **true**。

### <a name="example"></a>示例

```cpp
// numpunct_truename.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "English" );

   const numpunct < char> &npunct = use_facet <numpunct <char> >( loc );
   cout << loc.name( ) << " truename "<< npunct.truename( ) << endl;
   cout << loc.name( ) << " falsename "<< npunct.falsename( ) << endl;

   locale loc2("French");
   const numpunct <char> &npunct2 = use_facet <numpunct <char> >( loc2 );
   cout << loc2.name( ) << " truename "<< npunct2.truename( ) << endl;
   cout << loc2.name( ) << " falsename "<< npunct2.falsename( ) << endl;
}
```

```Output
English_United States.1252 truename true
English_United States.1252 falsename false
French_France.1252 truename true
French_France.1252 falsename false
```

## <a name="see-also"></a>请参阅

[\<locale>](../standard-library/locale.md)<br/>
[facet 类](../standard-library/locale-class.md#facet_class)<br/>
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>

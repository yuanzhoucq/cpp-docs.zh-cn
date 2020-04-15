---
title: collate 类
ms.date: 11/04/2016
f1_keywords:
- locale/std::collate
- locale/std::collate::char_type
- locale/std::collate::string_type
- locale/std::collate::compare
- locale/std::collate::do_compare
- locale/std::collate::do_hash
- locale/std::collate::do_transform
- locale/std::collate::hash
- locale/std::collate::transform
helpviewer_keywords:
- std::collate [C++]
- std::collate [C++], char_type
- std::collate [C++], string_type
- std::collate [C++], compare
- std::collate [C++], do_compare
- std::collate [C++], do_hash
- std::collate [C++], do_transform
- std::collate [C++], hash
- std::collate [C++], transform
ms.assetid: 92168798-9628-4a2e-be6e-fa62dcd4d6a6
ms.openlocfilehash: f05c2e9482f8a0bada3868fdc946d4d26a0e0e1d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371924"
---
# <a name="collate-class"></a>collate 类

一个类模板，用于描述可用作区域设置面的对象，用于控制字符串中字符的顺序和分组、字符串之间的比较和字符串的哈希。

## <a name="syntax"></a>语法

```cpp
template <class CharType>
class collate : public locale::facet;
```

### <a name="parameters"></a>参数

*字符类型*\
在程序中用于对字符进行编码的类型。

## <a name="remarks"></a>备注

对于任何区域设置 facet，静态对象 ID 的初始存储值为零。 首次尝试访问其存储值后，将在 `id` 中存储唯一正值。 在某些语言中，多个字符作为单个字符分组和处理，在其他语言中，单个字符被作为两个字符进行处理。 通过排序规则类提供的排序规则服务，可以在这些情况下进行排序。

### <a name="constructors"></a>构造函数

|构造函数|说明|
|-|-|
|[整理](#collate)|用作区域设置 facet 以处理字符串排序转换的 `collate` 类的对象的构造函数。|

### <a name="typedefs"></a>Typedef

|类型名称|说明|
|-|-|
|[char_type](#char_type)|一种类型，此类型描述 `CharType` 类型字符。|
|[string_type](#string_type)|一种类型，此类型描述包含 `basic_string` 类型字符的 `CharType` 类型字符串。|

### <a name="member-functions"></a>成员职能

|成员函数|说明|
|-|-|
|[比较](#compare)|根据两个字符序列的特定于 facet 的规则，比较这两个字符序列是否相等。|
|[do_compare](#do_compare)|一种虚拟函数，通过调用此函数可根据两个字符序列的特定于 facet 的规则来比较这两个序列是否相等。|
|[do_hash](#do_hash)|一种虚拟函数，通过调用此函数可根据序列的特定于 facet 的规则来确定它们的哈希值。|
|[do_transform](#do_transform)|一种虚拟函数，通过调用此函数可将字符序列从区域设置转换为字符串，可使用此字符串与以类似方式从同一区域设置转换的其他字符序列按字典顺序进行比较。|
|[散 列](#hash)|根据序列的特定于 facet 的规则来确定它们的哈希值。|
|[transform](#transform)|将字符序列从区域设置转换为字符串，可使用此字符串与以类似方式从同一区域设置转换的其他字符序列按字典顺序进行比较。|

## <a name="requirements"></a>要求

**标头：** \<locale>

**命名空间:** std

## <a name="collatechar_type"></a><a name="char_type"></a>整理：：char_type

一种类型，此类型描述 `CharType` 类型字符。

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>备注

类型是模板参数 `CharType` 的同义词。

## <a name="collatecollate"></a><a name="collate"></a>整理：：整理

用作区域设置 facet 以处理字符串排序转换的 collate 类的对象的构造函数。

```cpp
public:
    explicit collate(
    size_t _Refs = 0);

protected:
    collate(
const char* _Locname,
    size_t _Refs = 0);
```

### <a name="parameters"></a>参数

*_Refs*\
用于指定对象的内存管理类型的整数值。

*_Locname*\
区域设置的名称。

### <a name="remarks"></a>备注

*_Refs*参数的可能值及其显著性为：

- 0：对象的生存期由包含该对象的区域设置管理。

- 1：必须手动管理对象的生存期。

- \>1： 未定义这些值。

构造函数用区域设置初始化其基本对象 **：：**[分面](../standard-library/locale-class.md#facet_class)（`_Refs`。

## <a name="collatecompare"></a><a name="compare"></a>整理：：比较

根据两个字符序列的特定于 facet 的规则，比较这两个字符序列是否相等。

```cpp
int compare(const CharType* first1,
    const CharType* last1,
    const CharType* first2,
    const CharType* last2) const;
```

### <a name="parameters"></a>参数

*第一1*\
指向第一个序列中要比较的第一个元素的指针。

*最后1*\
指向第一个序列中要比较的最后一个元素的指针。

*第一2*\
指向第二个序列中要比较的第一个元素的指针。

*最后2*\
指向第二个序列中要比较的最后一个元素的指针。

### <a name="return-value"></a>返回值

此成员函数返回：

- 如果第一个序列小于第二个序列，则为 -1。

- 如果第一个序列大于第二个序列，则为 +1。

- 如果两个序列相等，则为 0。

### <a name="remarks"></a>备注

如果序列中的最早不相等对存在较小元素，或如果不存在不相等对，但第一个序列长度较短，则第一个序列相对较小。

成员函数返回[do_compare](#do_compare) `first1`（、 `last1` `first2`、 `last2`。 。

### <a name="example"></a>示例

```cpp
// collate_compare.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <tchar.h>
using namespace std;

int main() {
   locale loc ( "German_germany" );
   _TCHAR * s1 = _T("Das ist wei\x00dfzz."); // \x00df is the German sharp-s, it comes before z in the German alphabet
   _TCHAR * s2 = _T("Das ist weizzz.");
   int result1 = use_facet<collate<_TCHAR> > ( loc ).
      compare ( s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << result1 << endl;

   locale loc2 ( "C" );
   int result2 = use_facet<collate<_TCHAR> > ( loc2 ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << result2 << endl;
}
```

## <a name="collatedo_compare"></a><a name="do_compare"></a>整理：:do_比较

一种虚拟函数，通过调用此函数可根据两个字符序列的特定于 facet 的规则来比较这两个序列是否相等。

```cpp
virtual int do_compare(const CharType* first1,
    const CharType* last1,
    const CharType* first2,
    const CharType* last2) const;
```

### <a name="parameters"></a>参数

*第一1*\
指向第一个序列中要比较的第一个元素的指针。

*最后1*\
指向第一个序列中要比较的最后一个元素的指针。

*第一2*\
指向第二个序列中要比较的第一个元素的指针。

*最后2*\
指向第二个序列中要比较的最后一个元素的指针。

### <a name="return-value"></a>返回值

此成员函数返回：

- 如果第一个序列小于第二个序列，则为 -1。

- 如果第一个序列大于第二个序列，则为 +1。

- 如果两个序列相等，则为 0。

### <a name="remarks"></a>备注

受保护的虚拟成员函数将 * 前 11，Last1）] 处的序列与 *# first2， last2*的序列进行比较。 它通过在类型`CharType`对应元素`operator<`的对之间应用来比较值。 如果序列中的最早不相等对存在较小元素，或如果不存在不相等对，但第一个序列长度较短，则第一个序列相对较小。

### <a name="example"></a>示例

请参阅 [collate:: compare](#compare) 的示例，它调用 `do_compare`。

## <a name="collatedo_hash"></a><a name="do_hash"></a>整理：:d

一种虚拟函数，通过调用此函数可根据序列的特定于 facet 的规则来确定它们的哈希值。

```cpp
virtual long do_hash(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>参数

*第一*\
一个指向序列中具有待定值的第一个字符的指针。

*最后*\
一个指向序列中具有待定值的最后一个字符的指针。

### <a name="return-value"></a>返回值

针对序列的 **long** 类型的哈希值。

### <a name="remarks"></a>备注

哈希值可用于在列表数组中伪随机分布序列等。

### <a name="example"></a>示例

请参阅 [hash](#hash) 的示例，它调用`do_hash`。

## <a name="collatedo_transform"></a><a name="do_transform"></a>整理：:do_变换

一种虚拟函数，通过调用此函数可将字符序列从区域设置转换为字符串，可使用此字符串与以类似方式从同一区域设置转换的其他字符序列按字典顺序进行比较。

```cpp
virtual string_type do_transform(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>参数

*第一*\
指向序列中要转换的第一个字符的指针。

*最后*\
指向序列中要转换的最后一个字符的指针。

### <a name="return-value"></a>返回值

一个字符串，为转换后的字符序列。

### <a name="remarks"></a>备注

受保护的虚拟成员函数返回类[string_type的对象，](#string_type)其受控序列是序列的副本 * `first` `last`。 。 如果一个类派生自 collate\< **CharType**> overrides [do_compare](#do_compare)，还应该重写 `do_transform` 以进行匹配。 传递给 `collate::compare` 时，两个已转换的字符串应产生相同的结果，你会从传递未经转换的字符串中获得此结果以在派生类中进行比较。

### <a name="example"></a>示例

请参阅 [transform](#transform) 的示例，它调用 `do_transform`。

## <a name="collatehash"></a><a name="hash"></a>整理：：哈希

根据序列的特定于 facet 的规则来确定它们的哈希值。

```cpp
long hash(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>参数

*第一*\
一个指向序列中具有待定值的第一个字符的指针。

*最后*\
一个指向序列中具有待定值的最后一个字符的指针。

### <a name="return-value"></a>返回值

针对序列的 **long** 类型的哈希值。

### <a name="remarks"></a>备注

成员函数返回[do_hash](#do_hash) `first`（。 `last`

哈希值可用于在列表数组中伪随机分布序列等。

### <a name="example"></a>示例

```cpp
// collate_hash.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <tchar.h>
using namespace std;

int main( )
{
   locale loc ( "German_germany" );
   _TCHAR * s1 = _T("\x00dfzz abc."); // \x00df is the German sharp-s (looks like beta), it comes before z in the alphabet
   _TCHAR * s2 = _T("zzz abc."); // \x00df is the German sharp-s (looks like beta), it comes before z in the alphabet

   long r1 = use_facet< collate<_TCHAR> > ( loc ).
      hash (s1, &s1[_tcslen( s1 )-1 ]);
   long r2 =  use_facet< collate<_TCHAR> > ( loc ).
      hash (s2, &s2[_tcslen( s2 )-1 ] );
   cout << r1 << " " << r2 << endl;
}
```

```Output
541187293 551279837
```

## <a name="collatestring_type"></a><a name="string_type"></a>整理：：string_type

一种类型，此类型描述包含 `basic_string` 类型字符的 `CharType` 类型字符串。

```cpp
typedef basic_string<CharType> string_type;
```

### <a name="remarks"></a>备注

类型描述类模板的专门化[basic_string](../standard-library/basic-string-class.md)其对象可以存储源序列的副本。

### <a name="example"></a>示例

有关如何声明和使用 `string_type` 的示例，请参阅 [transform](#transform)。

## <a name="collatetransform"></a><a name="transform"></a>整理：：转换

将字符序列从区域设置转换为字符串，可使用此字符串与以类似方式从同一区域设置转换的其他字符序列按字典顺序进行比较。

```cpp
string_type transform(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>参数

*第一*\
指向序列中要转换的第一个字符的指针。

*最后*\
指向序列中要转换的最后一个字符的指针。

### <a name="return-value"></a>返回值

一个字符串，包含已转换的字符序列。

### <a name="remarks"></a>备注

成员函数返回[do_transform](#do_transform)`first`（。 `last`

### <a name="example"></a>示例

```cpp
// collate_transform.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <tchar.h>
using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   _TCHAR* s1 = _T("\x00dfzz abc.");
   // \x00df is the German sharp-s (looks like beta),
   // it comes before z in the alphabet
   _TCHAR* s2 = _T("zzz abc.");

   collate<_TCHAR>::string_type r1;   // OK for typedef
   r1 = use_facet< collate<_TCHAR> > ( loc ).
      transform (s1, &s1[_tcslen( s1 )-1 ]);

   cout << r1 << endl;

   basic_string<_TCHAR> r2 = use_facet< collate<_TCHAR> > ( loc ).
      transform (s2, &s2[_tcslen( s2 )-1 ]);

   cout << r2 << endl;

   int result1 = use_facet<collate<_TCHAR> > ( loc ).compare
      (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );

   cout << _tcscmp(r1.c_str( ),r2.c_str( )) << result1
      << _tcscmp(s1,s2) <<endl;
}
```

```Output

-1-11
```

## <a name="see-also"></a>另请参阅

[\<区域设置>](../standard-library/locale.md)\
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)

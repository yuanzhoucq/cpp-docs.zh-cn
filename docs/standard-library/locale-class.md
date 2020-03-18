---
title: locale 类
ms.date: 03/19/2019
f1_keywords:
- xlocale/std::locale
- xlocale/std::locale::category
- xlocale/std::locale::combine
- xlocale/std::locale::name
- xlocale/std::locale::classic
- xlocale/std::locale::global
- xlocale/std::locale::operator( )
- xlocale/std::locale::facet
- xlocale/std::locale::id
helpviewer_keywords:
- std::locale [C++]
- std::locale [C++], category
- std::locale [C++], combine
- std::locale [C++], name
- std::locale [C++], classic
- std::locale [C++], global
- std::locale [C++], facet
- std::locale [C++], id
ms.assetid: 7dd6d271-472d-4750-8fb5-ea8f55fbef62
ms.openlocfilehash: 551bca93a30bee52dc4c838864df28cb747d91df
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425549"
---
# <a name="locale-class"></a>locale 类

一种描述区域设置对象的类，此对象用于将特定于文化的信息封装为一组 facet 以共同定义特定本地化环境。

## <a name="syntax"></a>语法

```cpp
class locale;
```

## <a name="remarks"></a>备注

facet 是指向派生自 [facet](#facet_class) 类的类对象的指针，该类具有以下格式的公共对象：

```cpp
static locale::id id;
```

可以定义这些 facet 的开放式集。 还可以构建指定任意个 facet 的区域设置对象。

这些 facet 的预定义组表示传统上在标准 C 库中由函数 `setlocale` 管理的[区域设置类别](#category)。

类别 `collate` （LC_COLLATE）包括以下方面：

```cpp
collate<char>
collate<wchar_t>
```

类别 `ctype` （LC_CTYPE）包括以下方面：

```cpp
ctype<char>
ctype<wchar_t>
codecvt<char, char, mbstate_t>
codecvt<wchar_t, char, mbstate_t>
codecvt<char16_t, char, mbstate_t>
codecvt<char32_t, char, mbstate_t>
```

类别 `monetary` （LC_MONETARY）包括以下方面：

```cpp
moneypunct<char, false>
moneypunct<wchar_t, false>
moneypunct<char, true>
moneypunct<wchar_t, true>
money_get<char, istreambuf_iterator<char>>
money_get<wchar_t, istreambuf_iterator<wchar_t>>
money_put<char, ostreambuf_iterator<char>>
money_put<wchar_t, ostreambuf_iterator<wchar_t>>
```

类别 `numeric` （LC_NUMERIC）包括以下方面：

```cpp
num_get<char, istreambuf_iterator<char>>
num_get<wchar_t, istreambuf_iterator<wchar_t>>
num_put<char, ostreambuf_iterator<char>>
num_put<wchar_t, ostreambuf_iterator<wchar_t>>
numpunct<char>
numpunct<wchar_t>
```

类别 `time` （LC_TIME）包括以下方面：

```cpp
time_get<char, istreambuf_iterator<char>>
time_get<wchar_t, istreambuf_iterator<wchar_t>>
time_put<char, ostreambuf_iterator<char>>
time_put<wchar_t, ostreambuf_iterator<wchar_t>>
```

类别 `messages` （LC_MESSAGES）包括以下方面：

```cpp
messages<char>
messages<wchar_t>
```

（最后一个类别是 POSIX 所必需的，但不是 C 标准。）

其中一些预定义的方面由 `iostream` 类使用，用来控制数值与文本序列之间的转换。

locale 类的对象还将区域设置名称存储为[字符串](../standard-library/string-typedefs.md#string)类的对象。 若使用无效区域设置名称构造区域设置 facet 或区域设置对象，将引发 [runtime_error](../standard-library/runtime-error-class.md) 类的对象。 如果区域设置对象无法确定 C 样式区域设置与由对象表示的区域设置完全对应，则存储的区域设置名称将 `"*"`。 否则，可以在标准 C 库中建立匹配的区域设置，为某些区域设置对象 `locale_object`，`setlocale(LC_ALL , locale_object.`[名称](#name)`().c_str())`调用。

在此实现中，还可以调用静态成员函数：

```cpp
static locale empty();
```

构造不包含 facet 的区域设置对象。 它也是透明区域设置。 如果模板函数[has_facet](../standard-library/locale-functions.md#has_facet)并且[use_facet](../standard-library/locale-functions.md#use_facet)在透明区域设置中找不到请求的 facet，则它们首先参考全局区域设置，如果是透明的，则为经典区域设置。 因此，你可以编写：

```cpp
cout.imbue(locale::empty());
```

[`cout`](../standard-library/iostream.md#cout)的后续插入会按全局区域设置的当前状态进行经过调谐。 你还可以编写：

```cpp
locale loc(locale::empty(),
    locale::classic(),
    locale::numeric);

cout.imbue(loc);
```

对 `cout` 的后续插入的数值格式设置规则与 C 区域设置相同，即使全局区域设置提供有关插入日期和货币金额的更改规则也是如此。

### <a name="constructors"></a>构造函数

|构造函数|描述|
|-|-|
|[locale](#locale)|创建区域设置、区域设置副本，或其中的 facet 或类别替换为其他区域设置中的 facet 类别的区域设置副本。|

### <a name="typedefs"></a>Typedef

|类型名称|描述|
|-|-|
|[category](#category)|一种整数类型，此类型提供位掩码值以表示标准 facet 系列。|

### <a name="member-functions"></a>成员函数

|成员函数|描述|
|-|-|
|[combine](#combine)|将指定区域设置中的 facet 插入到目标区域设置。|
|[name](#name)|返回存储的区域设置名称。|

### <a name="static-functions"></a>静态函数

|||
|-|-|
|[classic](#classic)|此静态成员函数返回表示经典 C 区域设置的区域设置对象。|
|[global](#global)|重置程序的默认区域设置。|

### <a name="operators"></a>运算符

|Operator|描述|
|-|-|
|[operator=](#op_eq)|指定区域设置。|
|[operator!=](#op_neq)|测试两个区域设置是否不相等。|
|[operator( )](#op_call)|比较两个 `basic_string` 对象。|
|[operator==](#op_eq_eq)|测试两个区域设置是否相等。|

### <a name="classes"></a>类

|类|描述|
|-|-|
|[facet](#facet_class)|一种类，此类用作所有区域设置 facet 的基类。|
|[`id`](#id_class)|成员类提供用作索引以查找区域设置中的 facet 的唯一 facet 标识。|

## <a name="requirements"></a>要求

**标头：** \<locale>

**命名空间：** std

## <a name="category"></a>locale::category

一种整数类型，此类型提供位掩码值以表示标准 facet 系列。

```cpp
typedef int category;
static const int collate = LC_COLLATE;
static const int ctype = LC_CTYPE;
static const int monetary = LC_MONETARY;
static const int numeric = LC_NUMERIC;
static const int time = LC_TIME;
static const int messages = LC_MESSAGES;
static const int all = LC_ALL;
static const int none = 0;
```

### <a name="remarks"></a>备注

类型是**int**类型的同义词，该类型可以表示类区域设置本地位掩码类型的一组非重复元素，也可以用来表示任何相应的 C 区域设置类别。 这些元素为：

- `collate`，对应于 C 类别 LC_COLLATE

- `ctype`，对应于 C 类别 LC_CTYPE

- `monetary`，对应于 C 类别 LC_MONETARY

- `numeric`，对应于 C 类别 LC_NUMERIC

- `time`，对应于 C 类别 LC_TIME

- `messages`，对应于 POSIX 类别 LC_MESSAGES

另外两个有用的值是：

- `none`，对应于 C 类中的任何一个

- `all`，对应于所有类别的 C 联合 LC_ALL

可以通过将 `OR` 与这些常量结合使用来表示任意类别组，如 `monetary` &#124; `time`中所示。

## <a name="classic"></a>locale::classic

此静态成员函数返回表示经典 C 区域设置的区域设置对象。

```cpp
static const locale& classic();
```

### <a name="return-value"></a>返回值

C 区域设置的引用。

### <a name="remarks"></a>备注

经典 C 区域设置为美国。标准 C 库中的英文 ASCII 区域设置。 这是隐式的程序中所使用的区域设置。

### <a name="example"></a>示例

```cpp
// locale_classic.cpp
// compile with: /EHsc
#include <iostream>
#include <string>
#include <locale>

using namespace std;

int main( )
{
   locale loc1( "german" );
   locale loc2 = locale::global( loc1 );
   cout << "The name of the previous locale is: " << loc2.name( )
        << "." << endl;
   cout << "The name of the current locale is: " << loc1.name( )
        << "." << endl;

   if (loc2 == locale::classic( ) )
      cout << "The previous locale was classic." << endl;
   else
      cout << "The previous locale was not classic." << endl;

   if (loc1 == locale::classic( ) )
      cout << "The current locale is classic." << endl;
   else
      cout << "The current locale is not classic." << endl;
}
```

```Output
The name of the previous locale is: C.
The name of the current locale is: German_Germany.1252.
The previous locale was classic.
The current locale is not classic.
```

## <a name="combine"></a>locale::combine

将指定区域设置中的 facet 插入到目标区域设置。

```cpp
template <class Facet>
locale combine(const locale& source_locale) const;
```

### <a name="parameters"></a>参数

*source_locale*\
包含要插入到目标区域设置的 facet 的区域设置。

### <a name="return-value"></a>返回值

该成员函数将返回区域设置对象，该对象将替换 **\*这**一 `Facet` *source_locale*中列出的方面。

### <a name="example"></a>示例

```cpp
// locale_combine.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <tchar.h>
using namespace std;

int main() {
   locale loc ( "German_germany" );
   _TCHAR * s1 = _T("Das ist wei\x00dfzz."); // \x00df is the German sharp-s; it comes before z in the German alphabet
   _TCHAR * s2 = _T("Das ist weizzz.");
   int result1 = use_facet<collate<_TCHAR> > ( loc ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << isalpha (_T ( '\x00df' ), loc ) << result1 << endl;

   locale loc2 ( "C" );
   int result2 = use_facet<collate<_TCHAR> > ( loc2 ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << isalpha (_T ( '\x00df' ), loc2 )  << result2 << endl;

   locale loc3 = loc2.combine<collate<_TCHAR> > (loc);
   int result3 = use_facet<collate<_TCHAR> > ( loc3 ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << isalpha (_T ( '\x00df' ), loc3 ) << result3 << endl;
}
```

## <a name="facet_class"></a>facet 类

一种类，此类用作所有区域设置 facet 的基类。

```cpp
class facet {
protected:
    explicit facet(size_t references = 0);
    virtual ~facet();
private:
    facet(const facet&) // not defined
    void operator=(const facet&) // not defined
};
```

### <a name="remarks"></a>备注

不能复制或分配类 `facet`的对象。 可以构造和销毁派生自类 `locale::facet` 的对象，但不能构造和销毁适当的基类对象。 通常，构造 `locale`时，构造从 `facet` 派生的对象 `_Myfac`，如 `locale loc(locale::classic(), new _Myfac);`

在这种情况下，基类 `facet` 的构造函数应具有零*引用*参数。 当不再需要该对象时，将会将其删除，因此，只需在这种极少的情况下提供非零*引用*参数，您就可以在该对象的生存期内承担责任。

## <a name="global"></a>locale::global

重置程序的默认区域设置。 此调用会影响 C 和C++的全局区域设置。

```cpp
static locale global(const locale& new_default_locale);
```

### <a name="parameters"></a>参数

*new_default_locale*\
要由该程序用作默认区域设置的区域设置。

### <a name="return-value"></a>返回值

重置默认区域设置之前的上一个区域设置。

### <a name="remarks"></a>备注

在程序启动时，全局区域设置与经典区域设置相同。 `global()` 函数调用 `setlocale( LC_ALL, loc.name. c_str())` 以在标准 C 库中建立匹配的区域设置。

### <a name="example"></a>示例

```cpp
// locale_global.cpp
// compile by using: /EHsc
#include <locale>
#include <iostream>
#include <tchar.h>
using namespace std;

int main( )
{
   locale loc ( "German_germany" );
   locale loc1;
   cout << "The initial locale is: " << loc1.name( ) << endl;
   locale loc2 = locale::global ( loc );
   locale loc3;
   cout << "The current locale is: " << loc3.name( ) << endl;
   cout << "The previous locale was: " << loc2.name( ) << endl;
}
```

```Output
The initial locale is: C
The current locale is: German_Germany.1252
The previous locale was: C
```

## <a name="id_class"></a>  id 类

成员类提供用作索引以查找区域设置中的 facet 的唯一 facet 标识。

```cpp
class id
{
   protected:    id();
   private:      id(const id&)
   void operator=(const id&)  // not defined
};
```

### <a name="remarks"></a>备注

该成员类描述每个唯一区域设置 facet 所需的静态成员对象。 不能复制或分配类 `id`的对象。

## <a name="locale"></a>locale::locale

创建区域设置、区域设置副本，或其中的 facet 或类别替换为其他区域设置中的 facet 类别的区域设置副本。 还包含析构函数。

```cpp
locale();

explicit locale(const char* locale_name, category new_category = all);
explicit locale(const string& locale_name);
locale(const locale& from_locale);
locale(const locale& from_locale, const locale& Other, category new_category);
locale(const locale& from_locale, const char* locale_name, category new_category);

template <class Facet>
locale(const locale& from_locale, const Facet* new_facet);

~locale();
```

### <a name="parameters"></a>参数

*locale_name*\
区域设置的名称。

*from_locale*\
要进行复制以便用于构造新区域设置的区域设置。

*其他*\
要从中选择一种类别的区域设置。

*new_category*\
要替换为构造的区域设置的类别。

*new_facet*\
要替换为构造的区域设置的 facet。

### <a name="remarks"></a>备注

第一个构造函数将初始化该对象，以便匹配全局构造函数。 第二个和第三个构造函数初始化所有区域设置类别，使其行为与区域设置名称*locale_name*一致。 剩余的构造函数复制*from_locale*，并注明例外：

`locale(const locale& from_locale, const locale& Other, category new_category);`

替换为 C & *new_category*为非零的类别 c 的*其他*方面。

`locale(const locale& from_locale, const char* locale_name, category new_category);`

`locale(const locale& from_locale, const string& locale_name, category new_category);`

替换为 `replace_category & new_category` 为非零的类别*replace_category*对应的那些方面 `locale(locale_name, all)`。

`template<class Facet> locale(const locale& from_locale, Facet* new_facet);`

如果*new_facet*不是 null 指针，则将替换（或添加到） *from_locale* facet *new_facet*。

如果区域设置名称*locale_name*为 null 指针或无效，则该函数将引发[runtime_error](../standard-library/runtime-error-class.md)。

### <a name="example"></a>示例

```cpp
// locale_locale.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <tchar.h>
using namespace std;

int main( ) {

   // Second constructor
   locale loc ( "German_germany" );
   _TCHAR * s1 = _T("Das ist wei\x00dfzz."); // \x00df is the German sharp-s, it comes before z in the German alphabet
   _TCHAR * s2 = _T("Das ist weizzz.");
   int result1 = use_facet<collate<_TCHAR> > ( loc ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << isalpha (_T ( '\x00df' ), loc ) << result1 << endl;

   // The first (default) constructor
   locale loc2;
   int result2 = use_facet<collate<_TCHAR> > ( loc2 ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << isalpha (_T ( '\x00df' ), loc2 )  << result2 << endl;

   // Third constructor
   locale loc3 (loc2,loc, _M_COLLATE );
   int result3 = use_facet<collate<_TCHAR> > ( loc3 ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << isalpha (_T ( '\x00df' ), loc3 ) << result3 << endl;

   // Fourth constructor
   locale loc4 (loc2, "German_Germany", _M_COLLATE );
   int result4 = use_facet<collate<_TCHAR> > ( loc4 ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << isalpha (_T ( '\x00df' ), loc4 ) << result4 << endl;
}
```

## <a name="name"></a>locale::name

返回存储的区域设置名称。

```cpp
string name() const;
```

### <a name="return-value"></a>返回值

一个字符串，它提供区域设置的名称。

### <a name="example"></a>示例

```cpp
// locale_name.cpp
// compile with: /EHsc
#include <iostream>
#include <string>
#include <locale>

using namespace std;

int main( )
{
   locale loc1( "german" );
   locale loc2 = locale::global( loc1 );
   cout << "The name of the previous locale is: "
        << loc2.name( ) << "." << endl;
   cout << "The name of the current locale is: "
        << loc1.name( ) << "." << endl;
}
```

```Output
The name of the previous locale is: C.
The name of the current locale is: German_Germany.1252.
```

## <a name="op_eq"></a>locale：： operator =

指定区域设置。

```cpp
const locale& operator=(const locale& other) noexcept;
```

## <a name="op_neq"></a>locale::operator!=

测试两个区域设置是否不相等。

```cpp
bool operator!=(const locale& right) const;
```

### <a name="parameters"></a>参数

*right*\
要测试不相等的区域设置之一。

### <a name="return-value"></a>返回值

一个布尔值，如果区域设置不是相同区域设置的副本，则为**true** 。 如果区域设置是相同区域设置的副本，则**为 false** 。

### <a name="remarks"></a>备注

如果两个区域设置是相同的区域设置（如果是另一个区域的副本）或它们的名称相同，则这两个区域设置是相等的。

### <a name="example"></a>示例

```cpp
// locale_op_ne.cpp
// compile with: /EHsc
#include <iostream>
#include <string>
#include <locale>

using namespace std;

int main( )
{
   locale loc1( "German_Germany" );
   locale loc2( "German_Germany" );
   locale loc3( "English" );

   if ( loc1 != loc2 )
      cout << "locales loc1 (" << loc1.name( )
      << ") and\n loc2 (" << loc2.name( ) << ") are not equal." << endl;
   else
      cout << "locales loc1 (" << loc1.name( )
      << ") and\n loc2 (" << loc2.name( ) << ") are equal." << endl;

   if ( loc1 != loc3 )
      cout << "locales loc1 (" << loc1.name( )
      << ") and\n loc3 (" << loc3.name( ) << ") are not equal." << endl;
   else
      cout << "locales loc1 (" << loc1.name( )
      << ") and\n loc3 (" << loc3.name( ) << ") are equal." << endl;
}
```

```Output
locales loc1 (German_Germany.1252) and
loc2 (German_Germany.1252) are equal.
locales loc1 (German_Germany.1252) and
loc3 (English_United States.1252) are not equal.
```

## <a name="op_call"></a>locale::operator()

比较两个 `basic_string` 对象。

```cpp
template <class CharType, class Traits, class Allocator>
bool operator()(
    const basic_string<CharType, Traits, Allocator>& left,
    const basic_string<CharType, Traits, Allocator>& right) const;
```

### <a name="parameters"></a>参数

*左*\
左侧的字符串。

*right*\
右侧的字符串。

### <a name="return-value"></a>返回值

此成员函数返回：

- 如果第一个序列小于第二个序列，则为 -1。

- 如果第一个序列大于第二个序列，则为 +1。

- 如果两个序列相等，则为 0。

### <a name="remarks"></a>备注

该成员函数有效执行以下操作：

```cpp
const collate<CharType>& fac = use_fac<collate<CharType>>(*this);

return (fac.compare(left.begin(), left.end(), right.begin(), right.end()) < 0);
```

这意味着可以使用区域设置对象作为函数对象。

### <a name="example"></a>示例

```cpp
// locale_op_compare.cpp
// compile with: /EHsc
#include <iostream>
#include <string>
#include <locale>

int main( )
{
   using namespace std;
   wchar_t *sa = L"ztesting";
   wchar_t *sb = L"\0x00DFtesting";
   basic_string<wchar_t> a( sa );
   basic_string<wchar_t> b( sb );

   locale loc( "German_Germany" );
   cout << loc( a,b ) << endl;

   const collate<wchar_t>& fac = use_facet<collate<wchar_t> >( loc );
   cout << ( fac.compare( sa, sa + a.length( ),
       sb, sb + b.length( ) ) < 0) << endl;
}
```

```Output
0
0
```

## <a name="op_eq_eq"></a>locale::operator==

测试两个区域设置是否相等。

```cpp
bool operator==(const locale& right) const;
```

### <a name="parameters"></a>参数

*right*\
要测试相等的区域设置之一。

### <a name="return-value"></a>返回值

一个布尔值，如果区域设置是相同区域设置的副本，则为**true** 。 如果区域设置不是相同区域设置的副本，则**为 false** 。

### <a name="remarks"></a>备注

如果两个区域设置是相同的区域设置（如果是另一个区域的副本）或它们的名称相同，则这两个区域设置是相等的。

### <a name="example"></a>示例

```cpp
// locale_op_eq.cpp
// compile with: /EHsc
#include <iostream>
#include <string>
#include <locale>

using namespace std;

int main( )
{
   locale loc1( "German_Germany" );
   locale loc2( "German_Germany" );
   locale loc3( "English" );

   if ( loc1 == loc2 )
      cout << "locales loc1 (" << loc1.name( )
      << ")\n and loc2 (" << loc2.name( ) << ") are equal."
      << endl;
   else
      cout << "locales loc1 (" << loc1.name( )
      << ")\n and loc2 (" << loc2.name( ) << ") are not equal."
      << endl;

   if ( loc1 == loc3 )
      cout << "locales loc1 (" << loc1.name( )
      << ")\n and loc3 (" << loc3.name( ) << ") are equal."
      << endl;
   else
      cout << "locales loc1 (" << loc1.name( )
      << ")\n and loc3 (" << loc3.name( ) << ") are not equal."
      << endl;
}
```

```Output
locales loc1 (German_Germany.1252)
and loc2 (German_Germany.1252) are equal.
locales loc1 (German_Germany.1252)
and loc3 (English_United States.1252) are not equal.
```

## <a name="see-also"></a>请参阅

[\<locale>](../standard-library/locale.md)\
[代码页](../c-runtime-library/code-pages.md)\
[区域设置名称、语言和国家/地区字符串](../c-runtime-library/locale-names-languages-and-country-region-strings.md)\
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)

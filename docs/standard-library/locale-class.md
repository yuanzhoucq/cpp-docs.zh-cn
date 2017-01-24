---
title: "locale 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "xlocale/std::locale"
  - "std::locale"
  - "std.locale"
  - "locale"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "locale 类"
ms.assetid: 7dd6d271-472d-4750-8fb5-ea8f55fbef62
caps.latest.revision: 28
caps.handback.revision: 28
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# locale 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

一种描述区域设置对象的类，此对象用于将特定于文化的信息封装为一组 facet 以共同定义特定本地化环境。  
  
## <a name="syntax"></a>语法  
  
```  
class locale;  
```  
  
## <a name="remarks"></a>备注  
 Facet 是指向派生类中的类对象的指针 [方面](#facet_class) ，其窗体的公共对象︰  
  
```  
static locale::id id;  
```  
  
 可以定义这些 facet 的开放式集。 还可以构建指定任意个 facet 的区域设置对象。  
  
 这些 facet 的预定义的组表示 [区域设置类别](#locale__category) 传统上被管理的标准 C 库中由该函数 `setlocale`。  
  
 类别 collate (LC_COLLATE) 包括以下 facet：  
  
```  
collate<char>  
collate<wchar_t>  
```  
  
 类别 ctype (LC_CTYPE) 包括以下 facet：  
  
```  
ctype<char>  
ctype<wchar_t>  
codecvt<char, char, mbstate_t>  
codecvt<wchar_t, char, mbstate_t>  
codecvt<char16_t, char, mbstate_t>  
codecvt<char32_t, char, mbstate_t>  
```  
  
 类别 monetary (LC_MONETARY) 包括以下 facet：  
  
```  
moneypunct<char, false>  
moneypunct<wchar_t, false>  
moneypunct<char, true>  
moneypunct<wchar_t, true>  
money_get<char, istreambuf_iterator<char>>  
money_get<wchar_t, istreambuf_iterator<wchar_t>>  
money_put<char, ostreambuf_iterator<char>>  
money_put<wchar_t, ostreambuf_iterator<wchar_t>>  
```  
  
 类别 numeric (LC_NUMERIC) 包括以下 facet：  
  
```  
num_get<char, istreambuf_iterator<char>>  
num_get<wchar_t, istreambuf_iterator<wchar_t>>  
num_put<char, ostreambuf_iterator<char>>  
num_put<wchar_t, ostreambuf_iterator<wchar_t>>  
numpunct<char>  
numpunct<wchar_t>  
```  
  
 类别 time (LC_TIME) 包括以下 facet：  
  
```  
time_get<char, istreambuf_iterator<char>>  
time_get<wchar_t, istreambuf_iterator<wchar_t>>  
time_put<char, ostreambuf_iterator<char>>  
time_put<wchar_t, ostreambuf_iterator<wchar_t>>  
```  
  
 类别 messages (LC_MESSAGES) 包括以下 facet：  
  
```  
messages<char>  
messages<wchar_t>  
```  
  
 （最后一个类别是 Posix 需要而非 C 标准需要的类别。）  
  
 其中某些预定义的 facet 由 iostreams 类使用，用来控制数值与文本序列的相互转换。  
  
 类的区域设置的对象还将区域设置名称存储为类的对象 [字符串](../Topic/%3Cstring%3E%20typedefs.md#string)。 使用无效的区域设置名称构造区域设置 facet 或区域设置对象，将引发类的对象 [runtime_error](../standard-library/runtime-error-class.md)。 如果区域设置对象无法确定 C 样式区域设置与此对象表示的区域设置完全对应，则存储的区域设置名称为 `"*"`。 否则，您可以建立匹配的区域设置用于区域设置对象的标准的 C 库内 `_Loc`, ，通过调用 `setlocale`(LC_ALL `,` `_Loc`。 [名称](#locale__name)`().c_str()`)。  
  
 在此实现中，还可以调用静态成员函数：  
  
```  
static locale empty();
```  
  
 构造不包含 facet 的区域设置对象。 它也是透明的区域设置;如果模板函数 [has_facet](../Topic/%3Clocale%3E%20functions.md#has_facet) 和 [use_facet](../Topic/%3Clocale%3E%20functions.md#use_facet) 找不到请求的 facet 在透明区域设置中，他们查阅首先全局区域设置，然后，如果此为透明，经典区域设置。 因此，你可以编写：  
  
```  
cout.imbue(locale::empty());
```  
  
 后续插入到 [cout](../Topic/%3Ciostream%3E%20functions.md#cout) 间接通过全局区域设置的当前状态。 你还可以编写：  
  
```  
locale loc(locale::empty(),
    locale::classic(),  
    locale::numeric);

cout.imbue(loc);
```   
  
 对 `cout` 的后续插入的数值格式设置规则与 C 区域设置相同，即使全局区域设置提供有关插入日期和货币金额的更改规则也是如此。  
  
### <a name="constructors"></a>构造函数  
  
|||  
|-|-|  
|[区域设置](#locale__locale)|创建区域设置、区域设置副本，或其中的 facet 或类别替换为其他区域设置中的 facet 类别的区域设置副本。|  
  
### <a name="typedefs"></a>Typedef  
  
|||  
|-|-|  
|[类别](#locale__category)|一种整数类型，此类型提供位掩码值以表示标准 facet 系列。|  
  
### <a name="member-functions"></a>成员函数  
  
|||  
|-|-|  
|[组合](#locale__combine)|将指定区域设置中的 facet 插入到目标区域设置。|  
|[名称](#locale__name)|返回存储的区域设置名称。|  
  
### <a name="static-functions"></a>静态函数  
  
|||  
|-|-|  
|[经典](#locale__classic)|此静态成员函数返回表示经典 C 区域设置的区域设置对象。|  
|[全局](#locale__global)|重置程序的默认区域设置。|  
  
### <a name="operators"></a>运算符  
  
|||  
|-|-|  
|[运算符 ！ =](#locale__operator_neq)|测试两个区域设置是否不相等。|  
|[operator （)](#locale__operator__)|比较两个 `basic_string` 对象。|  
|[运算符 = =](#locale__operator_eq_eq)|测试两个区域设置是否相等。|  
  
### <a name="classes"></a>类  
  
|||  
|-|-|  
|[方面](#facet_class)|一种类，此类用作所有区域设置 facet 的基类。|  
|[id](#id_class)|成员类提供用作索引以查找区域设置中的 facet 的唯一 facet 标识。|  
  
## <a name="requirements"></a>要求  
 **标头︰** \< 区域设置>  
  
 **命名空间：** std  
  
##  <a name="a-namelocalecategorya-localecategory"></a><a name="locale__category"></a>  locale:: category  
 一种整数类型，此类型提供位掩码值以表示标准 facet 系列。  
  
```  
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
 类型为同义词 `int` 可表示的一组非重复元素的位掩码类型键入类的区域设置的本地或可用于表示任何相应的 C 区域设置类别。 元素为︰  
  
- **逐份打印**, ，分别对应于 C 类别 LC_COLLATE  
  
- **ctype**, ，分别对应于 C 类别 LC_CTYPE  
  
- **货币**, ，分别对应于 C 类别 LC_MONETARY  
  
- **数值**, ，分别对应于 C 类别 LC_NUMERIC  
  
- **时间**, ，分别对应于 C 类别 LC_TIME  
  
- **消息**, ，分别对应于 Posix 类别 LC_MESSAGES  
  
 此外，两个有用的值是︰  
  
- **无**, ，分别对应于无 C 类别  
  
- **所有**, ，分别对应于所有类别 LC_ALL C 联合  
  
 您可以通过使用表示类别的任意组 `OR` 两个常数，如下所示 **货币** &#124; **时间**。  
  
##  <a name="a-namelocaleclassica-localeclassic"></a><a name="locale__classic"></a>  locale:: classic  
 此静态成员函数返回表示经典 C 区域设置的区域设置对象。  
  
```  
static const locale& classic();
```  
  
### <a name="return-value"></a>返回值  
 对 C 区域设置的引用。  
  
### <a name="remarks"></a>备注  
 经典 C 区域设置是美国英语 ASCII 隐式不国际化的程序中使用标准 C 库中的区域设置。  
  
### <a name="example"></a>示例  
  
```  
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
  
##  <a name="a-namelocalecombinea-localecombine"></a><a name="locale__combine"></a>  locale:: combine  
 将指定区域设置中的 facet 插入到目标区域设置。  
  
```  
template <class Facet>  
locale combine(const locale& _Loc) const;
```  
  
### <a name="parameters"></a>参数  
 `_Loc`  
 包含要插入到目标区域设置 facet 的区域设置。  
  
### <a name="return-value"></a>返回值  
 成员函数将返回在替换或添加到的区域设置对象 **\*这** 方面 `Facet` 中列出 `_Loc`。  
  
### <a name="example"></a>示例  
  
```  
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
  
##  <a name="a-namefacetclassa-facet-class"></a><a name="facet_class"></a>  facet 类  
 一种类，此类用作所有区域设置 facet 的基类。  
  
类方面 {保护︰ 显式方面 (size_t _Refs = 0); 虚拟 ~ facet(); 私有︰ facet(const facet&) / / 未定义 void 运算符 =(const facet&) / / 未定义};  
  
### <a name="remarks"></a>备注  
 请注意不能复制或分配类方面的对象。 可以构造和销毁对象派生自类 `locale::facet` ，但不是适当的基类的对象。 通常情况下，构造一个对象 `_Myfac` 源自方面，如下所示构造区域设置、 时 **localeloc**( `locale::classic`（)、 **新**`_Myfac`);  
  
 在这种情况下，基类方面的构造函数应具有零 `_Refs` 参数。 当不再需要对象时，将删除它。 因此，提供非零 _ *Refs* 仅在极少情况下，您负责该对象的生存期中的参数。  
  
##  <a name="a-namelocaleglobala-localeglobal"></a><a name="locale__global"></a>  locale:: global  
 重置程序的默认区域设置。 这对于 C 和 c + + 将影响全局区域设置。  
  
```  
static locale global(const locale& _Loc);
```  
  
### <a name="parameters"></a>参数  
 `_Loc`  
 要由该程序用作默认区域设置的区域设置。  
  
### <a name="return-value"></a>返回值  
 上一个区域设置默认区域设置被重置之前。  
  
### <a name="remarks"></a>备注  
 在程序启动时，全局区域设置是经典区域设置相同。  `global()` 函数调用 `setlocale( LC_ALL, loc.name. c_str())` 建立标准 C 库中匹配的区域设置。  
  
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
  
##  <a name="a-nameidclassa-id-class"></a><a name="id_class"></a>  id 类  
 成员类提供用作索引以查找区域设置中的 facet 的唯一 facet 标识。  
  
类 id {保护︰ id （）; private: id(const id&) / / 未定义 void 运算符 =(const id&) / / 未定义};  
  
### <a name="remarks"></a>备注  
 成员类描述所需的每个唯一的区域设置 facet，静态成员对象。 请注意，不能复制或分配类的对象 **id**。  
  
##  <a name="a-namelocalelocalea-localelocale"></a><a name="locale__locale"></a>  locale:: locale  
 创建区域设置、区域设置副本，或其中的 facet 或类别替换为其他区域设置中的 facet 类别的区域设置副本。  
  
```  
locale();

explicit locale(
    const char* _Locname,  
    category _Cat = all);

explicit locale(
    const string& _Locname);

locale(
    const locale& _Loc);

locale(
    const locale& _Loc,   
    const locale& _Other,  
    category _Cat);

locale(
    const locale& _Loc,   
    const char* _Locname,  
    category _Cat);

template <class Facet>  
locale(
 const locale& _Loc,   
    const Facet* _Fac);
```  
  
### <a name="parameters"></a>参数  
 `_Locname`  
 区域设置的名称。  
  
 `_Loc`  
 在构造新的区域设置要复制的区域设置。  
  
 `_Other`  
 从中选择一种类别的区域设置。  
  
 `_Cat`  
 要替换成构造区域设置的类别。  
  
 `_Fac`  
 要替换成构造区域设置 facet。  
  
### <a name="remarks"></a>备注  
 第一个构造函数初始化要与全局区域设置匹配的对象。 第二个和第三个构造函数初始化的所有区域设置类别具有与区域设置名称保持一致的行为 `_Locname`。 剩余的构造函数复制 `_Loc`, ，与所示的异常︰  
  
 `locale(const locale& _Loc, const locale& _Other, category _Cat);`  
  
 可以替换 `_Other` 这些方面与 C 类别对应的是哪一个 C （& a) `_Cat` 为非零值。  
  
 `locale(const locale& _Loc, const char* _Locname, category _Cat);`  
  
 `locale(const locale& _Loc, const string& _Locname, category _Cat);`  
  
 可以替换 `locale(_Locname, _All)` 这些方面与 C 类别对应的是哪一个 C （& a) `_Cat`为非零值。  
  
 `template<class Facet> locale(const locale& _Loc, Facet* _Fac);`  
  
 在替换 （或将添加到） `_Loc` 方面 `_Fac`, ，如果 `_Fac` 不是 null 指针。  
  
 如果区域设置名称 `_Locname` 为 null 指针或无效，该函数将引发 [runtime_error](../standard-library/runtime-error-class.md)。  
  
### <a name="example"></a>示例  
  
```  
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
  
##  <a name="a-namelocalenamea-localename"></a><a name="locale__name"></a>  locale:: name  
 返回存储的区域设置名称。  
  
```  
string name() const;
```  
  
### <a name="return-value"></a>返回值  
 字符串，它提供的区域设置名称。  
  
### <a name="example"></a>示例  
  
```  
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
  
##  <a name="a-namelocaleoperatorneqa-localeoperator"></a><a name="locale__operator_neq"></a>  locale:: operator ！ =  
 测试两个区域设置是否不相等。  
  
```  
bool operator!=(const locale& right) const;
```  
  
### <a name="parameters"></a>参数  
 ` right`  
 要测试不相等的区域设置之一。  
  
### <a name="return-value"></a>返回值  
 一个布尔值，则 **true** 如果区域设置不是相同的区域设置; 的副本 **false** 如果区域设置相同的区域设置的副本。  
  
### <a name="remarks"></a>备注  
 如果它们是相同的区域设置，如果有一份另一个，或者它们具有相同的名称，两个区域设置相等。  
  
### <a name="example"></a>示例  
  
```  
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
  
##  <a name="a-namelocaleoperatora-localeoperator"></a><a name="locale__operator__"></a>  locale:: operator （)  
 比较两个 `basic_string` 对象。  
  
```  
template <class CharType, class Traits, class Allocator>  
bool operator()(
    const basic_string<CharType, Traits, Allocator>& left,  
    const basic_string<CharType, Traits, Allocator>& right) const;
```  
  
### <a name="parameters"></a>参数  
 ` left`  
 左侧的字符串。  
  
 ` right`  
 右侧的字符串。  
  
### <a name="return-value"></a>返回值  
 成员函数将返回︰  
  
-   如果小于第二个序列号比较的第一个序列，则为 – 1。  
  
-   如果第二个序列的第一个序列小于比较 + 1。  
  
-   如果序列相等，则为 0。  
  
### <a name="remarks"></a>备注  
 成员函数有效执行操作︰  
  
```  
const collate<CharType>& fac = use_fac<collate<CharType>>(*this);

return (fac.compare(left.begin(), left.end(), right.begin(), right.end()) <0);
```  
  
 因此，您可以使用的区域设置对象作为函数对象。  
  
### <a name="example"></a>示例  
  
```  
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
  
##  <a name="a-namelocaleoperatoreqeqa-localeoperator"></a><a name="locale__operator_eq_eq"></a>  locale:: operator = =  
 测试两个区域设置是否相等。  
  
```  
bool operator==(const locale& right) const;
```  
  
### <a name="parameters"></a>参数  
 ` right`  
 要测试相等的区域设置之一。  
  
### <a name="return-value"></a>返回值  
 一个布尔值，则 **true** 如果区域设置相同的区域设置; 的副本 **false** 如果区域设置不是相同的区域设置的副本。  
  
### <a name="remarks"></a>备注  
 如果它们是相同的区域设置，如果有一份另一个，或者它们具有相同的名称，两个区域设置相等。  
  
### <a name="example"></a>示例  
  
```  
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
  
## <a name="see-also"></a>另请参阅  
 [\< 区域设置>](../standard-library/locale.md)   
 [代码页](../c-runtime-library/code-pages.md)   
 [区域设置名称、 语言和国家/地区字符串](../c-runtime-library/locale-names-languages-and-country-region-strings.md)   
 [C + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)


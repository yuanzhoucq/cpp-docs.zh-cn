---
title: "regex_traits 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- regex_traits
- std::regex_traits
- regex/std::regex_traits
- std::regex_traits::char_type
- regex/std::regex_traits::char_type
- std::regex_traits::size_type
- regex/std::regex_traits::size_type
- std::regex_traits::string_type
- regex/std::regex_traits::string_type
- std::regex_traits::locale_type
- regex/std::regex_traits::locale_type
- std::regex_traits::char_class_type
- regex/std::regex_traits::char_class_type
- std::regex_traits::length
- regex/std::regex_traits::length
- std::regex_traits::translate
- regex/std::regex_traits::translate
- std::regex_traits::translate_nocase
- regex/std::regex_traits::translate_nocase
- std::regex_traits::transform
- regex/std::regex_traits::transform
- std::regex_traits::transform_primary
- regex/std::regex_traits::transform_primary
- std::regex_traits::lookup_classname
- regex/std::regex_traits::lookup_classname
- std::regex_traits::lookup_collatename
- regex/std::regex_traits::lookup_collatename
- std::regex_traits::isctype
- regex/std::regex_traits::isctype
- std::regex_traits::value
- regex/std::regex_traits::value
- std::regex_traits::imbue
- regex/std::regex_traits::imbue
- std::regex_traits::getloc
- regex/std::regex_traits::getloc
dev_langs:
- C++
helpviewer_keywords:
- regex_traits class
ms.assetid: bc5a5eed-32fc-4eb7-913d-71c42e729e81
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 41b445ceeeb1f37ee9873cb55f62d30d480d8718
ms.openlocfilehash: b41e9b019477fe86645a212ee9f345e0fe8685f7
ms.lasthandoff: 02/24/2017

---
# <a name="regextraits-class"></a>regex_traits 类
描述用于匹配的元素的特征。  
  
## <a name="syntax"></a>语法  
```  
template<class Elem>
class regex_traits {  
public:  
   typedef Elem char_type;  
   typedef size_t size_type;  
   typedef basic_string<Elem> string_type;  
   typedef locale locale_type;  
   typedef ctype_base::mask char_class_type;  

   regex_traits();
   static size_type length(const char_type *str);
   char_type translate(char_type ch) const;
   char_type translate_nocase(char_type ch) const;
   template <class FwdIt>  
   string_type transform(FwdIt first, FwdIt last) const;
   template <class FwdIt>  
   string_type transform_primary(FwdIt first, FwdIt last) const;
   template <class FwdIt>  
   char_class_type lookup_classname(FwdIt first, FwdIt last) const;
   template <class FwdIt>  
   string_type lookup_collatename(FwdIt first, FwdIt last) const;
   bool isctype(char_type ch, char_class_type cls) const;
   int value(char_type ch, int base) const;
   locale_type imbue(locale_type loc);
   locale_type getloc() const;
};  
 ``` 
#### <a name="parameters"></a>参数  
 `Elem`  
 要描述的字符元素类型。  
  
## <a name="remarks"></a>备注  
 此模板类描述 `Elem`类型的各种正则表达式特征。 此模板类 [basic_regex 类](../standard-library/basic-regex-class.md) 使用此信息来操作 `Elem` 类的元素。  
  
 每个 `regex_traits` 对象包含 `regex_traits::locale` 类型的对象，该对象由它的一些成员函数使用。 默认区域设置是一份 `regex_traits::locale()`副本。 成员函数 `imbue` 替换区域设置对象，而成员函数 `getloc` 返回区域设置对象的副本。  
  
## <a name="requirements"></a>要求  
 **标头：**\<regex&1;>  
  
 **命名空间：** std  
  
##  <a name="a-nameregextraitscharclasstypea--regextraitscharclasstype"></a><a name="regex_traits__char_class_type"></a>regex_traits::char_class_type  
 字符类指示符的类型。  
  
```  
typedef T8 char_class_type;  
```  
  
### <a name="remarks"></a>备注  
 类型用于指定字符类的未指定类型的同义词。 可以使用 `|` 运算符指定属于由操作数指定的类并集的字符类，从而组合此类型的值。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__regex__regex_traits_char_class_type.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_traits<char> Mytr;   
int main()   
    {   
    Mytr tr;   
  
    Mytr::char_type ch = tr.translate('a');   
    std::cout << "translate('a') == 'a' == " << std::boolalpha   
        << (ch == 'a') << std::endl;   
  
    std::cout << "nocase 'a' == 'A' == " << std::boolalpha   
        << (tr.translate_nocase('a') == tr.translate_nocase('A'))   
        << std::endl;   
  
    const char *lbegin = "abc";   
    const char *lend = lbegin + strlen(lbegin);   
    Mytr::size_type size = tr.length(lbegin);   
    std::cout << "length(\"abc\") == " << size <<std::endl;   
  
    Mytr::string_type str = tr.transform(lbegin, lend);   
    std::cout << "transform(\"abc\") < \"abc\" == " << std::boolalpha   
        << (str < "abc") << std::endl;   
  
    const char *ubegin = "ABC";   
    const char *uend = ubegin + strlen(ubegin);   
    std::cout << "primary \"ABC\" < \"abc\" == " << std::boolalpha   
        << (tr.transform_primary(ubegin, uend) <   
            tr.transform_primary(lbegin, lend))   
        << std::endl;   
  
    const char *dig = "digit";   
    Mytr::char_class_type cl = tr.lookup_classname(dig, dig + 5);   
    std::cout << "class digit == d == " << std::boolalpha   
        << (cl == tr.lookup_classname(dig, dig + 1))   
        << std::endl;   
  
    std::cout << "'3' is digit == " <<std::boolalpha   
        << tr.isctype('3', tr.lookup_classname(dig, dig + 5))   
        << std::endl;   
  
    std::cout << "hex C == " << tr.value('C', 16) << std::endl;   
  
// other members   
    str = tr.lookup_collatename(dig, dig + 5);   
  
    Mytr::locale_type loc = tr.getloc();   
    tr.imbue(loc);   
  
    return (0);   
    }  
  
```  
  
```Output  
translate('a') == 'a' == true  
nocase 'a' == 'A' == true  
length("abc") == 3  
transform("abc") < "abc" == false  
primary "ABC" < "abc" == false  
class digit == d == true  
'3' is digit == true  
hex C == 12  
```  
  
##  <a name="a-nameregextraitschartypea--regextraitschartype"></a><a name="regex_traits__char_type"></a>  regex_traits::char_type  
 元素的类型。  
  
```  
typedef Elem char_type;  
```  
  
### <a name="remarks"></a>备注  
 Typedef 是模板参数 `Elem`的同义词。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__regex__regex_traits_char_type.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_traits<char> Mytr;   
int main()   
    {   
    Mytr tr;   
  
    Mytr::char_type ch = tr.translate('a');   
    std::cout << "translate('a') == 'a' == " << std::boolalpha   
        << (ch == 'a') << std::endl;   
  
    std::cout << "nocase 'a' == 'A' == " << std::boolalpha   
        << (tr.translate_nocase('a') == tr.translate_nocase('A'))   
        << std::endl;   
  
    const char *lbegin = "abc";   
    const char *lend = lbegin + strlen(lbegin);   
    Mytr::size_type size = tr.length(lbegin);   
    std::cout << "length(\"abc\") == " << size <<std::endl;   
  
    Mytr::string_type str = tr.transform(lbegin, lend);   
    std::cout << "transform(\"abc\") < \"abc\" == " << std::boolalpha   
        << (str < "abc") << std::endl;   
  
    const char *ubegin = "ABC";   
    const char *uend = ubegin + strlen(ubegin);   
    std::cout << "primary \"ABC\" < \"abc\" == " << std::boolalpha   
        << (tr.transform_primary(ubegin, uend) <   
            tr.transform_primary(lbegin, lend))   
        << std::endl;   
  
    const char *dig = "digit";   
    Mytr::char_class_type cl = tr.lookup_classname(dig, dig + 5);   
    std::cout << "class digit == d == " << std::boolalpha   
        << (cl == tr.lookup_classname(dig, dig + 1))   
        << std::endl;   
  
    std::cout << "'3' is digit == " <<std::boolalpha   
        << tr.isctype('3', tr.lookup_classname(dig, dig + 5))   
        << std::endl;   
  
    std::cout << "hex C == " << tr.value('C', 16) << std::endl;   
  
// other members   
    str = tr.lookup_collatename(dig, dig + 5);   
  
    Mytr::locale_type loc = tr.getloc();   
    tr.imbue(loc);   
  
    return (0);   
    }  
  
```  
  
```Output  
translate('a') == 'a' == true  
nocase 'a' == 'A' == true  
length("abc") == 3  
transform("abc") < "abc" == false  
primary "ABC" < "abc" == false  
class digit == d == true  
'3' is digit == true  
hex C == 12  
```  
  
##  <a name="a-nameregextraitsgetloca--regextraitsgetloc"></a><a name="regex_traits__getloc"></a>  regex_traits::getloc  
 返回存储的区域设置对象。  
  
```  
locale_type getloc() const;
```  
  
### <a name="remarks"></a>备注  
 此成员函数返回存储的 `locale` 对象。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__regex__regex_traits_getloc.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_traits<char> Mytr;   
int main()   
    {   
    Mytr tr;   
  
    Mytr::char_type ch = tr.translate('a');   
    std::cout << "translate('a') == 'a' == " << std::boolalpha   
        << (ch == 'a') << std::endl;   
  
    std::cout << "nocase 'a' == 'A' == " << std::boolalpha   
        << (tr.translate_nocase('a') == tr.translate_nocase('A'))   
        << std::endl;   
  
    const char *lbegin = "abc";   
    const char *lend = lbegin + strlen(lbegin);   
    Mytr::size_type size = tr.length(lbegin);   
    std::cout << "length(\"abc\") == " << size <<std::endl;   
  
    Mytr::string_type str = tr.transform(lbegin, lend);   
    std::cout << "transform(\"abc\") < \"abc\" == " << std::boolalpha   
        << (str < "abc") << std::endl;   
  
    const char *ubegin = "ABC";   
    const char *uend = ubegin + strlen(ubegin);   
    std::cout << "primary \"ABC\" < \"abc\" == " << std::boolalpha   
        << (tr.transform_primary(ubegin, uend) <   
            tr.transform_primary(lbegin, lend))   
        << std::endl;   
  
    const char *dig = "digit";   
    Mytr::char_class_type cl = tr.lookup_classname(dig, dig + 5);   
    std::cout << "class digit == d == " << std::boolalpha   
        << (cl == tr.lookup_classname(dig, dig + 1))   
        << std::endl;   
  
    std::cout << "'3' is digit == " <<std::boolalpha   
        << tr.isctype('3', tr.lookup_classname(dig, dig + 5))   
        << std::endl;   
  
    std::cout << "hex C == " << tr.value('C', 16) << std::endl;   
  
// other members   
    str = tr.lookup_collatename(dig, dig + 5);   
  
    Mytr::locale_type loc = tr.getloc();   
    tr.imbue(loc);   
  
    return (0);   
    }  
  
```  
  
```Output  
translate('a') == 'a' == true  
nocase 'a' == 'A' == true  
length("abc") == 3  
transform("abc") < "abc" == false  
primary "ABC" < "abc" == false  
class digit == d == true  
'3' is digit == true  
hex C == 12  
```  
  
##  <a name="a-nameregextraitsimbuea--regextraitsimbue"></a><a name="regex_traits__imbue"></a>  regex_traits::imbue  
 更改存储的区域设置对象。  
  
```  
locale_type imbue(locale_type loc);
```  
  
### <a name="parameters"></a>参数  
 `loc`  
 要存储的区域设置对象。  
  
### <a name="remarks"></a>备注  
 成员函数将 `loc` 复制到存储的 `locale` 对象，并返回存储的 `locale` 对象的以前值的副本。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__regex__regex_traits_imbue.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_traits<char> Mytr;   
int main()   
    {   
    Mytr tr;   
  
    Mytr::char_type ch = tr.translate('a');   
    std::cout << "translate('a') == 'a' == " << std::boolalpha   
        << (ch == 'a') << std::endl;   
  
    std::cout << "nocase 'a' == 'A' == " << std::boolalpha   
        << (tr.translate_nocase('a') == tr.translate_nocase('A'))   
        << std::endl;   
  
    const char *lbegin = "abc";   
    const char *lend = lbegin + strlen(lbegin);   
    Mytr::size_type size = tr.length(lbegin);   
    std::cout << "length(\"abc\") == " << size <<std::endl;   
  
    Mytr::string_type str = tr.transform(lbegin, lend);   
    std::cout << "transform(\"abc\") < \"abc\" == " << std::boolalpha   
        << (str < "abc") << std::endl;   
  
    const char *ubegin = "ABC";   
    const char *uend = ubegin + strlen(ubegin);   
    std::cout << "primary \"ABC\" < \"abc\" == " << std::boolalpha   
        << (tr.transform_primary(ubegin, uend) <   
            tr.transform_primary(lbegin, lend))   
        << std::endl;   
  
    const char *dig = "digit";   
    Mytr::char_class_type cl = tr.lookup_classname(dig, dig + 5);   
    std::cout << "class digit == d == " << std::boolalpha   
        << (cl == tr.lookup_classname(dig, dig + 1))   
        << std::endl;   
  
    std::cout << "'3' is digit == " <<std::boolalpha   
        << tr.isctype('3', tr.lookup_classname(dig, dig + 5))   
        << std::endl;   
  
    std::cout << "hex C == " << tr.value('C', 16) << std::endl;   
  
// other members   
    str = tr.lookup_collatename(dig, dig + 5);   
  
    Mytr::locale_type loc = tr.getloc();   
    tr.imbue(loc);   
  
    return (0);   
    }  
  
```  
  
```Output  
translate('a') == 'a' == true  
nocase 'a' == 'A' == true  
length("abc") == 3  
transform("abc") < "abc" == false  
primary "ABC" < "abc" == false  
class digit == d == true  
'3' is digit == true  
hex C == 12  
```  
  
##  <a name="a-nameregextraitsisctypea--regextraitsisctype"></a><a name="regex_traits__isctype"></a>  regex_traits::isctype  
 类成员资格测试。  
  
```  
bool isctype(char_type ch, char_class_type cls) const;
```  
  
### <a name="parameters"></a>参数  
 `ch`  
 要测试的元素。  
  
 `cls`  
 要测试的类。  
  
### <a name="remarks"></a>备注  
 仅当字符 `ch` 属于 `cls`指定的字符类时，成员函数才返回 true。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__regex__regex_traits_isctype.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_traits<char> Mytr;   
int main()   
    {   
    Mytr tr;   
  
    Mytr::char_type ch = tr.translate('a');   
    std::cout << "translate('a') == 'a' == " << std::boolalpha   
        << (ch == 'a') << std::endl;   
  
    std::cout << "nocase 'a' == 'A' == " << std::boolalpha   
        << (tr.translate_nocase('a') == tr.translate_nocase('A'))   
        << std::endl;   
  
    const char *lbegin = "abc";   
    const char *lend = lbegin + strlen(lbegin);   
    Mytr::size_type size = tr.length(lbegin);   
    std::cout << "length(\"abc\") == " << size <<std::endl;   
  
    Mytr::string_type str = tr.transform(lbegin, lend);   
    std::cout << "transform(\"abc\") < \"abc\" == " << std::boolalpha   
        << (str < "abc") << std::endl;   
  
    const char *ubegin = "ABC";   
    const char *uend = ubegin + strlen(ubegin);   
    std::cout << "primary \"ABC\" < \"abc\" == " << std::boolalpha   
        << (tr.transform_primary(ubegin, uend) <   
            tr.transform_primary(lbegin, lend))   
        << std::endl;   
  
    const char *dig = "digit";   
    Mytr::char_class_type cl = tr.lookup_classname(dig, dig + 5);   
    std::cout << "class digit == d == " << std::boolalpha   
        << (cl == tr.lookup_classname(dig, dig + 1))   
        << std::endl;   
  
    std::cout << "'3' is digit == " <<std::boolalpha   
        << tr.isctype('3', tr.lookup_classname(dig, dig + 5))   
        << std::endl;   
  
    std::cout << "hex C == " << tr.value('C', 16) << std::endl;   
  
// other members   
    str = tr.lookup_collatename(dig, dig + 5);   
  
    Mytr::locale_type loc = tr.getloc();   
    tr.imbue(loc);   
  
    return (0);   
    }  
  
```  
  
```Output  
translate('a') == 'a' == true  
nocase 'a' == 'A' == true  
length("abc") == 3  
transform("abc") < "abc" == false  
primary "ABC" < "abc" == false  
class digit == d == true  
'3' is digit == true  
hex C == 12  
```  
  
##  <a name="a-nameregextraitslengtha--regextraitslength"></a><a name="regex_traits__length"></a>  regex_traits::length  
 返回以 null 结尾的序列的长度。  
  
```  
static size_type length(const char_type *str);
```  
  
### <a name="parameters"></a>参数  
 `str`  
 以 null 结尾的序列。  
  
### <a name="remarks"></a>备注  
 此静态成员函数返回 `std::char_traits<char_type>::length(str)`。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__regex__regex_traits_length.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_traits<char> Mytr;   
int main()   
    {   
    Mytr tr;   
  
    Mytr::char_type ch = tr.translate('a');   
    std::cout << "translate('a') == 'a' == " << std::boolalpha   
        << (ch == 'a') << std::endl;   
  
    std::cout << "nocase 'a' == 'A' == " << std::boolalpha   
        << (tr.translate_nocase('a') == tr.translate_nocase('A'))   
        << std::endl;   
  
    const char *lbegin = "abc";   
    const char *lend = lbegin + strlen(lbegin);   
    Mytr::size_type size = tr.length(lbegin);   
    std::cout << "length(\"abc\") == " << size <<std::endl;   
  
    Mytr::string_type str = tr.transform(lbegin, lend);   
    std::cout << "transform(\"abc\") < \"abc\" == " << std::boolalpha   
        << (str < "abc") << std::endl;   
  
    const char *ubegin = "ABC";   
    const char *uend = ubegin + strlen(ubegin);   
    std::cout << "primary \"ABC\" < \"abc\" == " << std::boolalpha   
        << (tr.transform_primary(ubegin, uend) <   
            tr.transform_primary(lbegin, lend))   
        << std::endl;   
  
    const char *dig = "digit";   
    Mytr::char_class_type cl = tr.lookup_classname(dig, dig + 5);   
    std::cout << "class digit == d == " << std::boolalpha   
        << (cl == tr.lookup_classname(dig, dig + 1))   
        << std::endl;   
  
    std::cout << "'3' is digit == " <<std::boolalpha   
        << tr.isctype('3', tr.lookup_classname(dig, dig + 5))   
        << std::endl;   
  
    std::cout << "hex C == " << tr.value('C', 16) << std::endl;   
  
// other members   
    str = tr.lookup_collatename(dig, dig + 5);   
  
    Mytr::locale_type loc = tr.getloc();   
    tr.imbue(loc);   
  
    return (0);   
    }  
  
```  
  
```Output  
translate('a') == 'a' == true  
nocase 'a' == 'A' == true  
length("abc") == 3  
transform("abc") < "abc" == false  
primary "ABC" < "abc" == false  
class digit == d == true  
'3' is digit == true  
hex C == 12  
```  
  
##  <a name="a-nameregextraitslocaletypea--regextraitslocaletype"></a><a name="regex_traits__locale_type"></a>  regex_traits::locale_type  
 存储的区域设置对象的类型。  
  
```  
typedef T7 locale_type;  
```  
  
### <a name="remarks"></a>备注  
 Typedef 是封装区域设置的类型的同义词。 在专业 `regex_traits<char>` 和 `regex_traits<wchar_t>` 中，它是 `std::locale`的同义词。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__regex__regex_traits_locale_type.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_traits<char> Mytr;   
int main()   
    {   
    Mytr tr;   
  
    Mytr::char_type ch = tr.translate('a');   
    std::cout << "translate('a') == 'a' == " << std::boolalpha   
        << (ch == 'a') << std::endl;   
  
    std::cout << "nocase 'a' == 'A' == " << std::boolalpha   
        << (tr.translate_nocase('a') == tr.translate_nocase('A'))   
        << std::endl;   
  
    const char *lbegin = "abc";   
    const char *lend = lbegin + strlen(lbegin);   
    Mytr::size_type size = tr.length(lbegin);   
    std::cout << "length(\"abc\") == " << size <<std::endl;   
  
    Mytr::string_type str = tr.transform(lbegin, lend);   
    std::cout << "transform(\"abc\") < \"abc\" == " << std::boolalpha   
        << (str < "abc") << std::endl;   
  
    const char *ubegin = "ABC";   
    const char *uend = ubegin + strlen(ubegin);   
    std::cout << "primary \"ABC\" < \"abc\" == " << std::boolalpha   
        << (tr.transform_primary(ubegin, uend) <   
            tr.transform_primary(lbegin, lend))   
        << std::endl;   
  
    const char *dig = "digit";   
    Mytr::char_class_type cl = tr.lookup_classname(dig, dig + 5);   
    std::cout << "class digit == d == " << std::boolalpha   
        << (cl == tr.lookup_classname(dig, dig + 1))   
        << std::endl;   
  
    std::cout << "'3' is digit == " <<std::boolalpha   
        << tr.isctype('3', tr.lookup_classname(dig, dig + 5))   
        << std::endl;   
  
    std::cout << "hex C == " << tr.value('C', 16) << std::endl;   
  
// other members   
    str = tr.lookup_collatename(dig, dig + 5);   
  
    Mytr::locale_type loc = tr.getloc();   
    tr.imbue(loc);   
  
    return (0);   
    }  
  
```  
  
```Output  
translate('a') == 'a' == true  
nocase 'a' == 'A' == true  
length("abc") == 3  
transform("abc") < "abc" == false  
primary "ABC" < "abc" == false  
class digit == d == true  
'3' is digit == true  
hex C == 12  
```  
  
##  <a name="a-nameregextraitslookupclassnamea--regextraitslookupclassname"></a><a name="regex_traits__lookup_classname"></a>  regex_traits::lookup_classname  
 将序列映射到字符类。  
  
```  
template <class FwdIt>  
char_class_type lookup_classname(FwdIt first, FwdIt last) const;
```  
  
### <a name="parameters"></a>参数  
 `first`  
 要查找的序列的开头。  
  
 `last`  
 要查找的序列的结尾。  
  
### <a name="remarks"></a>备注  
 该成员函数返回一个值，该值指定由其自变量指向的字符序列命名的字符类。 该值不依赖序列中字符的大小写。  
  
 专用化 `regex_traits<char>` 识别名称 `"d"`、`"s"`、`"w"`、`"alnum"`、`"alpha"`、`"blank"`、`"cntrl"`、`"digit"`、`"graph"`、`"lower"`、`"print"`、`"punct"`、`"space"`、`"upper"` 和 `"xdigit"`，均不区分大小写。  
  
 专用化 `regex_traits<wchar_t>` 识别名称 `L"d"`、`L"s"`、`L"w"`、`L"alnum"`、`L"alpha"`、`L"blank"`、`L"cntrl"`、`L"digit"`、`L"graph"`、`L"lower"`、`L"print"`、`L"punct"`、`L"space"`、`L"upper"` 和 `L"xdigit"`，均不区分大小写。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__regex__regex_traits_lookup_classname.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_traits<char> Mytr;   
int main()   
    {   
    Mytr tr;   
  
    Mytr::char_type ch = tr.translate('a');   
    std::cout << "translate('a') == 'a' == " << std::boolalpha   
        << (ch == 'a') << std::endl;   
  
    std::cout << "nocase 'a' == 'A' == " << std::boolalpha   
        << (tr.translate_nocase('a') == tr.translate_nocase('A'))   
        << std::endl;   
  
    const char *lbegin = "abc";   
    const char *lend = lbegin + strlen(lbegin);   
    Mytr::size_type size = tr.length(lbegin);   
    std::cout << "length(\"abc\") == " << size <<std::endl;   
  
    Mytr::string_type str = tr.transform(lbegin, lend);   
    std::cout << "transform(\"abc\") < \"abc\" == " << std::boolalpha   
        << (str < "abc") << std::endl;   
  
    const char *ubegin = "ABC";   
    const char *uend = ubegin + strlen(ubegin);   
    std::cout << "primary \"ABC\" < \"abc\" == " << std::boolalpha   
        << (tr.transform_primary(ubegin, uend) <   
            tr.transform_primary(lbegin, lend))   
        << std::endl;   
  
    const char *dig = "digit";   
    Mytr::char_class_type cl = tr.lookup_classname(dig, dig + 5);   
    std::cout << "class digit == d == " << std::boolalpha   
        << (cl == tr.lookup_classname(dig, dig + 1))   
        << std::endl;   
  
    std::cout << "'3' is digit == " <<std::boolalpha   
        << tr.isctype('3', tr.lookup_classname(dig, dig + 5))   
        << std::endl;   
  
    std::cout << "hex C == " << tr.value('C', 16) << std::endl;   
  
// other members   
    str = tr.lookup_collatename(dig, dig + 5);   
  
    Mytr::locale_type loc = tr.getloc();   
    tr.imbue(loc);   
  
    return (0);   
    }  
  
```  
  
```Output  
translate('a') == 'a' == true  
nocase 'a' == 'A' == true  
length("abc") == 3  
transform("abc") < "abc" == false  
primary "ABC" < "abc" == false  
class digit == d == true  
'3' is digit == true  
hex C == 12  
```  
  
##  <a name="a-nameregextraitslookupcollatenamea--regextraitslookupcollatename"></a><a name="regex_traits__lookup_collatename"></a>  regex_traits::lookup_collatename  
 将序列映射到排序规则元素。  
  
```  
template <class FwdIt>  
string_type lookup_collatename(FwdIt first, FwdIt last) const;
```  
  
### <a name="parameters"></a>参数  
 `first`  
 要查找的序列的开头。  
  
 `last`  
 要查找的序列的结尾。  
  
### <a name="remarks"></a>备注  
 此成员函数将返回一个字符串对象，它包含对应于序列 `[first, last)`的排序规则元素；如果该序列不是有效的排序规则元素，则返回空字符串。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__regex__regex_traits_lookup_collatename.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_traits<char> Mytr;   
int main()   
    {   
    Mytr tr;   
  
    Mytr::char_type ch = tr.translate('a');   
    std::cout << "translate('a') == 'a' == " << std::boolalpha   
        << (ch == 'a') << std::endl;   
  
    std::cout << "nocase 'a' == 'A' == " << std::boolalpha   
        << (tr.translate_nocase('a') == tr.translate_nocase('A'))   
        << std::endl;   
  
    const char *lbegin = "abc";   
    const char *lend = lbegin + strlen(lbegin);   
    Mytr::size_type size = tr.length(lbegin);   
    std::cout << "length(\"abc\") == " << size <<std::endl;   
  
    Mytr::string_type str = tr.transform(lbegin, lend);   
    std::cout << "transform(\"abc\") < \"abc\" == " << std::boolalpha   
        << (str < "abc") << std::endl;   
  
    const char *ubegin = "ABC";   
    const char *uend = ubegin + strlen(ubegin);   
    std::cout << "primary \"ABC\" < \"abc\" == " << std::boolalpha   
        << (tr.transform_primary(ubegin, uend) <   
            tr.transform_primary(lbegin, lend))   
        << std::endl;   
  
    const char *dig = "digit";   
    Mytr::char_class_type cl = tr.lookup_classname(dig, dig + 5);   
    std::cout << "class digit == d == " << std::boolalpha   
        << (cl == tr.lookup_classname(dig, dig + 1))   
        << std::endl;   
  
    std::cout << "'3' is digit == " <<std::boolalpha   
        << tr.isctype('3', tr.lookup_classname(dig, dig + 5))   
        << std::endl;   
  
    std::cout << "hex C == " << tr.value('C', 16) << std::endl;   
  
// other members   
    str = tr.lookup_collatename(dig, dig + 5);   
  
    Mytr::locale_type loc = tr.getloc();   
    tr.imbue(loc);   
  
    return (0);   
    }  
  
```  
  
```Output  
translate('a') == 'a' == true  
nocase 'a' == 'A' == true  
length("abc") == 3  
transform("abc") < "abc" == false  
primary "ABC" < "abc" == false  
class digit == d == true  
'3' is digit == true  
hex C == 12  
```  
  
##  <a name="a-nameregextraitsregextraitsa--regextraitsregextraits"></a><a name="regex_traits__regex_traits"></a>regex_traits::regex_traits  
 构造对象。  
  
```  
regex_traits();
```  
  
### <a name="remarks"></a>备注  
 构造函数构造其存储的 `locale` 对象初始化为默认区域设置的对象。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__regex__regex_traits_construct.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_traits<char> Mytr;   
int main()   
    {   
    Mytr tr;   
  
    Mytr::char_type ch = tr.translate('a');   
    std::cout << "translate('a') == 'a' == " << std::boolalpha   
        << (ch == 'a') << std::endl;   
  
    std::cout << "nocase 'a' == 'A' == " << std::boolalpha   
        << (tr.translate_nocase('a') == tr.translate_nocase('A'))   
        << std::endl;   
  
    const char *lbegin = "abc";   
    const char *lend = lbegin + strlen(lbegin);   
    Mytr::size_type size = tr.length(lbegin);   
    std::cout << "length(\"abc\") == " << size <<std::endl;   
  
    Mytr::string_type str = tr.transform(lbegin, lend);   
    std::cout << "transform(\"abc\") < \"abc\" == " << std::boolalpha   
        << (str < "abc") << std::endl;   
  
    const char *ubegin = "ABC";   
    const char *uend = ubegin + strlen(ubegin);   
    std::cout << "primary \"ABC\" < \"abc\" == " << std::boolalpha   
        << (tr.transform_primary(ubegin, uend) <   
            tr.transform_primary(lbegin, lend))   
        << std::endl;   
  
    const char *dig = "digit";   
    Mytr::char_class_type cl = tr.lookup_classname(dig, dig + 5);   
    std::cout << "class digit == d == " << std::boolalpha   
        << (cl == tr.lookup_classname(dig, dig + 1))   
        << std::endl;   
  
    std::cout << "'3' is digit == " <<std::boolalpha   
        << tr.isctype('3', tr.lookup_classname(dig, dig + 5))   
        << std::endl;   
  
    std::cout << "hex C == " << tr.value('C', 16) << std::endl;   
  
// other members   
    str = tr.lookup_collatename(dig, dig + 5);   
  
    Mytr::locale_type loc = tr.getloc();   
    tr.imbue(loc);   
  
    return (0);   
    }  
  
```  
  
```Output  
translate('a') == 'a' == true  
nocase 'a' == 'A' == true  
length("abc") == 3  
transform("abc") < "abc" == false  
primary "ABC" < "abc" == false  
class digit == d == true  
'3' is digit == true  
hex C == 12  
```  
  
##  <a name="a-nameregextraitssizetypea--regextraitssizetype"></a><a name="regex_traits__size_type"></a>regex_traits::size_type  
 序列长度的类型。  
  
```  
typedef T6 size_type;  
```  
  
### <a name="remarks"></a>备注  
 typedef 是无符号整数类型的同义词。 在专业 `regex_traits<char>` 和 `regex_traits<wchar_t>` 中，它是 `std::size_t` 的同义词。  
  
 typedef 是 `std::size_t` 的同义词。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__regex__regex_traits_size_type.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_traits<char> Mytr;   
int main()   
    {   
    Mytr tr;   
  
    Mytr::char_type ch = tr.translate('a');   
    std::cout << "translate('a') == 'a' == " << std::boolalpha   
        << (ch == 'a') << std::endl;   
  
    std::cout << "nocase 'a' == 'A' == " << std::boolalpha   
        << (tr.translate_nocase('a') == tr.translate_nocase('A'))   
        << std::endl;   
  
    const char *lbegin = "abc";   
    const char *lend = lbegin + strlen(lbegin);   
    Mytr::size_type size = tr.length(lbegin);   
    std::cout << "length(\"abc\") == " << size <<std::endl;   
  
    Mytr::string_type str = tr.transform(lbegin, lend);   
    std::cout << "transform(\"abc\") < \"abc\" == " << std::boolalpha   
        << (str < "abc") << std::endl;   
  
    const char *ubegin = "ABC";   
    const char *uend = ubegin + strlen(ubegin);   
    std::cout << "primary \"ABC\" < \"abc\" == " << std::boolalpha   
        << (tr.transform_primary(ubegin, uend) <   
            tr.transform_primary(lbegin, lend))   
        << std::endl;   
  
    const char *dig = "digit";   
    Mytr::char_class_type cl = tr.lookup_classname(dig, dig + 5);   
    std::cout << "class digit == d == " << std::boolalpha   
        << (cl == tr.lookup_classname(dig, dig + 1))   
        << std::endl;   
  
    std::cout << "'3' is digit == " <<std::boolalpha   
        << tr.isctype('3', tr.lookup_classname(dig, dig + 5))   
        << std::endl;   
  
    std::cout << "hex C == " << tr.value('C', 16) << std::endl;   
  
// other members   
    str = tr.lookup_collatename(dig, dig + 5);   
  
    Mytr::locale_type loc = tr.getloc();   
    tr.imbue(loc);   
  
    return (0);   
    }  
  
```  
  
```Output  
translate('a') == 'a' == true  
nocase 'a' == 'A' == true  
length("abc") == 3  
transform("abc") < "abc" == false  
primary "ABC" < "abc" == false  
class digit == d == true  
'3' is digit == true  
hex C == 12  
```  
  
##  <a name="a-nameregextraitsstringtypea--regextraitsstringtype"></a><a name="regex_traits__string_type"></a>regex_traits::string_type  
 元素字符串的类型。  
  
```  
typedef basic_string<Elem> string_type;  
```  
  
### <a name="remarks"></a>备注  
 typedef 是 `basic_string<Elem>`的同义词。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__regex__regex_traits_string_type.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_traits<char> Mytr;   
int main()   
    {   
    Mytr tr;   
  
    Mytr::char_type ch = tr.translate('a');   
    std::cout << "translate('a') == 'a' == " << std::boolalpha   
        << (ch == 'a') << std::endl;   
  
    std::cout << "nocase 'a' == 'A' == " << std::boolalpha   
        << (tr.translate_nocase('a') == tr.translate_nocase('A'))   
        << std::endl;   
  
    const char *lbegin = "abc";   
    const char *lend = lbegin + strlen(lbegin);   
    Mytr::size_type size = tr.length(lbegin);   
    std::cout << "length(\"abc\") == " << size <<std::endl;   
  
    Mytr::string_type str = tr.transform(lbegin, lend);   
    std::cout << "transform(\"abc\") < \"abc\" == " << std::boolalpha   
        << (str < "abc") << std::endl;   
  
    const char *ubegin = "ABC";   
    const char *uend = ubegin + strlen(ubegin);   
    std::cout << "primary \"ABC\" < \"abc\" == " << std::boolalpha   
        << (tr.transform_primary(ubegin, uend) <   
            tr.transform_primary(lbegin, lend))   
        << std::endl;   
  
    const char *dig = "digit";   
    Mytr::char_class_type cl = tr.lookup_classname(dig, dig + 5);   
    std::cout << "class digit == d == " << std::boolalpha   
        << (cl == tr.lookup_classname(dig, dig + 1))   
        << std::endl;   
  
    std::cout << "'3' is digit == " <<std::boolalpha   
        << tr.isctype('3', tr.lookup_classname(dig, dig + 5))   
        << std::endl;   
  
    std::cout << "hex C == " << tr.value('C', 16) << std::endl;   
  
// other members   
    str = tr.lookup_collatename(dig, dig + 5);   
  
    Mytr::locale_type loc = tr.getloc();   
    tr.imbue(loc);   
  
    return (0);   
    }  
  
```  
  
```Output  
translate('a') == 'a' == true  
nocase 'a' == 'A' == true  
length("abc") == 3  
transform("abc") < "abc" == false  
primary "ABC" < "abc" == false  
class digit == d == true  
'3' is digit == true  
hex C == 12  
```  
  
##  <a name="a-nameregextraitstransforma--regextraitstransform"></a><a name="regex_traits__transform"></a>regex_traits::transform  
 转换为等效顺序序列。  
  
```  
template <class FwdIt>  
string_type transform(FwdIt first, FwdIt last) const;
```  
  
### <a name="parameters"></a>参数  
 `first`  
 要转换的序列的开头。  
  
 `last`  
 要转换的序列的结尾。  
  
### <a name="remarks"></a>备注  
 此成员函数返回它使用转换规则生成的字符串，转换规则依赖于 `locale` 对象。 对于由迭代器范围 `[first1, last1)` 和 `[first2, last2)`指定的两个字符序列，如果由迭代器范围 `transform(first1, last1) < transform(first2, last2)` 指定的字符序列排序在由迭代器范围 `[first1, last1)` 指定的字符序列之前，则 `[first2, last2)`。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__regex__regex_traits_transform.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_traits<char> Mytr;   
int main()   
    {   
    Mytr tr;   
  
    Mytr::char_type ch = tr.translate('a');   
    std::cout << "translate('a') == 'a' == " << std::boolalpha   
        << (ch == 'a') << std::endl;   
  
    std::cout << "nocase 'a' == 'A' == " << std::boolalpha   
        << (tr.translate_nocase('a') == tr.translate_nocase('A'))   
        << std::endl;   
  
    const char *lbegin = "abc";   
    const char *lend = lbegin + strlen(lbegin);   
    Mytr::size_type size = tr.length(lbegin);   
    std::cout << "length(\"abc\") == " << size <<std::endl;   
  
    Mytr::string_type str = tr.transform(lbegin, lend);   
    std::cout << "transform(\"abc\") < \"abc\" == " << std::boolalpha   
        << (str < "abc") << std::endl;   
  
    const char *ubegin = "ABC";   
    const char *uend = ubegin + strlen(ubegin);   
    std::cout << "primary \"ABC\" < \"abc\" == " << std::boolalpha   
        << (tr.transform_primary(ubegin, uend) <   
            tr.transform_primary(lbegin, lend))   
        << std::endl;   
  
    const char *dig = "digit";   
    Mytr::char_class_type cl = tr.lookup_classname(dig, dig + 5);   
    std::cout << "class digit == d == " << std::boolalpha   
        << (cl == tr.lookup_classname(dig, dig + 1))   
        << std::endl;   
  
    std::cout << "'3' is digit == " <<std::boolalpha   
        << tr.isctype('3', tr.lookup_classname(dig, dig + 5))   
        << std::endl;   
  
    std::cout << "hex C == " << tr.value('C', 16) << std::endl;   
  
// other members   
    str = tr.lookup_collatename(dig, dig + 5);   
  
    Mytr::locale_type loc = tr.getloc();   
    tr.imbue(loc);   
  
    return (0);   
    }  
  
```  
  
```Output  
translate('a') == 'a' == true  
nocase 'a' == 'A' == true  
length("abc") == 3  
transform("abc") < "abc" == false  
primary "ABC" < "abc" == false  
class digit == d == true  
'3' is digit == true  
hex C == 12  
```  
  
##  <a name="a-nameregextraitstransformprimarya--regextraitstransformprimary"></a><a name="regex_traits__transform_primary"></a>regex_traits::transform_primary  
 转换为不区分大小写的顺序等效序列。  
  
```  
template <class FwdIt>  
string_type transform_primary(FwdIt first, FwdIt last) const;
```  
  
### <a name="parameters"></a>参数  
 `first`  
 要转换的序列的开头。  
  
 `last`  
 要转换的序列的结尾。  
  
### <a name="remarks"></a>备注  
 此成员函数返回它使用转换规则生成的字符串，转换规则依赖于 `locale` 对象。 对于由迭代器范围 `[first1, last1)` 和 `[first2, last2)`指定的两个字符序列，如果由迭代器范围 `transform_primary(first1, last1) < transform_primary(first2, last2)` 指定的字符序列排序在由迭代器范围 `[first1, last1)` 指定的字符序列之前（不考虑大小写或重音字符），则 `[first2, last2)` 。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__regex__regex_traits_transform_primary.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_traits<char> Mytr;   
int main()   
    {   
    Mytr tr;   
  
    Mytr::char_type ch = tr.translate('a');   
    std::cout << "translate('a') == 'a' == " << std::boolalpha   
        << (ch == 'a') << std::endl;   
  
    std::cout << "nocase 'a' == 'A' == " << std::boolalpha   
        << (tr.translate_nocase('a') == tr.translate_nocase('A'))   
        << std::endl;   
  
    const char *lbegin = "abc";   
    const char *lend = lbegin + strlen(lbegin);   
    Mytr::size_type size = tr.length(lbegin);   
    std::cout << "length(\"abc\") == " << size <<std::endl;   
  
    Mytr::string_type str = tr.transform(lbegin, lend);   
    std::cout << "transform(\"abc\") < \"abc\" == " << std::boolalpha   
        << (str < "abc") << std::endl;   
  
    const char *ubegin = "ABC";   
    const char *uend = ubegin + strlen(ubegin);   
    std::cout << "primary \"ABC\" < \"abc\" == " << std::boolalpha   
        << (tr.transform_primary(ubegin, uend) <   
            tr.transform_primary(lbegin, lend))   
        << std::endl;   
  
    const char *dig = "digit";   
    Mytr::char_class_type cl = tr.lookup_classname(dig, dig + 5);   
    std::cout << "class digit == d == " << std::boolalpha   
        << (cl == tr.lookup_classname(dig, dig + 1))   
        << std::endl;   
  
    std::cout << "'3' is digit == " <<std::boolalpha   
        << tr.isctype('3', tr.lookup_classname(dig, dig + 5))   
        << std::endl;   
  
    std::cout << "hex C == " << tr.value('C', 16) << std::endl;   
  
// other members   
    str = tr.lookup_collatename(dig, dig + 5);   
  
    Mytr::locale_type loc = tr.getloc();   
    tr.imbue(loc);   
  
    return (0);   
    }  
  
```  
  
```Output  
translate('a') == 'a' == true  
nocase 'a' == 'A' == true  
length("abc") == 3  
transform("abc") < "abc" == false  
primary "ABC" < "abc" == false  
class digit == d == true  
'3' is digit == true  
hex C == 12  
```  
  
##  <a name="a-nameregextraitstranslatea--regextraitstranslate"></a><a name="regex_traits__translate"></a>regex_traits::translate  
 转换为等效的匹配元素。  
  
```  
char_type translate(char_type ch) const;
```  
  
### <a name="parameters"></a>参数  
 `ch`  
 要转换的元素。  
  
### <a name="remarks"></a>备注  
 此成员函数返回一个字符，它通过使用取决于存储的 `locale` 对象的转换规则而生成。 对于两个 `char_type` 对象（ `ch1` 和 `ch2`），只有 `translate(ch1) == translate(ch2)` 和 `ch1` 匹配（在其中一个在正则表达式定义中出现且另一个在区分区域设置匹配的目标序列中的相应位置出现时），才为 `ch2` 。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__regex__regex_traits_translate.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_traits<char> Mytr;   
int main()   
    {   
    Mytr tr;   
  
    Mytr::char_type ch = tr.translate('a');   
    std::cout << "translate('a') == 'a' == " << std::boolalpha   
        << (ch == 'a') << std::endl;   
  
    std::cout << "nocase 'a' == 'A' == " << std::boolalpha   
        << (tr.translate_nocase('a') == tr.translate_nocase('A'))   
        << std::endl;   
  
    const char *lbegin = "abc";   
    const char *lend = lbegin + strlen(lbegin);   
    Mytr::size_type size = tr.length(lbegin);   
    std::cout << "length(\"abc\") == " << size <<std::endl;   
  
    Mytr::string_type str = tr.transform(lbegin, lend);   
    std::cout << "transform(\"abc\") < \"abc\" == " << std::boolalpha   
        << (str < "abc") << std::endl;   
  
    const char *ubegin = "ABC";   
    const char *uend = ubegin + strlen(ubegin);   
    std::cout << "primary \"ABC\" < \"abc\" == " << std::boolalpha   
        << (tr.transform_primary(ubegin, uend) <   
            tr.transform_primary(lbegin, lend))   
        << std::endl;   
  
    const char *dig = "digit";   
    Mytr::char_class_type cl = tr.lookup_classname(dig, dig + 5);   
    std::cout << "class digit == d == " << std::boolalpha   
        << (cl == tr.lookup_classname(dig, dig + 1))   
        << std::endl;   
  
    std::cout << "'3' is digit == " <<std::boolalpha   
        << tr.isctype('3', tr.lookup_classname(dig, dig + 5))   
        << std::endl;   
  
    std::cout << "hex C == " << tr.value('C', 16) << std::endl;   
  
// other members   
    str = tr.lookup_collatename(dig, dig + 5);   
  
    Mytr::locale_type loc = tr.getloc();   
    tr.imbue(loc);   
  
    return (0);   
    }  
  
```  
  
```Output  
translate('a') == 'a' == true  
nocase 'a' == 'A' == true  
length("abc") == 3  
transform("abc") < "abc" == false  
primary "ABC" < "abc" == false  
class digit == d == true  
'3' is digit == true  
hex C == 12  
```  
  
##  <a name="a-nameregextraitstranslatenocasea--regextraitstranslatenocase"></a><a name="regex_traits__translate_nocase"></a>  regex_traits::translate_nocase  
 转换为不区分大小写的等效匹配序列。  
  
```  
char_type translate_nocase(char_type ch) const;
```  
  
### <a name="parameters"></a>参数  
 `ch`  
 要转换的元素。  
  
### <a name="remarks"></a>备注  
 此成员函数返回一个字符，它通过使用取决于存储的 `locale` 对象的转换规则而生成。 对于两个 `char_type` 对象（ `ch1` 和 `ch2`），只有当 `translate_nocase(ch1) == translate_nocase(ch2)` 和 `ch1` 的匹配条件为其中一个在正则表达式中出现且另一个在不区分大小写匹配的目标序列中的相应位置出现时，才为 `ch2` 。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__regex__regex_traits_translate_nocase.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_traits<char> Mytr;   
int main()   
    {   
    Mytr tr;   
  
    Mytr::char_type ch = tr.translate('a');   
    std::cout << "translate('a') == 'a' == " << std::boolalpha   
        << (ch == 'a') << std::endl;   
  
    std::cout << "nocase 'a' == 'A' == " << std::boolalpha   
        << (tr.translate_nocase('a') == tr.translate_nocase('A'))   
        << std::endl;   
  
    const char *lbegin = "abc";   
    const char *lend = lbegin + strlen(lbegin);   
    Mytr::size_type size = tr.length(lbegin);   
    std::cout << "length(\"abc\") == " << size <<std::endl;   
  
    Mytr::string_type str = tr.transform(lbegin, lend);   
    std::cout << "transform(\"abc\") < \"abc\" == " << std::boolalpha   
        << (str < "abc") << std::endl;   
  
    const char *ubegin = "ABC";   
    const char *uend = ubegin + strlen(ubegin);   
    std::cout << "primary \"ABC\" < \"abc\" == " << std::boolalpha   
        << (tr.transform_primary(ubegin, uend) <   
            tr.transform_primary(lbegin, lend))   
        << std::endl;   
  
    const char *dig = "digit";   
    Mytr::char_class_type cl = tr.lookup_classname(dig, dig + 5);   
    std::cout << "class digit == d == " << std::boolalpha   
        << (cl == tr.lookup_classname(dig, dig + 1))   
        << std::endl;   
  
    std::cout << "'3' is digit == " <<std::boolalpha   
        << tr.isctype('3', tr.lookup_classname(dig, dig + 5))   
        << std::endl;   
  
    std::cout << "hex C == " << tr.value('C', 16) << std::endl;   
  
// other members   
    str = tr.lookup_collatename(dig, dig + 5);   
  
    Mytr::locale_type loc = tr.getloc();   
    tr.imbue(loc);   
  
    return (0);   
    }  
  
```  
  
```Output  
translate('a') == 'a' == true  
nocase 'a' == 'A' == true  
length("abc") == 3  
transform("abc") < "abc" == false  
primary "ABC" < "abc" == false  
class digit == d == true  
'3' is digit == true  
hex C == 12  
```  
  
##  <a name="a-nameregextraitsvaluea--regextraitsvalue"></a><a name="regex_traits__value"></a>  regex_traits::value  
 将元素转换为数字值。  
  
```  
int value(Elem ch, int radix) const;
```  
  
### <a name="parameters"></a>参数  
 `ch`  
 要转换的元素。  
  
 `radix`  
 要使用的算术基数。  
  
### <a name="remarks"></a>备注  
 该成员函数将返回由基数 `ch` 中字符 `radix`表示的值，或者如果 `ch` 不是基数 `radix`中的有效数字，则返回 -1。 只有使用 `radix` 参数 8、10 或 16 才能调用该函数。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__regex__regex_traits_value.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_traits<char> Mytr;   
int main()   
    {   
    Mytr tr;   
  
    Mytr::char_type ch = tr.translate('a');   
    std::cout << "translate('a') == 'a' == " << std::boolalpha   
        << (ch == 'a') << std::endl;   
  
    std::cout << "nocase 'a' == 'A' == " << std::boolalpha   
        << (tr.translate_nocase('a') == tr.translate_nocase('A'))   
        << std::endl;   
  
    const char *lbegin = "abc";   
    const char *lend = lbegin + strlen(lbegin);   
    Mytr::size_type size = tr.length(lbegin);   
    std::cout << "length(\"abc\") == " << size <<std::endl;   
  
    Mytr::string_type str = tr.transform(lbegin, lend);   
    std::cout << "transform(\"abc\") < \"abc\" == " << std::boolalpha   
        << (str < "abc") << std::endl;   
  
    const char *ubegin = "ABC";   
    const char *uend = ubegin + strlen(ubegin);   
    std::cout << "primary \"ABC\" < \"abc\" == " << std::boolalpha   
        << (tr.transform_primary(ubegin, uend) <   
            tr.transform_primary(lbegin, lend))   
        << std::endl;   
  
    const char *dig = "digit";   
    Mytr::char_class_type cl = tr.lookup_classname(dig, dig + 5);   
    std::cout << "class digit == d == " << std::boolalpha   
        << (cl == tr.lookup_classname(dig, dig + 1))   
        << std::endl;   
  
    std::cout << "'3' is digit == " <<std::boolalpha   
        << tr.isctype('3', tr.lookup_classname(dig, dig + 5))   
        << std::endl;   
  
    std::cout << "hex C == " << tr.value('C', 16) << std::endl;   
  
// other members   
    str = tr.lookup_collatename(dig, dig + 5);   
  
    Mytr::locale_type loc = tr.getloc();   
    tr.imbue(loc);   
  
    return (0);   
    }  
  
```  
  
```Output  
translate('a') == 'a' == true  
nocase 'a' == 'A' == true  
length("abc") == 3  
transform("abc") < "abc" == false  
primary "ABC" < "abc" == false  
class digit == d == true  
'3' is digit == true  
hex C == 12  
```  
  
## <a name="see-also"></a>另请参阅  
[\<regex>](../standard-library/regex.md)  
[regex_constants 类](../standard-library/regex-constants-class.md)  
[regex_error 类](../standard-library/regex-error-class.md)  
[\<regex> functions](../standard-library/regex-functions.md)  
[regex_iterator 类](../standard-library/regex-iterator-class.md)  
[\<regex> operators](../standard-library/regex-operators.md)  
[regex_token_iterator 类](../standard-library/regex-token-iterator-class.md)  
[\<regex> typedefs](../standard-library/regex-typedefs.md)  
 [regex_traits\<char> Class](../standard-library/regex-traits-char-class.md)   
 [regex_traits\<wchar_t> Class](../standard-library/regex-traits-wchar-t-class.md)



---
title: "basic_regex 类 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: regex/std::basic_regex
dev_langs: C++
helpviewer_keywords: basic_regex class
ms.assetid: 8a18c6b4-f22a-4cfd-bc16-b4267867ebc3
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 59ead4cce14828c2b416f3d4770f90db61e7d659
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="basicregex-class"></a>basic_regex 类
包装正则表达式。  
  
## <a name="syntax"></a>语法  
  
```  
class basic_regex {  
   public:  
   basic_regex();
   explicit basic_regex(const Elem *ptr,  
   flag_type flags = ECMAScript);
   basic_regex(const Elem *ptr, size_type len,  
   flag_type flags = ECMAScript);
   basic_regex(const basic_regex& right);
   template <class STtraits, class STalloc>  
   explicit basic_regex(const basic_string<Elem, STtraits, STalloc>& str,  
   flag_type flags = ECMAScript);
   template <class InIt>  
   explicit basic_regex(InIt first, InIt last,  
   flag_type flags = ECMAScript);
   basic_regex& operator=(const basic_regex& right);
   basic_regex& operator=(const Elem *ptr);
   template <class STtraits, class STalloc>  
   basic_regex& operator=(const basic_string<Elem, STtraits, STalloc>& str);
   basic_regex& assign(const basic_regex& right);
   basic_regex& assign(const Elem *ptr,  
   flag_type flags = ECMAScript);
   basic_regex& assign(const Elem *ptr, size_type len,  
   flag_type flags = ECMAScript);
   template <class STtraits, class STalloc>  
   basic_regex& assign(const basic_string<Elem, STtraits, STalloc>& str,  
   flag_type flags = ECMAScript);
   template <class InIt>  
   basic_regex& assign(InIt first, InIt last,  
   flag_type flags = ECMAScript);
   locale_type imbue(locale_type loc);
   locale_type getloc() const;
   void swap(basic_regex& other) throw();
   unsigned mark_count() const;
   flag_type flags() const;
   typedef Elem value_type;  
   typedef regex_constants::syntax_option_type flag_type;  
   typedef typename RXtraits::locale_type locale_type;  
   static const flag_type icase = regex_constants::icase;  
   static const flag_type nosubs = regex_constants::nosubs;  
   static const flag_type optimize = regex_constants::optimize;  
   static const flag_type collate = regex_constants::collate;  
   static const flag_type ECMAScript = regex_constants::ECMAScript;  
   static const flag_type basic = regex_constants::basic;  
   static const flag_type extended = regex_constants::extended;  
   static const flag_type awk = regex_constants::awk;  
   static const flag_type grep = regex_constants::grep;  
   static const flag_type egrep = regex_constants::egrep;  
   private:  
   RXtraits traits;    // exposition only  
   };  
   ```   
  
#### <a name="parameters"></a>参数  
 `Elem`  
 要匹配的元素的类型。  
  
 `RXtraits`  
 元素的特征类。  
  
## <a name="remarks"></a>备注  
 此模板类描述包含正则表达式的对象。 此模板类的对象可以传递给模板函数[regex_match](../standard-library/regex-functions.md#regex_match)， [regex_search](../standard-library/regex-functions.md#regex_search)，和[regex_replace](../standard-library/regex-functions.md#regex_replace)，适合的文本字符串自变量，以及若要搜索匹配正则表达式的文本。 此模板类有两种专用定义，包括针对 `char` 类型元素的类型定义 [regex](../standard-library/regex-typedefs.md#regex)，以及针对 `wchar_t` 类型元素的类型定义 [wregex](../standard-library/regex-typedefs.md#wregex)。  
  
 模板参数 `RXtraits` 描述模板类支持的正则表达式语法的各个重要属性。 一个指定这些正则表达式特征的外部接口必须与模板类 [regex_traits Class](../standard-library/regex-traits-class.md) 的对象相同的类。  
  
 某些函数使用操作数序列来定义正则表达式。 可以通过多种方式指定此操作数序列：  
  
 `ptr` - 从 `Elem`（不能为 null 指针）开始、以 null 结尾的序列（例如 C 字符串，`char` 类型的 `ptr`），其中结尾元素为值 `value_type()`，且不是操作数序列的一部分  
  
 `ptr`, `count` - 从 `count`（不能为 null 指针）开始的 `ptr` 元素序列  
  
 `str` - `basic_string` 对象 `str` 指定的序列  
  
 `first`, `last` - 迭代器 `first` 和 `last` 在范围 `[first, last)` 中分隔的元素序列  
  
 `right` - `basic_regex` 对象 `right`  
  
 这些成员函数还使用参数 `flags` 指定用于解释正则表达式的各个选项以及 `RXtraits` 类型描述的选项。  
  
## <a name="requirements"></a>要求  
 **标头：**\<regex 1>  
  
 **命名空间：** std  
  
##  <a name="assign"></a>  basic_regex::assign  
 将一个值分配到正则表达式对象。  
  
```  
basic_regex& assign(
    const basic_regex& right);

basic_regex& assign(
    const Elem* ptr,  
    flag_type flags = ECMAScript);

basic_regex& assign(
    const Elem* ptr,   
    size_type len,  
    flag_type flags = ECMAScript);

basic_regex& assign(
    initializer_list<_Elem> IList,  
    flag_type flags = regex_constants::ECMAScript);

template <class STtraits, class STalloc>  
basic_regex& assign(
    const basic_string<Elem, STtraits, STalloc>& str,  
    flag_type flags = ECMAScript);

template <class InIt>  
basic_regex& assign(
    InIt first, InIt last,  
    flag_type flags = ECMAScript);
```  
  
### <a name="parameters"></a>参数  
 `STtraits`  
 字符串源的特征类。  
  
 `STalloc`  
 字符串源的分配器类。  
  
 `InIt`  
 范围源的输入迭代器类型。  
  
 `right`  
 要复制的正则表达式源。  
  
 `ptr`  
 指向要复制的序列开头的指针。  
  
 `flags`  
 复制时要添加的语法选项标志。  
  
 `len/TD>`  
 要复制的序列的长度。  
  
 `str`  
 要复制的字符串。  
  
 `first`  
 要复制的序列的开头。  
  
 `last`  
 要复制的序列的结尾。  
  
 `IList`  
 要复制的 initializer_list。  
  
### <a name="remarks"></a>备注  
 每个成员函数将 `*this` 保留的正则表达式替换为操作数序列所描述的正则表达式，然后返回 `*this`。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__regex__basic_regex_assign.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
using namespace std;  
  
int main()  
{  
    regex::value_type elem = 'x';  
    regex::flag_type flag = regex::grep;  
  
    elem = elem;  // to quiet "unused" warnings   
    flag = flag;  
  
    // constructors   
    regex rx0;  
    cout << "match(\"abc\", \"\") == " << boolalpha  
        << regex_match("abc", rx0) << endl;  
  
    regex rx1("abcd", regex::ECMAScript);  
    cout << "match(\"abc\", \"abcd\") == " << boolalpha  
        << regex_match("abc", rx1) << endl;  
  
    regex rx2("abcd", 3);  
    cout << "match(\"abc\", \"abc\") == " << boolalpha  
        << regex_match("abc", rx2) << endl;  
  
    regex rx3(rx2);  
    cout << "match(\"abc\", \"abc\") == " << boolalpha  
        << regex_match("abc", rx3) << endl;  
  
    string str("abcd");  
    regex rx4(str);  
    cout << "match(string(\"abcd\"), \"abc\") == " << boolalpha  
        << regex_match("abc", rx4) << endl;  
  
    regex rx5(str.begin(), str.end() - 1);  
    cout << "match(string(\"abc\"), \"abc\") == " << boolalpha  
        << regex_match("abc", rx5) << endl;  
    cout << endl;  
  
    // assignments   
    rx0 = "abc";  
    rx0 = rx1;  
    rx0 = str;  
  
    rx0.assign("abcd", regex::ECMAScript);  
    rx0.assign("abcd", 3);  
    rx0.assign(rx1);  
    rx0.assign(str);  
    rx0.assign(str.begin(), str.end() - 1);  
  
    rx0.swap(rx1);  
  
    // mark_count   
    cout << "\"abc\" mark_count == "  
        << regex("abc").mark_count() << endl;  
    cout << "\"(abc)\" mark_count == "  
        << regex("(abc)").mark_count() << endl;  
  
    // locales   
    regex::locale_type loc = rx0.imbue(locale());  
    cout << "getloc == imbued == " << boolalpha  
        << (loc == rx0.getloc()) << endl;  
  
    // initializer_list  
    regex rx6({ 'a', 'b', 'c' }, regex::ECMAScript);  
    cout << "match(\"abc\") == " << boolalpha  
        << regex_match("abc", rx6);  
    cout << endl;   
}  
  
```  
  
```Output  
match("abc", "") == falsematch("abc", "abcd") == falsematch("abc", "abc") == truematch("abc", "abc") == truematch(string("abcd"), "abc") == falsematch(string("abc"), "abc") == true"abc" mark_count == 0"(abc)" mark_count == 1getloc == imbued == truematch("abc") == true  
```  
  
##  <a name="basic_regex"></a>  basic_regex::basic_regex  
 构造正则表达式对象。  
  
```  
basic_regex();

explicit basic_regex(
    const Elem* ptr,  
    flag_type flags);

explicit basic_regex(
    const Elem* ptr,   
    size_type len,  
    flag_type flags);

basic_regex(
    const basic_regex& right);

basic_regex(
    initializer_list<Type> IList,  
    flag_type flags);

template <class STtraits, class STalloc>  
explicit basic_regex(
    const basic_string<Elem, STtraits, STalloc>& str,  
    flag_type flags);

template <class InIt>  
explicit basic_regex(
    InIt first,   
    InIt last,  
    flag_type flags);
```  
  
### <a name="parameters"></a>参数  
 `STtraits`  
 字符串源的特征类。  
  
 `STalloc`  
 字符串源的分配器类。  
  
 `InIt`  
 范围源的输入迭代器类型。  
  
 `right`  
 要复制的正则表达式源。  
  
 `ptr`  
 指向要复制的序列开头的指针。  
  
 `flags`  
 复制时要添加的语法选项标志。  
  
 `len/TD>`  
 要复制的序列的长度。  
  
 `str`  
 要复制的字符串。  
  
 `first`  
 要复制的序列的开头。  
  
 `last`  
 要复制的序列的结尾。  
  
 `IList`  
 要复制的 initializer_list。  
  
### <a name="remarks"></a>备注  
 所有构造函数将存储类型 `RXtraits` 的默认构造对象。  
  
 第一个构造函数构造一个空 `basic_regex` 对象。 其他构造函数构造 `basic_regex` 对象，其中包含由操作数序列描述的正则表达式。  
  
 一个空`basic_regex`对象不匹配任何字符序列时传递给[regex_match](../standard-library/regex-functions.md#regex_match)， [regex_search](../standard-library/regex-functions.md#regex_search)，或[regex_replace](../standard-library/regex-functions.md#regex_replace)。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__regex__basic_regex_construct.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
using namespace std;  
  
int main()  
{  
    regex::value_type elem = 'x';  
    regex::flag_type flag = regex::grep;  
  
    elem = elem;  // to quiet "unused" warnings   
    flag = flag;  
  
    // constructors   
    regex rx0;  
    cout << "match(\"abc\", \"\") == " << boolalpha  
        << regex_match("abc", rx0) << endl;  
  
    regex rx1("abcd", regex::ECMAScript);  
    cout << "match(\"abc\", \"abcd\") == " << boolalpha  
        << regex_match("abc", rx1) << endl;  
  
    regex rx2("abcd", 3);  
    cout << "match(\"abc\", \"abc\") == " << boolalpha  
        << regex_match("abc", rx2) << endl;  
  
    regex rx3(rx2);  
    cout << "match(\"abc\", \"abc\") == " << boolalpha  
        << regex_match("abc", rx3) << endl;  
  
    string str("abcd");  
    regex rx4(str);  
    cout << "match(string(\"abcd\"), \"abc\") == " << boolalpha  
        << regex_match("abc", rx4) << endl;  
  
    regex rx5(str.begin(), str.end() - 1);  
    cout << "match(string(\"abc\"), \"abc\") == " << boolalpha  
        << regex_match("abc", rx5) << endl;  
    cout << endl;  
  
    // assignments   
    rx0 = "abc";  
    rx0 = rx1;  
    rx0 = str;  
  
    rx0.assign("abcd", regex::ECMAScript);  
    rx0.assign("abcd", 3);  
    rx0.assign(rx1);  
    rx0.assign(str);  
    rx0.assign(str.begin(), str.end() - 1);  
  
    rx0.swap(rx1);  
  
    // mark_count   
    cout << "\"abc\" mark_count == "  
        << regex("abc").mark_count() << endl;  
    cout << "\"(abc)\" mark_count == "  
        << regex("(abc)").mark_count() << endl;  
  
    // locales   
    regex::locale_type loc = rx0.imbue(locale());  
    cout << "getloc == imbued == " << boolalpha  
        << (loc == rx0.getloc()) << endl;  
  
    // initializer_list  
    regex rx6{ { 'a', 'b', 'c' } };  
    cout << "match(\"abc\", \"abc\") == " << boolalpha  
        << regex_match("abc", rx6);  
    cout << endl;  
}  
  
```  
  
```Output  
match("abc", "") == falsematch("abc", "abcd") == falsematch("abc", "abc") == truematch("abc", "abc") == truematch(string("abcd"), "abc") == falsematch(string("abc"), "abc") == true"abc" mark_count == 0"(abc)" mark_count == 1getloc == imbued == truematch("abc", "abc") == true  
```  
  
##  <a name="flag_type"></a>  basic_regex::flag_type  
 语法选项标志的类型。  
  
```  
typedef regex_constants::syntax_option_type flag_type;  
```  
  
### <a name="remarks"></a>备注  
 该类型是 [regex_constants::syntax_option_type](../standard-library/regex-constants-class.md#syntax_option_type) 的同义词。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__regex__basic_regex_flag_type.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex::value_type elem = 'x';   
    std::regex::flag_type flag = std::regex::grep;   
  
    elem = elem;  // to quiet "unused" warnings   
    flag = flag;   
  
// constructors   
    std::regex rx0;   
    std::cout << "match(\"abc\", \"\") == " << std::boolalpha   
        << regex_match("abc", rx0) << std::endl;   
  
    std::regex rx1("abcd", std::regex::ECMAScript);   
    std::cout << "match(\"abc\", \"abcd\") == " << std::boolalpha   
        << regex_match("abc", rx1) << std::endl;   
  
    std::regex rx2("abcd", 3);   
    std::cout << "match(\"abc\", \"abc\") == " << std::boolalpha   
        << regex_match("abc", rx2) << std::endl;   
  
    std::regex rx3(rx2);   
    std::cout << "match(\"abc\", \"abc\") == " << std::boolalpha   
        << regex_match("abc", rx3) << std::endl;   
  
    std::string str("abcd");   
    std::regex rx4(str);   
    std::cout << "match(string(\"abcd\"), \"abc\") == " << std::boolalpha   
        << regex_match("abc", rx4) << std::endl;   
  
    std::regex rx5(str.begin(), str.end() - 1);   
    std::cout << "match(string(\"abc\"), \"abc\") == " << std::boolalpha   
        << regex_match("abc", rx5) << std::endl;   
    std::cout << std::endl;   
  
// assignments   
    rx0 = "abc";   
    rx0 = rx1;   
    rx0 = str;   
  
    rx0.assign("abcd", std::regex::ECMAScript);   
    rx0.assign("abcd", 3);   
    rx0.assign(rx1);   
    rx0.assign(str);   
    rx0.assign(str.begin(), str.end() - 1);   
  
    rx0.swap(rx1);   
  
// mark_count   
    std::cout << "\"abc\" mark_count == "   
        << std::regex("abc").mark_count() << std::endl;   
    std::cout << "\"(abc)\" mark_count == "   
        << std::regex("(abc)").mark_count() << std::endl;   
  
// locales   
    std::regex::locale_type loc = rx0.imbue(std::locale());   
    std::cout << "getloc == imbued == " << std::boolalpha   
        << (loc == rx0.getloc()) << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
match("abc", "") == false  
match("abc", "abcd") == false  
match("abc", "abc") == true  
match("abc", "abc") == true  
match(string("abcd"), "abc") == false  
match(string("abc"), "abc") == true  
  
"abc" mark_count == 0  
"(abc)" mark_count == 1  
getloc == imbued == true  
```  
  
##  <a name="flags"></a>  basic_regex::flags  
 返回语法选项标志。  
  
```  
flag_type flags() const;
```  
  
### <a name="remarks"></a>备注  
 成员函数返回 `flag_type` 自变量的值，该值传递到对一个 [basic_regex::assign](#assign) 成员函数的最近调用，或者如果没有实施这类调用，则返回传递到构造函数的值。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__regex__basic_regex_flags.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex::value_type elem = 'x';   
    std::regex::flag_type flag = std::regex::grep;   
  
    elem = elem;  // to quiet "unused" warnings   
    flag = flag;   
  
// constructors   
    std::regex rx0;   
    std::cout << "match(\"abc\", \"\") == " << std::boolalpha   
        << regex_match("abc", rx0) << std::endl;   
  
    std::regex rx1("abcd", std::regex::ECMAScript);   
    std::cout << "match(\"abc\", \"abcd\") == " << std::boolalpha   
        << regex_match("abc", rx1) << std::endl;   
  
    std::regex rx2("abcd", 3);   
    std::cout << "match(\"abc\", \"abc\") == " << std::boolalpha   
        << regex_match("abc", rx2) << std::endl;   
  
    std::regex rx3(rx2);   
    std::cout << "match(\"abc\", \"abc\") == " << std::boolalpha   
        << regex_match("abc", rx3) << std::endl;   
  
    std::string str("abcd");   
    std::regex rx4(str);   
    std::cout << "match(string(\"abcd\"), \"abc\") == " << std::boolalpha   
        << regex_match("abc", rx4) << std::endl;   
  
    std::regex rx5(str.begin(), str.end() - 1);   
    std::cout << "match(string(\"abc\"), \"abc\") == " << std::boolalpha   
        << regex_match("abc", rx5) << std::endl;   
    std::cout << std::endl;   
  
// assignments   
    rx0 = "abc";   
    rx0 = rx1;   
    rx0 = str;   
  
    rx0.assign("abcd", std::regex::ECMAScript);   
    rx0.assign("abcd", 3);   
    rx0.assign(rx1);   
    rx0.assign(str);   
    rx0.assign(str.begin(), str.end() - 1);   
  
    rx0.swap(rx1);   
  
// mark_count   
    std::cout << "\"abc\" mark_count == "   
        << std::regex("abc").mark_count() << std::endl;   
    std::cout << "\"(abc)\" mark_count == "   
        << std::regex("(abc)").mark_count() << std::endl;   
  
// locales   
    std::regex::locale_type loc = rx0.imbue(std::locale());   
    std::cout << "getloc == imbued == " << std::boolalpha   
        << (loc == rx0.getloc()) << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
match("abc", "") == false  
match("abc", "abcd") == false  
match("abc", "abc") == true  
match("abc", "abc") == true  
match(string("abcd"), "abc") == false  
match(string("abc"), "abc") == true  
  
"abc" mark_count == 0  
"(abc)" mark_count == 1  
getloc == imbued == true  
```  
  
##  <a name="getloc"></a>  basic_regex::getloc  
 返回存储的区域设置对象。  
  
```  
locale_type getloc() const;
```  
  
### <a name="remarks"></a>备注  
 成员函数将返回 `traits.`[regex_traits::getloc](../standard-library/regex-traits-class.md#getloc)`()`。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__regex__basic_regex_getloc.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex::value_type elem = 'x';   
    std::regex::flag_type flag = std::regex::grep;   
  
    elem = elem;  // to quiet "unused" warnings   
    flag = flag;   
  
// constructors   
    std::regex rx0;   
    std::cout << "match(\"abc\", \"\") == " << std::boolalpha   
        << regex_match("abc", rx0) << std::endl;   
  
    std::regex rx1("abcd", std::regex::ECMAScript);   
    std::cout << "match(\"abc\", \"abcd\") == " << std::boolalpha   
        << regex_match("abc", rx1) << std::endl;   
  
    std::regex rx2("abcd", 3);   
    std::cout << "match(\"abc\", \"abc\") == " << std::boolalpha   
        << regex_match("abc", rx2) << std::endl;   
  
    std::regex rx3(rx2);   
    std::cout << "match(\"abc\", \"abc\") == " << std::boolalpha   
        << regex_match("abc", rx3) << std::endl;   
  
    std::string str("abcd");   
    std::regex rx4(str);   
    std::cout << "match(string(\"abcd\"), \"abc\") == " << std::boolalpha   
        << regex_match("abc", rx4) << std::endl;   
  
    std::regex rx5(str.begin(), str.end() - 1);   
    std::cout << "match(string(\"abc\"), \"abc\") == " << std::boolalpha   
        << regex_match("abc", rx5) << std::endl;   
    std::cout << std::endl;   
  
// assignments   
    rx0 = "abc";   
    rx0 = rx1;   
    rx0 = str;   
  
    rx0.assign("abcd", std::regex::ECMAScript);   
    rx0.assign("abcd", 3);   
    rx0.assign(rx1);   
    rx0.assign(str);   
    rx0.assign(str.begin(), str.end() - 1);   
  
    rx0.swap(rx1);   
  
// mark_count   
    std::cout << "\"abc\" mark_count == "   
        << std::regex("abc").mark_count() << std::endl;   
    std::cout << "\"(abc)\" mark_count == "   
        << std::regex("(abc)").mark_count() << std::endl;   
  
// locales   
    std::regex::locale_type loc = rx0.imbue(std::locale());   
    std::cout << "getloc == imbued == " << std::boolalpha   
        << (loc == rx0.getloc()) << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
match("abc", "") == false  
match("abc", "abcd") == false  
match("abc", "abc") == true  
match("abc", "abc") == true  
match(string("abcd"), "abc") == false  
match(string("abc"), "abc") == true  
  
"abc" mark_count == 0  
"(abc)" mark_count == 1  
getloc == imbued == true  
```  
  
##  <a name="imbue"></a>  basic_regex::imbue  
 更改存储的区域设置对象。  
  
```  
locale_type imbue(locale_type loc);
```  
  
### <a name="parameters"></a>参数  
 `loc`  
 要存储的区域设置对象。  
  
### <a name="remarks"></a>备注  
 该成员函数将清空 `*this` 并返回 `traits.`[regex_traits::imbue](../standard-library/regex-traits-class.md#imbue)`(loc)`。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__regex__basic_regex_imbue.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex::value_type elem = 'x';   
    std::regex::flag_type flag = std::regex::grep;   
  
    elem = elem;  // to quiet "unused" warnings   
    flag = flag;   
  
// constructors   
    std::regex rx0;   
    std::cout << "match(\"abc\", \"\") == " << std::boolalpha   
        << regex_match("abc", rx0) << std::endl;   
  
    std::regex rx1("abcd", std::regex::ECMAScript);   
    std::cout << "match(\"abc\", \"abcd\") == " << std::boolalpha   
        << regex_match("abc", rx1) << std::endl;   
  
    std::regex rx2("abcd", 3);   
    std::cout << "match(\"abc\", \"abc\") == " << std::boolalpha   
        << regex_match("abc", rx2) << std::endl;   
  
    std::regex rx3(rx2);   
    std::cout << "match(\"abc\", \"abc\") == " << std::boolalpha   
        << regex_match("abc", rx3) << std::endl;   
  
    std::string str("abcd");   
    std::regex rx4(str);   
    std::cout << "match(string(\"abcd\"), \"abc\") == " << std::boolalpha   
        << regex_match("abc", rx4) << std::endl;   
  
    std::regex rx5(str.begin(), str.end() - 1);   
    std::cout << "match(string(\"abc\"), \"abc\") == " << std::boolalpha   
        << regex_match("abc", rx5) << std::endl;   
    std::cout << std::endl;   
  
// assignments   
    rx0 = "abc";   
    rx0 = rx1;   
    rx0 = str;   
  
    rx0.assign("abcd", std::regex::ECMAScript);   
    rx0.assign("abcd", 3);   
    rx0.assign(rx1);   
    rx0.assign(str);   
    rx0.assign(str.begin(), str.end() - 1);   
  
    rx0.swap(rx1);   
  
// mark_count   
    std::cout << "\"abc\" mark_count == "   
        << std::regex("abc").mark_count() << std::endl;   
    std::cout << "\"(abc)\" mark_count == "   
        << std::regex("(abc)").mark_count() << std::endl;   
  
// locales   
    std::regex::locale_type loc = rx0.imbue(std::locale());   
    std::cout << "getloc == imbued == " << std::boolalpha   
        << (loc == rx0.getloc()) << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
match("abc", "") == false  
match("abc", "abcd") == false  
match("abc", "abc") == true  
match("abc", "abc") == true  
match(string("abcd"), "abc") == false  
match(string("abc"), "abc") == true  
  
"abc" mark_count == 0  
"(abc)" mark_count == 1  
getloc == imbued == true  
```  
  
##  <a name="locale_type"></a>  basic_regex::locale_type  
 存储的区域设置对象的类型。  
  
```  
typedef typename RXtraits::locale_type locale_type;  
```  
  
### <a name="remarks"></a>备注  
 该类型是 [regex_traits::locale_type](../standard-library/regex-traits-class.md#locale_type) 的同义词。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__regex__basic_regex_locale_type.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex::value_type elem = 'x';   
    std::regex::flag_type flag = std::regex::grep;   
  
    elem = elem;  // to quiet "unused" warnings   
    flag = flag;   
  
// constructors   
    std::regex rx0;   
    std::cout << "match(\"abc\", \"\") == " << std::boolalpha   
        << regex_match("abc", rx0) << std::endl;   
  
    std::regex rx1("abcd", std::regex::ECMAScript);   
    std::cout << "match(\"abc\", \"abcd\") == " << std::boolalpha   
        << regex_match("abc", rx1) << std::endl;   
  
    std::regex rx2("abcd", 3);   
    std::cout << "match(\"abc\", \"abc\") == " << std::boolalpha   
        << regex_match("abc", rx2) << std::endl;   
  
    std::regex rx3(rx2);   
    std::cout << "match(\"abc\", \"abc\") == " << std::boolalpha   
        << regex_match("abc", rx3) << std::endl;   
  
    std::string str("abcd");   
    std::regex rx4(str);   
    std::cout << "match(string(\"abcd\"), \"abc\") == " << std::boolalpha   
        << regex_match("abc", rx4) << std::endl;   
  
    std::regex rx5(str.begin(), str.end() - 1);   
    std::cout << "match(string(\"abc\"), \"abc\") == " << std::boolalpha   
        << regex_match("abc", rx5) << std::endl;   
    std::cout << std::endl;   
  
// assignments   
    rx0 = "abc";   
    rx0 = rx1;   
    rx0 = str;   
  
    rx0.assign("abcd", std::regex::ECMAScript);   
    rx0.assign("abcd", 3);   
    rx0.assign(rx1);   
    rx0.assign(str);   
    rx0.assign(str.begin(), str.end() - 1);   
  
    rx0.swap(rx1);   
  
// mark_count   
    std::cout << "\"abc\" mark_count == "   
        << std::regex("abc").mark_count() << std::endl;   
    std::cout << "\"(abc)\" mark_count == "   
        << std::regex("(abc)").mark_count() << std::endl;   
  
// locales   
    std::regex::locale_type loc = rx0.imbue(std::locale());   
    std::cout << "getloc == imbued == " << std::boolalpha   
        << (loc == rx0.getloc()) << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
match("abc", "") == false  
match("abc", "abcd") == false  
match("abc", "abc") == true  
match("abc", "abc") == true  
match(string("abcd"), "abc") == false  
match(string("abc"), "abc") == true  
  
"abc" mark_count == 0  
"(abc)" mark_count == 1  
getloc == imbued == true  
```  
  
##  <a name="mark_count"></a>  basic_regex::mark_count  
 返回匹配的子表达式的数目。  
  
```  
unsigned mark_count() const;
```  
  
### <a name="remarks"></a>备注  
 成员函数将返回正则表达式中的捕获组数量。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__regex__basic_regex_mark_count.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex::value_type elem = 'x';   
    std::regex::flag_type flag = std::regex::grep;   
  
    elem = elem;  // to quiet "unused" warnings   
    flag = flag;   
  
// constructors   
    std::regex rx0;   
    std::cout << "match(\"abc\", \"\") == " << std::boolalpha   
        << regex_match("abc", rx0) << std::endl;   
  
    std::regex rx1("abcd", std::regex::ECMAScript);   
    std::cout << "match(\"abc\", \"abcd\") == " << std::boolalpha   
        << regex_match("abc", rx1) << std::endl;   
  
    std::regex rx2("abcd", 3);   
    std::cout << "match(\"abc\", \"abc\") == " << std::boolalpha   
        << regex_match("abc", rx2) << std::endl;   
  
    std::regex rx3(rx2);   
    std::cout << "match(\"abc\", \"abc\") == " << std::boolalpha   
        << regex_match("abc", rx3) << std::endl;   
  
    std::string str("abcd");   
    std::regex rx4(str);   
    std::cout << "match(string(\"abcd\"), \"abc\") == " << std::boolalpha   
        << regex_match("abc", rx4) << std::endl;   
  
    std::regex rx5(str.begin(), str.end() - 1);   
    std::cout << "match(string(\"abc\"), \"abc\") == " << std::boolalpha   
        << regex_match("abc", rx5) << std::endl;   
    std::cout << std::endl;   
  
// assignments   
    rx0 = "abc";   
    rx0 = rx1;   
    rx0 = str;   
  
    rx0.assign("abcd", std::regex::ECMAScript);   
    rx0.assign("abcd", 3);   
    rx0.assign(rx1);   
    rx0.assign(str);   
    rx0.assign(str.begin(), str.end() - 1);   
  
    rx0.swap(rx1);   
  
// mark_count   
    std::cout << "\"abc\" mark_count == "   
        << std::regex("abc").mark_count() << std::endl;   
    std::cout << "\"(abc)\" mark_count == "   
        << std::regex("(abc)").mark_count() << std::endl;   
  
// locales   
    std::regex::locale_type loc = rx0.imbue(std::locale());   
    std::cout << "getloc == imbued == " << std::boolalpha   
        << (loc == rx0.getloc()) << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
match("abc", "") == false  
match("abc", "abcd") == false  
match("abc", "abc") == true  
match("abc", "abc") == true  
match(string("abcd"), "abc") == false  
match(string("abc"), "abc") == true  
  
"abc" mark_count == 0  
"(abc)" mark_count == 1  
getloc == imbued == true  
```  
  
##  <a name="op_eq"></a>  basic_regex::operator=  
 将一个值分配到正则表达式对象。  
  
```  
basic_regex& operator=(const basic_regex& right);

basic_regex& operator=(const Elem *str);

template <class STtraits, class STalloc>  
basic_regex& operator=(const basic_string<Elem, STtraits, STalloc>& str);
```  
  
### <a name="parameters"></a>参数  
 `STtraits`  
 字符串源的特征类。  
  
 `STalloc`  
 字符串源的分配器类。  
  
 `right`  
 要复制的正则表达式源。  
  
 `str`  
 要复制的字符串。  
  
### <a name="remarks"></a>备注  
 每个运算符将 `*this` 保留的正则表达式替换为操作数序列所描述的正则表达式，然后返回 `*this`。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__regex__basic_regex_operator_as.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex::value_type elem = 'x';   
    std::regex::flag_type flag = std::regex::grep;   
  
    elem = elem;  // to quiet "unused" warnings   
    flag = flag;   
  
// constructors   
    std::regex rx0;   
    std::cout << "match(\"abc\", \"\") == " << std::boolalpha   
        << regex_match("abc", rx0) << std::endl;   
  
    std::regex rx1("abcd", std::regex::ECMAScript);   
    std::cout << "match(\"abc\", \"abcd\") == " << std::boolalpha   
        << regex_match("abc", rx1) << std::endl;   
  
    std::regex rx2("abcd", 3);   
    std::cout << "match(\"abc\", \"abc\") == " << std::boolalpha   
        << regex_match("abc", rx2) << std::endl;   
  
    std::regex rx3(rx2);   
    std::cout << "match(\"abc\", \"abc\") == " << std::boolalpha   
        << regex_match("abc", rx3) << std::endl;   
  
    std::string str("abcd");   
    std::regex rx4(str);   
    std::cout << "match(string(\"abcd\"), \"abc\") == " << std::boolalpha   
        << regex_match("abc", rx4) << std::endl;   
  
    std::regex rx5(str.begin(), str.end() - 1);   
    std::cout << "match(string(\"abc\"), \"abc\") == " << std::boolalpha   
        << regex_match("abc", rx5) << std::endl;   
    std::cout << std::endl;   
  
// assignments   
    rx0 = "abc";   
    rx0 = rx1;   
    rx0 = str;   
  
    rx0.assign("abcd", std::regex::ECMAScript);   
    rx0.assign("abcd", 3);   
    rx0.assign(rx1);   
    rx0.assign(str);   
    rx0.assign(str.begin(), str.end() - 1);   
  
    rx0.swap(rx1);   
  
// mark_count   
    std::cout << "\"abc\" mark_count == "   
        << std::regex("abc").mark_count() << std::endl;   
    std::cout << "\"(abc)\" mark_count == "   
        << std::regex("(abc)").mark_count() << std::endl;   
  
// locales   
    std::regex::locale_type loc = rx0.imbue(std::locale());   
    std::cout << "getloc == imbued == " << std::boolalpha   
        << (loc == rx0.getloc()) << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
match("abc", "") == false  
match("abc", "abcd") == false  
match("abc", "abc") == true  
match("abc", "abc") == true  
match(string("abcd"), "abc") == false  
match(string("abc"), "abc") == true  
  
"abc" mark_count == 0  
"(abc)" mark_count == 1  
getloc == imbued == true  
```  
  
##  <a name="swap"></a>  basic_regex::swap  
 交换两个正则表达式对象。  
  
```  
void swap(basic_regex& right) throw();
```  
  
### <a name="parameters"></a>参数  
 `right`  
 要交换的正则表达式对象。  
  
### <a name="remarks"></a>备注  
 成员函数交换 `*this` 和 `right`之间的正则表达式。 它定时执行此操作且不引发异常。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__regex__basic_regex_swap.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex::value_type elem = 'x';   
    std::regex::flag_type flag = std::regex::grep;   
  
    elem = elem;  // to quiet "unused" warnings   
    flag = flag;   
  
// constructors   
    std::regex rx0;   
    std::cout << "match(\"abc\", \"\") == " << std::boolalpha   
        << regex_match("abc", rx0) << std::endl;   
  
    std::regex rx1("abcd", std::regex::ECMAScript);   
    std::cout << "match(\"abc\", \"abcd\") == " << std::boolalpha   
        << regex_match("abc", rx1) << std::endl;   
  
    std::regex rx2("abcd", 3);   
    std::cout << "match(\"abc\", \"abc\") == " << std::boolalpha   
        << regex_match("abc", rx2) << std::endl;   
  
    std::regex rx3(rx2);   
    std::cout << "match(\"abc\", \"abc\") == " << std::boolalpha   
        << regex_match("abc", rx3) << std::endl;   
  
    std::string str("abcd");   
    std::regex rx4(str);   
    std::cout << "match(string(\"abcd\"), \"abc\") == " << std::boolalpha   
        << regex_match("abc", rx4) << std::endl;   
  
    std::regex rx5(str.begin(), str.end() - 1);   
    std::cout << "match(string(\"abc\"), \"abc\") == " << std::boolalpha   
        << regex_match("abc", rx5) << std::endl;   
    std::cout << std::endl;   
  
// assignments   
    rx0 = "abc";   
    rx0 = rx1;   
    rx0 = str;   
  
    rx0.assign("abcd", std::regex::ECMAScript);   
    rx0.assign("abcd", 3);   
    rx0.assign(rx1);   
    rx0.assign(str);   
    rx0.assign(str.begin(), str.end() - 1);   
  
    rx0.swap(rx1);   
  
// mark_count   
    std::cout << "\"abc\" mark_count == "   
        << std::regex("abc").mark_count() << std::endl;   
    std::cout << "\"(abc)\" mark_count == "   
        << std::regex("(abc)").mark_count() << std::endl;   
  
// locales   
    std::regex::locale_type loc = rx0.imbue(std::locale());   
    std::cout << "getloc == imbued == " << std::boolalpha   
        << (loc == rx0.getloc()) << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
match("abc", "") == false  
match("abc", "abcd") == false  
match("abc", "abc") == true  
match("abc", "abc") == true  
match(string("abcd"), "abc") == false  
match(string("abc"), "abc") == true  
  
"abc" mark_count == 0  
"(abc)" mark_count == 1  
getloc == imbued == true  
```  
  
##  <a name="value_type"></a>  basic_regex::value_type  
 元素类型。  
  
```  
typedef Elem value_type;  
```  
  
### <a name="remarks"></a>备注  
 该类型是模板参数 `Elem`的同义词。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__regex__basic_regex_value_type.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex::value_type elem = 'x';   
    std::regex::flag_type flag = std::regex::grep;   
  
    elem = elem;  // to quiet "unused" warnings   
    flag = flag;   
  
// constructors   
    std::regex rx0;   
    std::cout << "match(\"abc\", \"\") == " << std::boolalpha   
        << regex_match("abc", rx0) << std::endl;   
  
    std::regex rx1("abcd", std::regex::ECMAScript);   
    std::cout << "match(\"abc\", \"abcd\") == " << std::boolalpha   
        << regex_match("abc", rx1) << std::endl;   
  
    std::regex rx2("abcd", 3);   
    std::cout << "match(\"abc\", \"abc\") == " << std::boolalpha   
        << regex_match("abc", rx2) << std::endl;   
  
    std::regex rx3(rx2);   
    std::cout << "match(\"abc\", \"abc\") == " << std::boolalpha   
        << regex_match("abc", rx3) << std::endl;   
  
    std::string str("abcd");   
    std::regex rx4(str);   
    std::cout << "match(string(\"abcd\"), \"abc\") == " << std::boolalpha   
        << regex_match("abc", rx4) << std::endl;   
  
    std::regex rx5(str.begin(), str.end() - 1);   
    std::cout << "match(string(\"abc\"), \"abc\") == " << std::boolalpha   
        << regex_match("abc", rx5) << std::endl;   
    std::cout << std::endl;   
  
// assignments   
    rx0 = "abc";   
    rx0 = rx1;   
    rx0 = str;   
  
    rx0.assign("abcd", std::regex::ECMAScript);   
    rx0.assign("abcd", 3);   
    rx0.assign(rx1);   
    rx0.assign(str);   
    rx0.assign(str.begin(), str.end() - 1);   
  
    rx0.swap(rx1);   
  
// mark_count   
    std::cout << "\"abc\" mark_count == "   
        << std::regex("abc").mark_count() << std::endl;   
    std::cout << "\"(abc)\" mark_count == "   
        << std::regex("(abc)").mark_count() << std::endl;   
  
// locales   
    std::regex::locale_type loc = rx0.imbue(std::locale());   
    std::cout << "getloc == imbued == " << std::boolalpha   
        << (loc == rx0.getloc()) << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
match("abc", "") == false  
match("abc", "abcd") == false  
match("abc", "abc") == true  
match("abc", "abc") == true  
match(string("abcd"), "abc") == false  
match(string("abc"), "abc") == true  
  
"abc" mark_count == 0  
"(abc)" mark_count == 1  
getloc == imbued == true  
```  
  
## <a name="see-also"></a>另请参阅  
 [\<regex>](../standard-library/regex.md)   
 [regex_match](../standard-library/regex-functions.md#regex_match)   
 [regex_search](../standard-library/regex-functions.md#regex_search)   
 [regex_replace](../standard-library/regex-functions.md#regex_replace)   
 [regex](../standard-library/regex-typedefs.md#regex)   
 [wregex](../standard-library/regex-typedefs.md#wregex)   
 [regex_traits 类](../standard-library/regex-traits-class.md)


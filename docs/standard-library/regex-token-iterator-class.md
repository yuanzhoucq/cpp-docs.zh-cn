---
title: "regex_token_iterator 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- regex_token_iterator
- regex/std::regex_token_iterator
- regex/std::regex_token_iterator::regex_type
- regex/std::regex_token_iterator::value_type
- regex/std::regex_token_iterator::iterator_category
- regex/std::regex_token_iterator::difference_type
- regex/std::regex_token_iterator::pointer
- regex/std::regex_token_iterator::reference
- regex/std::regex_token_iterator::operator==
- regex/std::regex_token_iterator::operator!=
- regex/std::regex_token_iterator::operator*
- regex/std::regex_token_iterator::operator->
- regex/std::regex_token_iterator::operator++
- regex/std::regex_token_iterator::operator!=
dev_langs:
- C++
helpviewer_keywords:
- regex_token_iterator class
ms.assetid: a213ba48-8e4e-4b6b-871a-2637acf05f15
caps.latest.revision: 15
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: 38a34e2957b3fb4cf2713d61ac3633691b04b03c
ms.contentlocale: zh-cn
ms.lasthandoff: 04/29/2017

---
# <a name="regextokeniterator-class"></a>regex_token_iterator 类
子匹配项的迭代器类。  
  
## <a name="syntax"></a>语法  
```  
template<class BidIt,
   class Elem = typename std::iterator_traits<BidIt>::value_type,
   class RxTraits = regex_traits<Elem> >
class regex_token_iterator {  
public:  
   typedef basic_regex<Elem, RXtraits> regex_type;  
   typedef sub_match<BidIt> value_type;  
   typedef std::forward_iterator_tag iterator_category;  
   typedef std::ptrdiff_t difference_type;  
   typedef const sub_match<BidIt> *pointer;  
   typedef const sub_match<BidIt>& reference;  
   regex_token_iterator();
   regex_token_iterator(
      BidIt first, BidIt last,  
      const regex_type& re, int submatch = 0,  
      regex_constants::match_flag_type f = regex_constants::match_default);
   regex_token_iterator(
      BidIt first, BidIt last,  
      const regex_type& re, const std::vector<int> submatches,  
      regex_constants::match_flag_type f = regex_constants::match_default);
   template <std::size_t N>  
   regex_token_iterator(
      BidIt first, BidIt last,  
      const regex_type& re, const int (&submatches)[N],  
      regex_constants::match_flag_type f = regex_constants::match_default);
   bool operator==(const regex_token_iterator& right);
   bool operator!=(const regex_token_iterator& right);
   const basic_string<Elem>& operator*();
   const basic_string<Elem> * operator->();
   regex_token_iterator& operator++();
   regex_token_iterator& operator++(int);
private:  
   regex_iterator<BidIt, Elem, RXtraits> it; // exposition only  
   vector<int> subs;   // exposition only  
   int pos;  // exposition only  
   };  
```  
#### <a name="parameters"></a>参数  
 `BidIt`  
 子匹配项的迭代器类型。  
  
 `Elem`  
 要匹配的元素的类型。  
  
 `RXtraits`  
 元素的特征类。  
  
## <a name="remarks"></a>备注  
 此模板类描述常量前向迭代器对象。 从概念上讲，它承载 `regex_iterator` 对象，并用于搜索字符序列中正则表达式的匹配项。 它提取 `sub_match<BidIt>` 类型的对象，这些对象表示由每个正则表达式匹配项的存储向量 `subs` 中的索引值标识的子匹配项。  
  
 -1 索引值指定在上一个正则表达式匹配项末尾后立即开始（如果不存在上一个正则表达式匹配项，则为从字符序列的起始处开始）的字符序列，并扩展到但不包含当前正则表达式匹配项的第一个字符（如果不存在当前匹配项，则扩展到字符序列末尾）。 任何其他索引值 `idx` 指定承载于 `it.match[idx]`中捕获组的内容。  
  
## <a name="requirements"></a>要求  
 **标头：**\<regex 1>  
  
 **命名空间：** std  
  
##  <a name="difference_type"></a>  regex_token_iterator::difference_type  
 迭代器差异的类型。  
  
```  
typedef std::ptrdiff_t difference_type;  
```  
  
### <a name="remarks"></a>备注  
 该类型是 `std::ptrdiff_t`的同义词。  
  
### <a name="example"></a>示例  
  
```cpp    
#include <regex>   
#include <iostream>   
  
typedef std::regex_token_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "aaxaayaaz";   
    Myiter::regex_type rx("(a)a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
// show whole match   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefix before match   
    next = Myiter(pat, pat + strlen(pat), rx, -1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show (a) submatch only   
    next = Myiter(pat, pat + strlen(pat), rx, 1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and submatches   
    std::vector<int> vec;   
    vec.push_back(-1);   
    vec.push_back(1);   
    next = Myiter(pat, pat + strlen(pat), rx, vec);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and whole matches   
    int arr[] = {-1, 0};   
    next = Myiter(pat, pat + strlen(pat), rx, arr);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
```  
  
```Output  
match == aa  
match == aa  
match == aa  
  
match ==   
match == x  
match == y  
match == z  
  
match == a  
match == a  
match == a  
  
match ==   
match == a  
match == x  
match == a  
match == y  
match == a  
match == z  
  
match ==   
match == aa  
match == x  
match == aa  
match == y  
match == aa  
match == z  
```  
  
##  <a name="iterator_category"></a>  regex_token_iterator::iterator_category  
 迭代器类别的类型。  
  
```  
typedef std::forward_iterator_tag iterator_category;  
```  
  
### <a name="remarks"></a>备注  
 该类型是 `std::forward_iterator_tag`的同义词。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__regex__regex_token_iterator_iterator_category.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_token_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "aaxaayaaz";   
    Myiter::regex_type rx("(a)a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
// show whole match   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefix before match   
    next = Myiter(pat, pat + strlen(pat), rx, -1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show (a) submatch only   
    next = Myiter(pat, pat + strlen(pat), rx, 1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and submatches   
    std::vector<int> vec;   
    vec.push_back(-1);   
    vec.push_back(1);   
    next = Myiter(pat, pat + strlen(pat), rx, vec);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and whole matches   
    int arr[] = {-1, 0};   
    next = Myiter(pat, pat + strlen(pat), rx, arr);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
  
```  
  
```Output  
match == aa  
match == aa  
match == aa  
  
match ==   
match == x  
match == y  
match == z  
  
match == a  
match == a  
match == a  
  
match ==   
match == a  
match == x  
match == a  
match == y  
match == a  
match == z  
  
match ==   
match == aa  
match == x  
match == aa  
match == y  
match == aa  
match == z  
  
```  
  
##  <a name="op_neq"></a>regex_token_iterator::operator!=  
 比较不相等的迭代器。  
  
```  
bool operator!=(const regex_token_iterator& right);
```  
  
### <a name="parameters"></a>参数  
 `right`  
 要进行比较的迭代器。  
  
### <a name="remarks"></a>备注  
 成员函数返回 `!(*this == right)`。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__regex__regex_token_iterator_operator_ne.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_token_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "aaxaayaaz";   
    Myiter::regex_type rx("(a)a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
// show whole match   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefix before match   
    next = Myiter(pat, pat + strlen(pat), rx, -1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show (a) submatch only   
    next = Myiter(pat, pat + strlen(pat), rx, 1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and submatches   
    std::vector<int> vec;   
    vec.push_back(-1);   
    vec.push_back(1);   
    next = Myiter(pat, pat + strlen(pat), rx, vec);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and whole matches   
    int arr[] = {-1, 0};   
    next = Myiter(pat, pat + strlen(pat), rx, arr);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
  
```  
  
```Output  
match == aa  
match == aa  
match == aa  
  
match ==   
match == x  
match == y  
match == z  
  
match == a  
match == a  
match == a  
  
match ==   
match == a  
match == x  
match == a  
match == y  
match == a  
match == z  
  
match ==   
match == aa  
match == x  
match == aa  
match == y  
match == aa  
match == z  
  
```  
  
##  <a name="op_star"></a>regex_token_iterator::operator*  
 访问指定的子匹配项。  
  
```  
const sub_match<BidIt>& operator*();
```  
  
### <a name="remarks"></a>备注  
 成员函数返回一个 `sub_match<BidIt>` 对象，该对象表示由索引值 `subs[pos]`标识的捕获组。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__regex__regex_token_iterator_operator_star.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_token_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "aaxaayaaz";   
    Myiter::regex_type rx("(a)a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
// show whole match   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefix before match   
    next = Myiter(pat, pat + strlen(pat), rx, -1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show (a) submatch only   
    next = Myiter(pat, pat + strlen(pat), rx, 1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and submatches   
    std::vector<int> vec;   
    vec.push_back(-1);   
    vec.push_back(1);   
    next = Myiter(pat, pat + strlen(pat), rx, vec);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and whole matches   
    int arr[] = {-1, 0};   
    next = Myiter(pat, pat + strlen(pat), rx, arr);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
  
```  
  
```Output  
match == aa  
match == aa  
match == aa  
  
match ==   
match == x  
match == y  
match == z  
  
match == a  
match == a  
match == a  
  
match ==   
match == a  
match == x  
match == a  
match == y  
match == a  
match == z  
  
match ==   
match == aa  
match == x  
match == aa  
match == y  
match == aa  
match == z  
  
```  
  
##  <a name="op_add_add"></a>regex_token_iterator::operator++  
 递增迭代器。  
  
```  
regex_token_iterator& operator++();

regex_token_iterator& operator++(int);
```  
  
### <a name="remarks"></a>备注  
 如果存储的迭代器 `it` 是序列末尾迭代器，则第一个运算符将存储的值 `pos` 设置为 `subs.size()` 的值（从而生成序列末尾迭代器）。 否则，运算符递增存储的值 `pos`；如果结果等于值 `subs.size()`，则它将存储的值 `pos` 设置为零，并递增存储的迭代器 `it`。 如果递增存储的迭代器让它不等于序列结尾迭代器，则运算符不会进一步执行操作。 否则，如果前面匹配项的结尾位于字符序列的结尾，则运算符将 `pos` 的存储的值设置为 `subs.size()`。 否则，运算符重复递增存储的值 `pos`，直到 `pos == subs.size()` 或 `subs[pos] == -1`（从而确保其中一个索引值为 -1 时，迭代器的下一次取消引用将返回字符序列的结尾）。 在所有情况下，运算符都会返回对象。  
  
 第二个运算符生成对象的副本，递增对象，然后返回副本。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__regex__regex_token_iterator_operator_inc.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_token_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "aaxaayaaz";   
    Myiter::regex_type rx("(a)a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
// show whole match   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefix before match   
    next = Myiter(pat, pat + strlen(pat), rx, -1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show (a) submatch only   
    next = Myiter(pat, pat + strlen(pat), rx, 1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and submatches   
    std::vector<int> vec;   
    vec.push_back(-1);   
    vec.push_back(1);   
    next = Myiter(pat, pat + strlen(pat), rx, vec);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and whole matches   
    int arr[] = {-1, 0};   
    next = Myiter(pat, pat + strlen(pat), rx, arr);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
  
```  
  
```Output  
match == aa  
match == aa  
match == aa  
  
match ==   
match == x  
match == y  
match == z  
  
match == a  
match == a  
match == a  
  
match ==   
match == a  
match == x  
match == a  
match == y  
match == a  
match == z  
  
match ==   
match == aa  
match == x  
match == aa  
match == y  
match == aa  
match == z  
  
```  
  
##  <a name="op_eq_eq"></a>regex_token_iterator::operator==  
 比较迭代器是否相等。  
  
```  
bool operator==(const regex_token_iterator& right);
```  
  
### <a name="parameters"></a>参数  
 右  
 要进行比较的迭代器。  
  
### <a name="remarks"></a>备注  
 成员函数返回 `it == right.it && subs == right.subs && pos == right.pos`。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__regex__regex_token_iterator_operator_eq.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_token_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "aaxaayaaz";   
    Myiter::regex_type rx("(a)a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
// show whole match   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefix before match   
    next = Myiter(pat, pat + strlen(pat), rx, -1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show (a) submatch only   
    next = Myiter(pat, pat + strlen(pat), rx, 1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and submatches   
    std::vector<int> vec;   
    vec.push_back(-1);   
    vec.push_back(1);   
    next = Myiter(pat, pat + strlen(pat), rx, vec);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and whole matches   
    int arr[] = {-1, 0};   
    next = Myiter(pat, pat + strlen(pat), rx, arr);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
  
```  
  
```Output  
match == aa  
match == aa  
match == aa  
  
match ==   
match == x  
match == y  
match == z  
  
match == a  
match == a  
match == a  
  
match ==   
match == a  
match == x  
match == a  
match == y  
match == a  
match == z  
  
match ==   
match == aa  
match == x  
match == aa  
match == y  
match == aa  
match == z  
  
```  
  
##  <a name="regex_token_iterator__operator-_gt"></a>regex_token_iterator::operator-&gt;  
 访问指定的子匹配项。  
  
```  
const sub_match<BidIt> * operator->();
```  
  
### <a name="remarks"></a>备注  
 成员函数返回一个指向 `sub_match<BidIt>` 对象的指针，该对象表示由索引值 `subs[pos]`标识的捕获组。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__regex__regex_token_iterator_operator_arrow.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_token_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "aaxaayaaz";   
    Myiter::regex_type rx("(a)a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
// show whole match   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefix before match   
    next = Myiter(pat, pat + strlen(pat), rx, -1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show (a) submatch only   
    next = Myiter(pat, pat + strlen(pat), rx, 1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and submatches   
    std::vector<int> vec;   
    vec.push_back(-1);   
    vec.push_back(1);   
    next = Myiter(pat, pat + strlen(pat), rx, vec);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and whole matches   
    int arr[] = {-1, 0};   
    next = Myiter(pat, pat + strlen(pat), rx, arr);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
  
```  
  
```Output  
match == aa  
match == aa  
match == aa  
  
match ==   
match == x  
match == y  
match == z  
  
match == a  
match == a  
match == a  
  
match ==   
match == a  
match == x  
match == a  
match == y  
match == a  
match == z  
  
match ==   
match == aa  
match == x  
match == aa  
match == y  
match == aa  
match == z  
  
```  
  
##  <a name="pointer"></a>  regex_token_iterator::pointer  
 指向一个匹配的指针的类型。  
  
```  
typedef sub_match<BidIt> *pointer;  
```  
  
### <a name="example"></a>示例  
  
```cpp  
// std__regex__regex_token_iterator_pointer.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_token_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "aaxaayaaz";   
    Myiter::regex_type rx("(a)a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
// show whole match   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefix before match   
    next = Myiter(pat, pat + strlen(pat), rx, -1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show (a) submatch only   
    next = Myiter(pat, pat + strlen(pat), rx, 1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and submatches   
    std::vector<int> vec;   
    vec.push_back(-1);   
    vec.push_back(1);   
    next = Myiter(pat, pat + strlen(pat), rx, vec);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and whole matches   
    int arr[] = {-1, 0};   
    next = Myiter(pat, pat + strlen(pat), rx, arr);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
  
```  
  
```Output  
match == aa  
match == aa  
match == aa  
  
match ==   
match == x  
match == y  
match == z  
  
match == a  
match == a  
match == a  
  
match ==   
match == a  
match == x  
match == a  
match == y  
match == a  
match == z  
  
match ==   
match == aa  
match == x  
match == aa  
match == y  
match == aa  
match == z  
  
```  
  
### <a name="remarks"></a>备注  
 该类型是 `sub_match<BidIt>*`的同义词，其中 `BidIt` 是模板参数。  
  
##  <a name="reference"></a>  regex_token_iterator::reference  
 对子匹配项的引用的类型。  
  
```  
typedef sub_match<BidIt>& reference;  
```  
  
### <a name="remarks"></a>备注  
 类型是 `sub_match<BidIt>&` 的同义词，其中 `BidIt` 是模板参数。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__regex__regex_token_iterator_reference.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_token_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "aaxaayaaz";   
    Myiter::regex_type rx("(a)a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
// show whole match   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefix before match   
    next = Myiter(pat, pat + strlen(pat), rx, -1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show (a) submatch only   
    next = Myiter(pat, pat + strlen(pat), rx, 1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and submatches   
    std::vector<int> vec;   
    vec.push_back(-1);   
    vec.push_back(1);   
    next = Myiter(pat, pat + strlen(pat), rx, vec);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and whole matches   
    int arr[] = {-1, 0};   
    next = Myiter(pat, pat + strlen(pat), rx, arr);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
  
```  
  
```Output  
match == aa  
match == aa  
match == aa  
  
match ==   
match == x  
match == y  
match == z  
  
match == a  
match == a  
match == a  
  
match ==   
match == a  
match == x  
match == a  
match == y  
match == a  
match == z  
  
match ==   
match == aa  
match == x  
match == aa  
match == y  
match == aa  
match == z  
  
```  
  
##  <a name="regex_token_iterator"></a>  regex_token_iterator::regex_token_iterator  
 构造迭代器。  
  
```  
regex_token_iterator();

regex_token_iterator(BidIt first, BidIt last,  
    const regex_type& re, int submatch = 0,  
    regex_constants::match_flag_type f = regex_constants::match_default);

regex_token_iterator(BidIt first, BidIt last,  
    const regex_type& re, const vector<int> submatches,  
    regex_constants::match_flag_type f = regex_constants::match_default);

template <std::size_t N>  
regex_token_iterator(BidIt first, BidIt last,  
    const regex_type& re, const int (&submatches)[N],  
    regex_constants::match_flag_type f = regex_constants::match_default);
```  
  
### <a name="parameters"></a>参数  
 `first`  
 要匹配的序列的开头。  
  
 `last`  
 要匹配的序列的结尾。  
  
 `re`  
 匹配项正则表达式。  
  
 `f`  
 匹配标志。  
  
### <a name="remarks"></a>备注  
 第一个构造函数将构造序列末迭代器。  
  
 第二个构造函数将构造一个对象，其存储的迭代器 `it` 初始化为 `regex_iterator<BidIt, Elem, RXtraits>(first, last, re, f)`，其存储的向量 `subs` 承载恰好一个整数（值为 `submatch`），并且其存储的值 `pos` 为零。 注意：对于每个成功的正则表达式匹配项，生成的对象将提取由索引值 `submatch` 标识的子匹配项。  
  
 第三个构造函数将构造一个对象，其存储的迭代器 `it` 初始化为 `regex_iterator<BidIt, Elem, RXtraits>(first, last, re, f)`，其存储的向量 `subs` 承载构造函数参数 `submatches`的一个副本，并且其存储的值 `pos` 为零。  
  
 第四个构造函数将构造一个对象，其存储的迭代器 `it` 初始化为 `regex_iterator<BidIt, Elem, RXtraits>(first, last, re, f)`，其存储的向量 `subs` 承载构造函数参数 `N` 指向的 `submatches`值，并且其存储的值 `pos` 为零。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__regex__regex_token_iterator_construct.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_token_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "aaxaayaaz";   
    Myiter::regex_type rx("(a)a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
// show whole match   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefix before match   
    next = Myiter(pat, pat + strlen(pat), rx, -1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show (a) submatch only   
    next = Myiter(pat, pat + strlen(pat), rx, 1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and submatches   
    std::vector<int> vec;   
    vec.push_back(-1);   
    vec.push_back(1);   
    next = Myiter(pat, pat + strlen(pat), rx, vec);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and whole matches   
    int arr[] = {-1, 0};   
    next = Myiter(pat, pat + strlen(pat), rx, arr);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
  
```  
  
```Output  
match == aa  
match == aa  
match == aa  
  
match ==   
match == x  
match == y  
match == z  
  
match == a  
match == a  
match == a  
  
match ==   
match == a  
match == x  
match == a  
match == y  
match == a  
match == z  
  
match ==   
match == aa  
match == x  
match == aa  
match == y  
match == aa  
match == z  
  
```  
  
##  <a name="regex_type"></a>regex_token_iterator::regex_type  
 要匹配的正则表达式类型。  
  
```  
typedef basic_regex<Elem, RXtraits> regex_type;  
```  
  
### <a name="remarks"></a>备注  
 typedef 是 `basic_regex<Elem, RXtraits>`的同义词。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__regex__regex_token_iterator_regex_type.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_token_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "aaxaayaaz";   
    Myiter::regex_type rx("(a)a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
// show whole match   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefix before match   
    next = Myiter(pat, pat + strlen(pat), rx, -1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show (a) submatch only   
    next = Myiter(pat, pat + strlen(pat), rx, 1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and submatches   
    std::vector<int> vec;   
    vec.push_back(-1);   
    vec.push_back(1);   
    next = Myiter(pat, pat + strlen(pat), rx, vec);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and whole matches   
    int arr[] = {-1, 0};   
    next = Myiter(pat, pat + strlen(pat), rx, arr);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
  
```  
  
```Output  
match == aa  
match == aa  
match == aa  
  
match ==   
match == x  
match == y  
match == z  
  
match == a  
match == a  
match == a  
  
match ==   
match == a  
match == x  
match == a  
match == y  
match == a  
match == z  
  
match ==   
match == aa  
match == x  
match == aa  
match == y  
match == aa  
match == z  
  
```  
  
##  <a name="value_type"></a>  regex_token_iterator::value_type  
 子匹配项的类型。  
  
```  
typedef sub_match<BidIt> value_type;  
```  
  
### <a name="remarks"></a>备注  
 类型是 `sub_match<BidIt>` 的同义词，其中 `BidIt` 是模板参数。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__regex__regex_token_iterator_value_type.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_token_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "aaxaayaaz";   
    Myiter::regex_type rx("(a)a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
// show whole match   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefix before match   
    next = Myiter(pat, pat + strlen(pat), rx, -1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show (a) submatch only   
    next = Myiter(pat, pat + strlen(pat), rx, 1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and submatches   
    std::vector<int> vec;   
    vec.push_back(-1);   
    vec.push_back(1);   
    next = Myiter(pat, pat + strlen(pat), rx, vec);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and whole matches   
    int arr[] = {-1, 0};   
    next = Myiter(pat, pat + strlen(pat), rx, arr);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
  
```  
  
```Output  
match == aa  
match == aa  
match == aa  
  
match ==   
match == x  
match == y  
match == z  
  
match == a  
match == a  
match == a  
  
match ==   
match == a  
match == x  
match == a  
match == y  
match == a  
match == z  
  
match ==   
match == aa  
match == x  
match == aa  
match == y  
match == aa  
match == z  
  
```  
  
## <a name="see-also"></a>另请参阅  
[\<regex>](../standard-library/regex.md)  
[regex_constants 类](../standard-library/regex-constants-class.md)  
[regex_error 类](../standard-library/regex-error-class.md)  
[\<regex> functions](../standard-library/regex-functions.md)  
[regex_iterator 类](../standard-library/regex-iterator-class.md)  
[\<regex> operators](../standard-library/regex-operators.md)  
[regex_traits 类](../standard-library/regex-traits-class.md)  
[\<regex> typedefs](../standard-library/regex-typedefs.md)  



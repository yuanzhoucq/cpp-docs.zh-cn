---
title: "basic_regex 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::tr1::basic_regex"
  - "basic_regex"
  - "std.tr1.basic_regex"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "basic_regex 类 [TR1]"
ms.assetid: 8a18c6b4-f22a-4cfd-bc16-b4267867ebc3
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# basic_regex 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

包装正则表达式。  
  
## 语法  
  
```  
template<class Elem,  
    class RXtraits = regex_traits<Elem>,  
    class basic_regex {  
public:  
    basic_regex();  
    explicit basic_regex(const Elem *ptr,  
        flag_type flags = ECMAScript);  
    basic_regex(const Elem *ptr, size_type len,  
        flag_type flags = ECMAScript);  
    basic_regex(const basic_regex& right);  
    template<class STtraits, class STalloc>  
        explicit basic_regex(const basic_string<Elem, STtraits, STalloc>& str,  
            flag_type flags = ECMAScript);  
    template<class InIt>  
        explicit basic_regex(InIt first, InIt last,  
            flag_type flags = ECMAScript);  
  
    basic_regex& operator=(const basic_regex& right);  
    basic_regex& operator=(const Elem *ptr);  
    template<class STtraits, class STalloc>  
        basic_regex& operator=(const basic_string<Elem, STtraits, STalloc>& str);  
    basic_regex& assign(const basic_regex& right);  
    basic_regex& assign(const Elem *ptr,  
        flag_type flags = ECMAScript);  
    basic_regex& assign(const Elem *ptr, size_type len,  
        flag_type flags = ECMAScript);  
    template<class STtraits, class STalloc>  
    basic_regex& assign(const basic_string<Elem, STtraits, STalloc>& str,  
        flag_type flags = ECMAScript);  
    template<class InIt>  
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
  
#### 参数  
 `Elem`  
 要匹配的元素的类型。  
  
 `RXtraits`  
 元素的特征类。  
  
## 备注  
 此模板类描述包含正则表达式的对象。  此模板类对象可传递给模板函数 [regex\_match 函数](../Topic/regex_match%20Function.md)、[regex\_search 函数](../Topic/regex_search%20Function.md) 和 [regex\_replace 函数](../Topic/regex_replace%20Function.md)，结合适合的文本字符串参数，可搜索与正则表达式匹配的文本。  此模板类有两种专用化，包括针对 `char` 类型元素的类型定义 [regex Typedef](../Topic/regex%20Typedef.md)，以及针对 `wchar_t` 类型元素的类型定义 [wregex Typedef](../Topic/wregex%20Typedef.md)。  
  
 模板参数 `RXtraits` 描述模板类支持的正则表达式语法的各个重要属性。  一个类，指定这些正则表达式特征的类的外部接口必须与模板类 [regex\_traits 类](../standard-library/regex-traits-class.md) 的对象相同。  
  
 某些函数使用操作数序列来定义正则表达式。  可以通过多种方式指定此操作数序列：  
  
 `ptr` \- 从 `Elem`（不能为 null 指针）开始、以 null 结尾的序列（例如 C 字符串，`char` 类型的 `ptr`），其中结尾元素为值 `value_type()`，且不是操作数序列的一部分  
  
 `ptr`, `count` \- 从 `count`（不能为 null 指针）开始的 `ptr` 元素序列  
  
 `str` \- `basic_string` 对象 `str` 指定的序列  
  
 `first`, `last` \- 迭代器 `first` 和 `last` 在范围 `[first, last)` 中分隔的元素序列  
  
 `right` \- `basic_regex` 对象 `right`  
  
 这些成员函数还使用参数 `flags` 指定用于解释正则表达式的各个选项以及 `RXtraits` 类型描述的选项。  
  
## 要求  
 **标头：**\<regex\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<regex\>](../standard-library/regex.md)   
 [regex\_match 函数](../Topic/regex_match%20Function.md)   
 [regex\_search 函数](../Topic/regex_search%20Function.md)   
 [regex\_replace 函数](../Topic/regex_replace%20Function.md)   
 [regex Typedef](../Topic/regex%20Typedef.md)   
 [wregex Typedef](../Topic/wregex%20Typedef.md)   
 [regex\_traits 类](../standard-library/regex-traits-class.md)
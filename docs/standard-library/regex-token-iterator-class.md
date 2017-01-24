---
title: "regex_token_iterator 类 | Microsoft Docs"
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
  - "regex_token_iterator"
  - "std.tr1.regex_token_iterator"
  - "std::tr1::regex_token_iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "regex_token_iterator 类 [TR1]"
ms.assetid: a213ba48-8e4e-4b6b-871a-2637acf05f15
caps.latest.revision: 15
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# regex_token_iterator 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

子匹配项的迭代器类。  
  
## 语法  
  
```  
template<class BidIt, class Elem = iterator_traits<BidIt>::value_type,  
    class RXtraits = regex_traits<Elem> >  
        class regex_token_iterator {  
public:  
    typedef basic_regex<Elem, RXtraits> regex_type;  
    typedef sub_match<BidIt> value_type;  
    typedef std::forward_iterator_tag iterator_category;  
    typedef std::ptrdiff_t difference_type;  
    typedef const sub_match<BidIt> *pointer;  
    typedef const sub_match<BidIt>& reference;  
  
    regex_token_iterator();  
    regex_token_iterator(BidIt first, BidIt last,  
        const regex_type& re, int submatch = 0,  
        regex_constants::match_flag_type f = regex_constants::match_default);  
    regex_token_iterator(BidIt first, BidIt last,  
        const regex_type& re, const std::vector<int> submatches,  
        regex_constants::match_flag_type f = regex_constants::match_default);  
    template<std::size_t N>  
    regex_token_iterator(BidIt first, BidIt last,  
        const regex_type& re, const int (&submatches)[N],  
        regex_constants::match_flag_type f = regex_constants::match_default);  
  
    bool operator==(const regex_token_iterator& right);  
    bool operator!=(const regex_token_iterator& right);  
    const basic_string<Elem>& operator*();  
    const basic_string<Elem> *operator->();  
    regex_token_iterator& operator++();  
    regex_token_iterator& operator++(int);  
private:  
    regex_iterator<BidIt, Elem, RXtraits> it; // exposition only  
    vector<int> subs;                         // exposition only  
    int pos;                                  // exposition only  
    };  
```  
  
#### 参数  
 `BidIt`  
 子匹配项的迭代器类型。  
  
 `Elem`  
 要匹配的元素的类型。  
  
 `RXtraits`  
 元素的特征类。  
  
## 备注  
 此模板类描述常量前向迭代器对象。 从概念上讲，它承载 `regex_iterator` 对象，并用于搜索字符序列中正则表达式的匹配项。 它提取 `sub_match<BidIt>` 类型的对象，这些对象表示由每个正则表达式匹配项的存储向量 `subs` 中的索引值标识的子匹配项。  
  
 \-1 索引值指定在上一个正则表达式匹配项末尾后立即开始（如果不存在上一个正则表达式匹配项，则为从字符序列的起始处开始）的字符序列，并扩展到但不包含当前正则表达式匹配项的第一个字符（如果不存在当前匹配项，则扩展到字符序列末尾）。 任何其他索引值 `idx` 指定承载于 `it.match[idx]` 中捕获组的内容。  
  
## 要求  
 **标头：**\<regex\>  
  
 **命名空间：**std  
  
## 请参阅  
 [\<regex\>](../standard-library/regex.md)   
 [regex\_token\_iterator](../standard-library/regex-token-iterator-class.md)   
 [regex\_iterator 类](../standard-library/regex-iterator-class.md)
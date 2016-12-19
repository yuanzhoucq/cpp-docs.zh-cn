---
title: "regex_iterator 类 | Microsoft Docs"
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
  - "std::tr1::regex_iterator"
  - "std.tr1.regex_iterator"
  - "regex_iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "regex_iterator 类 [TR1]"
ms.assetid: 0cfd8fd0-5a95-4f3c-bf8e-6ef028c423d3
caps.latest.revision: 16
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# regex_iterator 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

匹配项的迭代器类。  
  
## 语法  
  
```  
template<class BidIt, class Elem = iterator_traits<BidIt>::value_type,  
    class RXtraits = regex_traits<Elem> >  
        class regex_iterator {  
public:  
    typedef basic_regex<Elem, RXtraits> regex_type;  
    typedef match_results<BidIt> value_type;  
    typedef std::forward_iterator_tag iterator_category;  
    typedef std::ptrdiff_t difference_type;  
    typedef const match_results<BidIt>* pointer;  
    typedef const match_results<BidIt>& reference;  
  
    regex_iterator();  
    regex_iterator(BidIt first, BidIt last,  
        const regex_type& re,  
        regex_constants::match_flag_type f = regex_constants::match_default);  
  
    bool operator==(const regex_iterator& right);  
    bool operator!=(const regex_iterator& right);  
    const match_results<BidIt>& operator*();  
    const match_results<BidIt> *operator->();  
    regex_iterator& operator++();  
    regex_iterator& operator++(int);  
  
    BidIt begin;                            // exposition only  
    BidIt end;                              // exposition only  
    regex_type *pregex;                     // exposition only  
    regex_constants::match_flag_type flags; // exposition only  
    match_results<BidIt> match;             // exposition only  
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
 此模板类描述常量前向迭代器对象。 它将其正则表达式对象 `*pregex` 重复应用到迭代器范围 `[begin, end)` 定义的字符序列，以提取 `match_results<BidIt>` 类型的对象。  
  
## 示例  
 有关正则表达式的示例，请参阅下面的主题：  
  
-   [regex\_match 函数](../Topic/regex_match%20Function.md)  
  
-   [regex\_replace 函数](../Topic/regex_replace%20Function.md)  
  
-   [regex\_search 函数](../Topic/regex_search%20Function.md)  
  
-   [swap 函数](../Topic/swap%20Function%20%3Cregex%3E.md)  
  
## 要求  
 **标头：**\<regex\>  
  
 **命名空间：**std  
  
## 请参阅  
 [\<regex\>](../standard-library/regex.md)   
 [regex\_iterator](../standard-library/regex-iterator-class.md)
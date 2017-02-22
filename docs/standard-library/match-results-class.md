---
title: "match_results 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.tr1.match_results"
  - "match_results"
  - "std::tr1::match_results"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "match_results 类 [TR1]"
ms.assetid: b504fdca-e5dd-429d-9960-6e27c9167fa6
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# match_results 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

包含一系列子匹配项。  
  
## 语法  
  
```  
template<class BidIt,  
    class Alloc = allocator<typename iterator_traits<BidIt>::value_type> >  
    class match_results {  
public:  
    explicit match_results(const Alloc& alloc = Alloc());  
    match_results(const match_results& right);  
  
    match_results& operator=(const match_results& right);  
  
    difference_type position(size_type sub = 0) const;  
    difference_type length(size_type sub = 0) const;  
    string_type str(size_type sub = 0) const;  
    const_reference operator[](size_type n) const;  
  
    const_reference prefix() const;  
    const_reference suffix() const;  
    const_iterator begin() const;  
    const_iterator end() const;  
  
    template<class OutIt>  
        OutIt format(OutIt out,  
            const string_type& fmt, match_flag_type flags = format_default) const;  
    string_type format(const string_type& fmt,  
        match_flag_type flags = format_default) const;  
  
    allocator_type get_allocator() const;  
    void swap(const match_results& other) throw();  
  
    size_type size() const;  
    size_type max_size() const;  
    bool empty() const;  
  
    typedef sub_match<BidIt> value_type;  
    typedef const typename Alloc::const_reference const_reference;  
    typedef const_reference reference;  
    typedef T0 const_iterator;  
    typedef const_iterator iterator;  
    typedef typename iterator_traits<BidIt>::difference_type difference_type;  
    typedef typename Alloc::size_type size_type;  
    typedef Alloc allocator_type;  
    typedef typename iterator_traits<BidIt>::value_type char_type;  
    typedef basic_string<char_type> string_type;  
    };  
```  
  
#### 参数  
 `BidIt`  
 子匹配项的迭代器类型。  
  
 `Alloc`  
 用于管理存储的分配器的类型。  
  
## 备注  
 模板类描述一个对象，该对象用于控制由正则表达式搜索生成的 `sub_match<BidIt>` 类型元素不可修改的序列。 每个元素指向与该元素对应的捕获组匹配的子序列。  
  
## 要求  
 **标头：**\<regex\>  
  
 **命名空间：**std  
  
## 请参阅  
 [\<regex\>](../standard-library/regex.md)
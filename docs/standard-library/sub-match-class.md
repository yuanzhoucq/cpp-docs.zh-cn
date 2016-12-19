---
title: "sub_match 类 | Microsoft Docs"
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
  - "sub_match"
  - "std::tr1::sub_match"
  - "std.tr1.sub_match"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "sub_match 类 [TR1]"
ms.assetid: 804e2b9e-d16a-4c4c-ac60-024e0b2dd0e8
caps.latest.revision: 19
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# sub_match 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

介绍子匹配项。  
  
## 语法  
  
```  
template<class BidIt>  
    class sub_match  
        : public std::pair<BidIt, BidIt> {  
public:  
    bool matched;  
    int compare(const sub_match& right) const;  
    int compare(const basic_string<value_type>& right) const;  
    int compare(const value_type *right) const;  
    difference_type length() const;  
    operator basic_string<value_type>() const;  
    basic_string<value_type> str() const;  
    typedef typename iterator_traits<BidIt>::value_type value_type;  
    typedef typename iterator_traits<BidIt>::difference_type difference_type;  
    typedef BidIt iterator;  
    };  
```  
  
#### 参数  
 `BidIt`  
 子匹配项的迭代器类型。  
  
## 备注  
 此模板类描述指定字符序列的对象，该字符序列与调用 [regex\_match 函数](../Topic/regex_match%20Function.md) 或 [regex\_search 函数](../Topic/regex_search%20Function.md) 的捕获组匹配。[match\_results 类](../standard-library/match-results-class.md) 类型的对象保存这些对象的数组，每个数组用于搜索中所用正则表达式中的每个捕获组。  
  
 如果捕获组不匹配，则对象的数据成员 `matched` 保持为 false，两个迭代器 `first` 和 `second`（继承自基类 `std::pair`）相等。 如果捕获组匹配，则 `matched` 保持为 true，迭代器 `first` 指向与捕获组匹配的目标序列中第一个字符，迭代器 `second` 与捕获组匹配的目标序列中最后一个字符后紧邻的位置。 请注意，对于长度为零的匹配项，成员 `matched` 保持为 true，两个迭代器将相等并将同时将指向匹配项的位置。  
  
 当捕获组仅由一个断言或一个允许重复次数为零的重复组成时，可能出现长度为零的匹配项。 例如：  
  
 “^”匹配目标序列“a”；`sub_match` 对象对应捕获组 0 持有两个迭代器，它们均指向序列中第一个字符。  
  
 “b\(a\*\)b”匹配目标序列“bb”；`sub_match` 对象对应捕获组 0 持有两个迭代器，它们均指向序列中第二个字符。  
  
## 要求  
 **标头：**\<regex\>  
  
 **命名空间：**std  
  
## 请参阅  
 [\<regex\>](../standard-library/regex.md)   
 [sub\_match](../standard-library/sub-match-class.md)   
 [regex\_match 函数](../Topic/regex_match%20Function.md)   
 [regex\_search 函数](../Topic/regex_search%20Function.md)
---
title: "&lt;regex&gt; | Microsoft Docs"
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
  - "<regex>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "regex 标头 [TR1]"
ms.assetid: 5dd4ef74-6063-4dbc-b692-1960bb736f0b
caps.latest.revision: 23
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt;regex&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定义一个模板类来分析[正则表达式 \(C\+\+\)](../standard-library/regular-expressions-cpp.md)，以及定义多个模板类和函数来在文本中搜索正则表达式对象的匹配项。  
  
## 语法  
  
```  
#include <regex>  
```  
  
## 备注  
 若要创建正则表达式对象，请将模板类 [basic\_regex 类](../standard-library/basic-regex-class.md) 或其专用化（[regex Typedef](../Topic/regex%20Typedef.md) 和[wregex Typedef](../Topic/wregex%20Typedef.md)）之一与类型为 [regex\_constants::syntax\_option\_type](../Topic/regex_constants::syntax_option_type.md) 的语法标志一起使用。  
  
 若要在文本中搜索正则表达式对象的匹配项，请将模板函数 [regex\_match 函数](../Topic/regex_match%20Function.md) 和 [regex\_search 函数](../Topic/regex_search%20Function.md) 与类型 [regex\_constants::match\_flag\_type](../Topic/regex_constants::match_flag_type.md) 的匹配项标志一起使用。  这些函数通过将模板类 [match\_results 类](../standard-library/match-results-class.md) 及其专用化（[cmatch Typedef](../Topic/cmatch%20Typedef.md)、[wcmatch Typedef](../Topic/wcmatch%20Typedef.md)、[smatch Typedef](../Topic/smatch%20Typedef.md) 和 [wsmatch Typedef](../Topic/wsmatch%20Typedef.md)）与模板类 [sub\_match 类](../standard-library/sub-match-class.md) 及其专用化（[csub\_match Typedef](../Topic/csub_match%20Typedef.md)、[wcsub\_match Typedef](../Topic/wcsub_match%20Typedef.md)、[ssub\_match Typedef](../Topic/ssub_match%20Typedef.md) 和 [wssub\_match Typedef](../Topic/wssub_match%20Typedef.md)）一起使用来返回结果。  
  
 若要替换匹配正则表达式对象的文本，请将模板函数 [regex\_replace 函数](../Topic/regex_replace%20Function.md) 与类型 [regex\_constants::match\_flag\_type](../Topic/regex_constants::match_flag_type.md) 的匹配项标志一起使用。  
  
 若要循环访问正则表达式对象的多个匹配项，请将模板类 [regex\_iterator 类](../standard-library/regex-iterator-class.md) 和 [regex\_token\_iterator 类](../standard-library/regex-token-iterator-class.md) 或其专用化之一（[cregex\_iterator Typedef](../Topic/cregex_iterator%20Typedef.md)、[sregex\_iterator Typedef](../Topic/sregex_iterator%20Typedef.md)、[wcregex\_iterator Typedef](../Topic/wcregex_iterator%20Typedef.md)、[wsregex\_iterator Typedef](../Topic/wsregex_iterator%20Typedef.md)、[cregex\_token\_iterator Typedef](../Topic/cregex_token_iterator%20Typedef.md)、[sregex\_token\_iterator Typedef](../Topic/sregex_token_iterator%20Typedef.md)、[wcregex\_token\_iterator Typedef](../Topic/wcregex_token_iterator%20Typedef.md) 或 [wsregex\_token\_iterator Typedef](../Topic/wsregex_token_iterator%20Typedef.md)）与类型 [regex\_constants::match\_flag\_type](../Topic/regex_constants::match_flag_type.md) 的匹配项标志一起使用。  
  
 若要修改正则表达式语法的详细信息，请编写一个实现正则表达式特征的类。  
  
### 类  
  
|||  
|-|-|  
|[basic\_regex](../standard-library/basic-regex-class.md)|包装正则表达式。|  
|[match\_results](../standard-library/match-results-class.md)|包含一系列子匹配项。|  
|[regex\_constants](../standard-library/regex-constants-class.md)|包含各种类型的常量。|  
|[regex\_error](../standard-library/regex-error-class.md)|报告错误的正则表达式。|  
|[regex\_iterator](../standard-library/regex-iterator-class.md)|循环访问匹配结果。|  
|[regex\_traits](../standard-library/regex-traits-class.md)|描述用于匹配的元素的特征。|  
|[regex\_traits\<char\>](../standard-library/regex-traits-char-class.md)|描述用于匹配的 `char` 的特征。|  
|[regex\_traits\<wchar\_t\>](../standard-library/regex-traits-wchar-t-class.md)|描述用于匹配的 `wchar_t` 的特征。|  
|[regex\_token\_iterator](../standard-library/regex-token-iterator-class.md)|循环访问子匹配项。|  
|[sub\_match](../standard-library/sub-match-class.md)|介绍子匹配项。|  
  
### 类型定义  
  
|||  
|-|-|  
|[cmatch](../Topic/cmatch%20Typedef.md)|`char` `match_results` 的类型定义。|  
|[cregex\_iterator](../Topic/cregex_iterator%20Typedef.md)|`char` `regex_iterator` 的类型定义。|  
|[cregex\_token\_iterator](../Topic/cregex_token_iterator%20Typedef.md)|`char` `regex_token_iterator` 的类型定义。|  
|[csub\_match](../Topic/csub_match%20Typedef.md)|`char` `sub_match` 的类型定义。|  
|[正则表达式](../Topic/regex%20Typedef.md)|`char` `basic_regex` 的类型定义。|  
|[smatch](../Topic/smatch%20Typedef.md)|`string` `match_results` 的类型定义。|  
|[sregex\_iterator](../Topic/sregex_iterator%20Typedef.md)|`string` `regex_iterator` 的类型定义。|  
|[sregex\_token\_iterator](../Topic/sregex_token_iterator%20Typedef.md)|`string` `regex_token_iterator` 的类型定义。|  
|[ssub\_match](../Topic/ssub_match%20Typedef.md)|`string` `sub_match` 的类型定义。|  
|[wcmatch](../Topic/wcmatch%20Typedef.md)|`wchar_t` `match_results` 的类型定义。|  
|[wcregex\_iterator](../Topic/wcregex_iterator%20Typedef.md)|`wchar_t` `regex_iterator` 的类型定义。|  
|[wcregex\_token\_iterator](../Topic/wcregex_token_iterator%20Typedef.md)|`wchar_t` `regex_token_iterator` 的类型定义。|  
|[wcsub\_match](../Topic/wcsub_match%20Typedef.md)|`wchar_t` `sub_match` 的类型定义。|  
|[wregex](../Topic/wregex%20Typedef.md)|`wchar_t` `basic_regex` 的类型定义。|  
|[wsmatch](../Topic/wsmatch%20Typedef.md)|`wstring` `match_results` 的类型定义。|  
|[wsregex\_iterator](../Topic/wsregex_iterator%20Typedef.md)|`wstring` `regex_iterator` 的类型定义。|  
|[wsregex\_token\_iterator](../Topic/wsregex_token_iterator%20Typedef.md)|`wstring` `regex_token_iterator` 的类型定义。|  
|[wssub\_match](../Topic/wssub_match%20Typedef.md)|`wstring` `sub_match` 的类型定义。|  
  
### Functions  
  
|||  
|-|-|  
|[regex\_match](../Topic/regex_match%20Function.md)|与正则表达式完全匹配。|  
|[regex\_replace](../Topic/regex_replace%20Function.md)|替换匹配正则表达式。|  
|[regex\_search](../Topic/regex_search%20Function.md)|搜索正则表达式匹配项。|  
|[swap](../Topic/swap%20Function%20%3Cregex%3E.md)|交换 `basic_regex` 或 `match_results` 对象。|  
  
### 运算符  
  
|||  
|-|-|  
|[operator\=\=](../Topic/operator==%20%3Cregex%3E.md)|比较各种对象，相等。|  
|[operator\!\=](../Topic/operator!=%20%3Cregex%3E.md)|比较各种对象，不相等。|  
|[运算符 \<](../Topic/operator%3C%20%3Cregex%3E.md)|比较各种对象，小于。|  
|[运算符 \<\=](../Topic/operator%3C=%20%3Cregex%3E.md)|比较各种对象，小于或等于。|  
|[运算符 \>](../Topic/operator%3E%20%3Cregex%3E.md)|比较各种对象，大于。|  
|[运算符 \>\=](../Topic/operator%3E=%20%3Cregex%3E.md)|比较各种对象，大于或等于。|  
|[运算符 \<\<](../Topic/operator%3C%3C%20%3Cregex%3E.md)|将 `sub_match` 插入流中。|  
  
## 请参阅  
 [正则表达式 \(C\+\+\)](../standard-library/regular-expressions-cpp.md)
---
title: "regex_traits 类 | Microsoft Docs"
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
  - "regex_traits"
  - "std::tr1::regex_traits"
  - "std.tr1.regex_traits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "regex_traits 类 [TR1]"
ms.assetid: bc5a5eed-32fc-4eb7-913d-71c42e729e81
caps.latest.revision: 19
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# regex_traits 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述用于匹配的元素的特征。  
  
## 语法  
  
```  
template<class Elem>  
    struct regex_traits {  
    regex_traits();  
  
    static size_type length(const char_type *str);  
    char_type translate(char_type ch) const;  
    char_type translate_nocase(char_type ch) const;  
    template<class FwdIt>  
        string_type transform(FwdIt first, FwdIt last) const;  
    template<class FwdIt>  
        string_type transform_primary(FwdIt first, FwdIt last) const;  
    template<class FwdIt>  
        char_class_type lookup_classname(FwdIt first, FwdIt last) const;  
    template<class FwdIt>  
        string_type lookup_collatename(FwdIt first, FwdIt last) const;  
    bool isctype(char_type ch, char_class_type cls) const;  
    int value(Elem ch, int base) const;  
    locale_type imbue(locale_type loc);  
    locale_type getloc() const;  
  
    typedef Elem char_type;  
    typedef T6 size_type;  
    typedef basic_string<Elem> string_type;  
    typedef T7 locale_type;  
    typedef T8 char_class_type;  
    };  
```  
  
#### 参数  
 `Elem`  
 要描述的元素类型。  
  
## 备注  
 此模板类描述 `Elem` 类型的各种正则表达式特征。 此模板类 [basic\_regex 类](../standard-library/basic-regex-class.md) 使用此信息来操作 `Elem` 类型的元素。  
  
 每个 `regex_traits` 对象包含 `regex_traits::locale` 类型的对象，该对象由它的一些成员函数使用。 默认区域设置是一份 `regex_traits::locale()` 副本。 成员函数 `imbue` 替换区域设置对象，而成员函数 `getloc` 返回区域设置对象的副本。  
  
## 要求  
 **标头：**\<regex\>  
  
 **命名空间：**std  
  
## 请参阅  
 [\<regex\>](../standard-library/regex.md)   
 [regex\_traits](../standard-library/regex-traits-class.md)   
 [regex\_traits \< char \> 类](../standard-library/regex-traits-char-class.md)   
 [regex\_traits\<wchar\_t\> 类](../standard-library/regex-traits-wchar-t-class.md)
---
title: "regex_error 类 | Microsoft Docs"
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
  - "std::tr1::regex_error"
  - "regex_error"
  - "std.tr1.regex_error"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "regex_error 类 [TR1]"
ms.assetid: 3333a1a3-ca6f-4612-84b2-1b4c7e3db5a4
caps.latest.revision: 19
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# regex_error 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

报告错误的 basic\_regex 对象。  
  
## 语法  
  
```  
class regex_error  
    : public std::runtime_error {  
public:  
    explicit regex_error(regex_constants::error_code error);  
    regex_constants::error_code code() const;  
    };  
```  
  
## 备注  
 该类描述一个异常对象，引发该异常的目的是为报告一个构造中的错误或 `basic_regex` 对象的使用错误。  
  
## 要求  
 **标头：**\<regex\>  
  
 **命名空间：**std  
  
## 请参阅  
 [\<regex\>](../standard-library/regex.md)   
 [regex\_error](../standard-library/regex-error-class.md)
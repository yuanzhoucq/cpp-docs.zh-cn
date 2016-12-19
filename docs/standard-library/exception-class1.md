---
title: "exception 类 | Microsoft Docs"
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
  - "std.exception"
  - "exception"
  - "std::exception"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "exception 类"
ms.assetid: 4f181f67-5888-4b50-89a6-745091ffb2fe
caps.latest.revision: 19
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# exception 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

该类用作标准 C\+\+ 库中某些表达式抛出的所有异常的基类。  
  
## 语法  
  
```  
class exception {  
public:  
    exception();  
    exception(const char * const &message);  
    exception(const char * const &message, int);  
    exception(const exception &right);  
    exception& operator=(const exception &right);  
    virtual ~exception();  
    virtual const char *what() const;  
};  
```  
  
## 备注  
 具体而言，此基类为 [\<stdexcept\>](../standard-library/stdexcept.md)定义的标准异常类的根。  C\# `what` 返回的字符串值由默认构造函数未指定，但能由特定派生类的构造函数定义为实现定义的 C 字符串。  成员函数不引发任何异常。  
  
 `int` 参数使您得以指定不应分配内存。  `int` 的值将忽略。  
  
> [!NOTE]
>  构造函数 `exception(const char * const &message)` 和 `exception(const char * const &message, int)` 是 Microsoft 扩展的标准 C\+\+ 库。  
  
## 示例  
 有关从 `exception` 类继承来的标准异常类的示例，请参见 [\<stdexcept\>](../standard-library/stdexcept.md)定义的任何类。  
  
## 要求  
 **标头：** \<exception \>  
  
 **命名空间:**  std  
  
## 请参阅  
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
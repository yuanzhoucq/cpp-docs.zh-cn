---
title: "filesystem_error 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "filesystem/std::tr2::sys::filesystem_error"
dev_langs: 
  - "C++"
ms.assetid: c53aac27-c1fa-43e4-8967-48ea8ba1f172
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# filesystem_error 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

所引发以报告低级系统溢出的全部异常的基类。  
  
## 语法  
  
```  
class filesystem_error    : public system_error;  
```  
  
## 备注  
 此类用作引发报告 \<filesystem\> 函数中所有异常的基类。 它存储类型为 string 的对象，出于阐释目的将其称为 mymesg。 它还存储两个 path 类型的对象，称为 mypval1 和 mypval2。  
  
## filesystem\_error::filesystem\_error  
  
```  
filesystem_error(const string& what_arg, error_code ec);  
filesystem_error(const string& what_arg,  
    const path& pval1, error_code ec);  
filesystem_error(const string& what_arg,  
    const path& pval1, const path& pval2, error_code ec);  
```  
  
 第一个构造函数从 what\_arg 和 ec 构造其消息。 第二个构造函数从 pval1（存储在 mypval1 中）构造其消息。 第三个构造函数从 pval1（存储在 mypval1）和 pval2（存储在 mypval2 中）构造其消息。  
  
## filesystem\_error::path1  
  
```  
const path& path1() const noexcept;  
  
```  
  
 此成员函数返回 mypval1  
  
## filesystem\_error::path2  
  
```  
const path& path2() const noexcept;  
  
```  
  
 此成员函数返回 mypval2  
  
## filesystem\_error::what  
  
```  
const char *what() const noexcept;  
```  
  
 此成员函数返回指向 NTBS 的指针，最好是由 runtime\_error::what\(\)、system\_error::what\(\)、mymesg、mypval1.native\_string\(\) 和 mypval2.native\_string\(\) 组成。  
  
## 要求  
 **标头：**filesystem  
  
 **命名空间：**std::tr2::sys  
  
## 请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [system\_error 类](../standard-library/system-error-class.md)   
 [\<filesystem\>](../standard-library/filesystem.md)   
 [\<exception\>](../standard-library/exception.md)
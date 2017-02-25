---
title: "file_status 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "filesystem/std::tr2::sys::file_status"
  - "filesystem/std::tr2::sys::file_status::perms"
  - "filesystem/std::tr2::sys::file_status::type"
dev_langs: 
  - "C++"
ms.assetid: 9781840e-ad22-44dd-ad79-0fabaa94bac4
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# file_status 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

包装 [file\_type](../Topic/file_type%20Enumeration.md)。  
  
## 语法  
  
```  
class file_status;  
```  
  
## file\_status::file\_status  
  
```  
explicit file_status(file_type ftype = file_type::none,    perms mask = perms::unknown) noexcept;file_status(const file_status&) noexcept = default;file_status(file_status&&) noexcept = default;  
```  
  
## file\_status::operator\=  
  
```  
file_status& operator=(const file_status&) noexcept = default;  
file_status& operator=(file_status&&) nexcept = default;  
```  
  
 默认成员赋值运算符的行为符合预期。  
  
## 类型  
  
```  
file_type type() const noexcept  
void type(file_type _Ftype) noexcept  
```  
  
 获取或设置 file\_type。  
  
## 权限  
  
```  
perms permissions() const noexcept  
void permissions(perms_Prms) noexcept   
```  
  
 获取或设置文件权限。  
  
 使用资源库将文件设置为只读，或删除只读特性。  
  
## 要求  
 **标头：**filesystem  
  
 **命名空间：**std::tr2::sys  
  
## 请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [path 类（C\+\+ 标准模板库）](../standard-library/path-class-cpp-standard-template-library.md)   
 [\<filesystem\>](../standard-library/filesystem.md)
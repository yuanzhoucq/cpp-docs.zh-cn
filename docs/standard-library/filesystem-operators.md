---
title: "&lt;文件系统&gt; 运算符 | Microsoft Docs"
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
  - "FILESYSTEM/std::experimental::filesystem::v1::operator=="
  - "std::experimental::filesystem::v1::operator=="
  - "FILESYSTEM/std::experimental::filesystem::v1::operator!="
  - "std::experimental::filesystem::v1::operator!="
  - "FILESYSTEM/std::experimental::filesystem::v1::operator<"
  - "std::experimental::filesystem::v1::operator<"
  - "FILESYSTEM/std::experimental::filesystem::v1::operator<="
  - "std::experimental::filesystem::v1::operator<="
  - "FILESYSTEM/std::experimental::filesystem::v1::operator>"
  - "std::experimental::filesystem::v1::operator>"
  - "FILESYSTEM/std::experimental::filesystem::v1::operator>="
  - "std::experimental::filesystem::v1::operator>="
  - "FILESYSTEM/std::experimental::filesystem::v1::operator/"
  - "std::experimental::filesystem::v1::operator/"
  - "FILESYSTEM/std::experimental::filesystem::v1::operator<<"
  - "std::experimental::filesystem::v1::operator<<"
  - "FILESYSTEM/std::experimental::filesystem::v1::operator>>"
  - "std::experimental::filesystem::v1::operator>>"
dev_langs: 
  - "C++"
ms.assetid: 102c4833-aa3b-41a8-8998-f5003c546bfd
caps.latest.revision: 12
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt;文件系统&gt; 运算符
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

这些运算符将两个路径作为字符串进行词汇比较。 使用**等效**函数来确定两个路径（例如，相对路径和绝对路径）是否指向磁盘上的同一文件或目录。  
  
```  
C:\root > D:\root: false  
C:\root > C:\root\sub: false  
C:\root > C:\roo: true  
  
```  
  
 有关详细信息，请参阅 [文件系统导航 \(C\+\+\)](../standard-library/file-system-navigation.md)。  
  
## operator\=\=  
  
```  
bool operator==(const path& left, const path& right) noexcept;  
```  
  
 函数返回 left.native\(\) \=\= right.native\(\)。  
  
## operator\!\=  
  
```  
bool operator!=(const path& left, const path& right) noexcept;  
```  
  
 函数返回 \!\(left \=\= right\)。  
  
## operator\<  
  
```  
bool operator<(const path& left, const path& right) noexcept;  
```  
  
 函数返回 left.native\(\) \< right.native\(\)。  
  
## operator\<\=  
  
```  
bool operator<=(const path& left, const path& right) noexcept;  
```  
  
 函数返回 \!\(right \< left\)。  
  
## operator\>  
  
```  
bool operator>(const path& left, const path& right) noexcept;  
```  
  
 函数返回 right \< left。  
  
## operator\>\=  
  
```  
bool operator>=(const path& left, const path& right) noexcept;  
```  
  
 函数返回 \!\(left \< right\)。  
  
## operator\/  
  
```  
path operator/(const path& left, const path& right);  
```  
  
 函数执行：  
  
```  
basic_string<Elem, Traits> str;  
path ans = left;  
return (ans /= right);  
  
```  
  
## operator\<\<  
  
```  
template<class Elem, class Traits>    basic_ostream<Elem, Traits>&    operator<<(basic_ostream<Elem, Traits>& os, const path& pval);  
```  
  
 函数返回 os \<\< pval.string\<Elem, Traits\>\(\)。  
  
## operator\>\>  
  
```  
template<class Elem, class Traits>    basic_istream<Elem, Traits>&    operator<<(basic_istream<Elem, Traits>& is, const path& pval);  
```  
  
 函数执行：  
  
```  
basic_string<Elem, Traits> str;  
is >> str;  
pval = str;  
return (is);  
  
```  
  
## operator\=\=  
  
```  
bool operator==(const path& left, const path& right) noexcept;  
```  
  
 函数返回 left.native\(\) \=\= right.native\(\)。  
  
## 请参阅  
 [path 类（C\+\+ 标准模板库）](../standard-library/path-class-cpp-standard-template-library.md)   
 [文件系统导航 \(C\+\+\)](../standard-library/file-system-navigation.md)   
 [\<filesystem\>](../standard-library/filesystem.md)
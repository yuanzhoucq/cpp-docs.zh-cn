---
title: "directory_iterator 类 | Microsoft Docs"
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
  - "filesystem/std::tr2::sys::directory_iterator"
  - "directory_iterator"
  - "filesystem/std::experimental::filesystem::v1::_Directory_iterator::_Directory_iterator"
  - "filesystem/std::experimental::filesystem::v1::directory_iterator"
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_iterator::directory_iterator"
  - "std::experimental::filesystem::v1::directory_iterator::directory_iterator"
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_iterator::increment"
  - "std::experimental::filesystem::v1::directory_iterator::increment"
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_iterator::operator="
  - "std::experimental::filesystem::v1::directory_iterator::operator="
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_iterator::operator=="
  - "std::experimental::filesystem::v1::directory_iterator::operator=="
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_iterator::operator!="
  - "std::experimental::filesystem::v1::directory_iterator::operator!="
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_iterator::operator*"
  - "std::experimental::filesystem::v1::directory_iterator::operator*"
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_iterator::operator->"
  - "std::experimental::filesystem::v1::directory_iterator::operator->"
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_iterator::operator++"
  - "std::experimental::filesystem::v1::directory_iterator::operator++"
dev_langs: 
  - "C++"
ms.assetid: dca2ecf8-3e69-4644-a83d-705061e10cc8
caps.latest.revision: 19
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# directory_iterator 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述通过目录中的文件名排序的输入迭代器。 对于迭代器 X，表达式 \*X 计算到 directory\_entry 类对文件名及与其状态有关的任何信息进行包装的对象。  
  
 该类存储类型路径的对象（此处出于阐述的目的称为 mydir，它表示要对其进行排序的目录的名称）和类型 directory\_entry 的对象（此处称为 myentry，它表示目录序列中的当前文件名）。 类型 directory\_entry 的默认构造对象具有一个空的 mydir 路径名称并表示序列末迭代器。  
  
 例如，给定具有条目 def 和 ghi 的目录 abc，则代码：  
  
 `for (directory_iterator next(path("abc")), end; next != end; ++next)     visit(next->path());`  
  
 将通过参数路径 \("abc\/def"\) 和路径 \("abc\/ghi"\) 调用访问。  
  
 有关详细信息和代码示例，请参阅 [文件系统导航 \(C\+\+\)](../standard-library/file-system-navigation.md)。  
  
## 语法  
  
```  
class directory_iterator;  
```  
  
## directory\_iterator::directory\_iterator  
  
```cpp  
directory_iterator() noexcept;  
explicit directory_iterator(const path& pval);  
directory_iterator(const path& pval,  
    error_code& ec) noexcept;  
directory_iterator(const directory_iterator&) = default;  
directory_iterator(directory_iterator&&) noexcept = default;  
```  
  
 第一个构造函数将生成序列末迭代器。 第二个和第三个构造函数将 pval 存储在 mydir 中，然后尝试将 mydir 作为目录打开和读取。 如果成功，它们会将目录中的第一个文件名存储在 myentry 中；否则它们将生成序列末迭代器。  
  
 默认构造函数的行为符合预期。  
  
## directory\_iterator::increment  
  
```cpp  
directory_iterator& increment(  
    error_code& ec) noexcept;  
```  
  
 该函数尝试转到目录中的下一个文件名。 如果成功，它会将该文件名存储在 myentry 中；否则它会生成一个序列末迭代器。  
  
## directory\_iterator::operator\!\=  
  
```cpp  
bool operator!=(const directory_iterator& right) const;  
```  
  
 该成员运算符返回 \!\(\*this \=\= right\)。  
  
## directory\_iterator::operator\=  
  
```cpp  
directory_iterator& operator=(const directory_iterator&) = default;  
directory_iterator& operator=(directory_iterator&&) noexcept = default;  
```  
  
 默认成员赋值运算符的行为符合预期。  
  
## directory\_iterator::operator\=\=  
  
```cpp  
bool operator==(const directory_iterator& right) const;  
  
```  
  
 仅当 \*this 和 right 均为序列末迭代器或均不为序列末迭代器时，此成员运算符才返回 true。  
  
## directory\_iterator::operator\*  
  
```cpp  
const directory_entry& operator*() const;  
```  
  
 该成员运算符将返回 myentry。  
  
## directory\_iterator::operator\-\>  
  
```cpp  
const directory_entry *operator->() const;  
```  
  
 此成员函数返回 &\*\*this。  
  
## directory\_iterator::operator\+\+  
  
```cpp  
directory_iterator& operator++();  
directory_iterator& operator++(int);  
```  
  
 第一个成员函数调用 increment\(\)，然后返回 \*this。 第二个成员函数复制该对象，并调用 increment\(\)，然后返回副本。  
  
## 要求  
 **标头：**filesystem  
  
 **命名空间：**std::experimental::filesystem::v1  
  
## 请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [\<filesystem\>](../standard-library/filesystem.md)   
 [文件系统导航 \(C\+\+\)](../standard-library/file-system-navigation.md)
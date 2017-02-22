---
title: "directory_entry 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "filesystem/std::tr2::sys::directory_entry"
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_entry::operator const std::experimental::filesystem::v1::path &"
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_entry::directory_entry"
  - "std::experimental::filesystem::v1::directory_entry::directory_entry"
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_entry::operator="
  - "std::experimental::filesystem::v1::directory_entry::operator="
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_entry::assign"
  - "std::experimental::filesystem::v1::directory_entry::assign"
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_entry::replace_filename"
  - "std::experimental::filesystem::v1::directory_entry::replace_filename"
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_entry::path"
  - "std::experimental::filesystem::v1::directory_entry::path"
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_entry::status"
  - "std::experimental::filesystem::v1::directory_entry::status"
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_entry::symlink_status"
  - "std::experimental::filesystem::v1::directory_entry::symlink_status"
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_entry::operator<"
  - "std::experimental::filesystem::v1::directory_entry::operator<"
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_entry::operator=="
  - "std::experimental::filesystem::v1::directory_entry::operator=="
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_entry::operator!="
  - "std::experimental::filesystem::v1::directory_entry::operator!="
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_entry::operator<="
  - "std::experimental::filesystem::v1::directory_entry::operator<="
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_entry::operator>"
  - "std::experimental::filesystem::v1::directory_entry::operator>"
  - "FILESYSTEM/std::experimental::filesystem::v1::directory_entry::operator>="
  - "std::experimental::filesystem::v1::directory_entry::operator>="
dev_langs: 
  - "C++"
ms.assetid: 1827c67b-4137-4548-adb0-f955f7acaf08
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# directory_entry 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述由 `*X` 返回的对象，其中 *X* 是 [directory\_iterator](../standard-library/directory-iterator-class.md) 或 [recursive\_directory\_iterator](../standard-library/recursive-directory-iterator-class.md)。  
  
## 语法  
  
```  
class directory_entry;  
```  
  
## 备注  
 该类存储类型 [path Class](../standard-library/path-class-cpp-standard-template-library.md) 的对象。`path` 可以是 [path](../standard-library/path-class-cpp-standard-template-library.md)，也可以是派生自 `path` 的类型。 它还存储两个 [file\_type](../Topic/file_type%20Enumeration.md) 值；一个表示有关存储文件名的状态的已知信息，另一个表示有关文件名的符号链接状态的已知信息。  
  
 有关详细信息和代码示例，请参阅 [文件系统导航 \(C\+\+\)](../standard-library/file-system-navigation.md)。  
  
## assign  
  
```  
void assign(const PFX path& pval,  
    file_status stat_arg = file_status(),  
    file_status symstat_arg = file_status());  
```  
  
 成员函数将 pval 分配到 mypath，stat 分配到 mystat，并将 symstat 分配到 mysymstat。  
  
## directory\_entry  
  
```  
directory_entry() = default;  
directory_entry(const directory_entry&) = default;  
directory_entry(directory_entry&&) noexcept = default;  
explicit directory_entry(const PFX path& pval,  
    file_status stat_arg = file_status(),  
    file_status symstat_arg = file_status());  
```  
  
 默认构造函数行为符合预期。 第四个构造函数将 mypath 初始化到 pval，mystat 初始化到 stat\_arg，并将 mysymstat 初始化到 symstat\_arg。  
  
## operator\!\=  
  
```  
bool operator!=(const directory_entry& right) const noexcept;  
  
```  
  
 此成员函数返回 \!\(\*this \=\= right\)。  
  
## operator\=  
  
```  
directory_entry& operator=(const directory_entry&) = default;  
directory_entry& operator=(directory_entry&&) noexcept = default;  
  
```  
  
 默认成员赋值运算符的行为符合预期。  
  
## operator\=\=  
  
```  
bool operator==(const directory_entry& right) const noexcept;  
```  
  
 此成员函数返回 mypath \=\= right.mypath。  
  
## operator\<  
  
```  
  
bool operator<(const directory_entry& right) const noexcept;  
  
```  
  
 此成员函数返回 mypath \< right.mypath。  
  
## operator\<\=  
  
```  
bool operator<=(const directory_entry& right) const noexcept;  
```  
  
 此成员函数返回 \!\(right \< \*this\)。  
  
## operator\>  
  
```  
bool operator>(const directory_entry& right) const noexcept;  
```  
  
 此成员函数返回 right \< \*this。  
  
## operator\>\=  
  
```  
bool operator>=(const directory_entry& right) const noexcept;  
  
```  
  
 此成员函数返回 \!\(\*this \< right\)。  
  
## operator const path\_type&  
  
```  
operator const path&() const; // retained  
```  
  
 该成员运算符将返回 mypath。  
  
## path  
  
```  
const PFX path& path() const noexcept;  
```  
  
 此成员函数返回 mypath。  
  
## replace\_filename  
  
```  
void replace_filename(const PFX path& pval,  
    file_status stat_arg = file_status(),  
    file_status symstat_arg = file_status());  
```  
  
 此成员函数将 mypath 替换为 mypath.parent\_path\(\) \/ pval，mystat 替换为 stat\_arg，并将 mysymstat 替换为 ymstat\_arg  
  
## status  
  
```  
file_status status() const;  
file_status status(  
    error_code& ec) const noexcept;  
Otherwise, mystat = status(mypval).  
  
```  
  
 这两个成员函数均返回第一次可能按如下更改的 mystat：  
  
1.  如果为 status\_known\(mystat\)，则不执行任何操作。  
  
2.  如果为 \!status\_known\(mysymstat\) && \!is\_symlink\(mysymstat\)，则 mystat \= mysymstat。  
  
## symlink\_status  
  
```  
file_status symlink_status() const;  
file_status symlink_status(  
    error_code& ec) const noexcept;  
```  
  
 这两个成员函数均返回第一次可能按如下更改的 mysymstat：如果为 status\_known\(mysymstat\)，则不执行任何操作。 否则为 mysymstat \= symlink\_status\(mypval\)。  
  
## 要求  
 **标头：**filesystem  
  
 **命名空间：**std::tr2::sys  
  
## 请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [\<filesystem\>](../standard-library/filesystem.md)
---
title: "recursive_directory_iterator 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "filesystem/std::tr2::sys::recursive_directory_iterator"
dev_langs: 
  - "C++"
ms.assetid: 79a061bd-5b64-404c-97e8-749c888c2ced
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# recursive_directory_iterator 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述一个输入迭代器，它对目录中的文件名进行排序，可能以递归方式降序到子目录。 对于迭代器 X，表达式 \*X 计算到 directory\_entry 类对文件名及与其状态有关的任何信息进行包装的对象。  
  
 有关详细信息和代码示例，请参阅 [文件系统导航 \(C\+\+\)](../standard-library/file-system-navigation.md)。  
  
## 语法  
  
```  
class recursive_directory_iterator;  
```  
  
## 备注  
 模板类存储以下内容：  
  
1.  类型 stack\<pair\<directory\_iterator, path\>\> 的对象（此处出于阐述目的称为 mystack），它表示待排序的一套目录  
  
2.  directory\_entry 类型的对象（此处称为 myentry），它表示目录序列中的当前文件名  
  
3.  bool 类型对象（此处称为 no\_push），它记录是否禁用以递归方式降序到子目录  
  
4.  directory\_options 类型的对象（此处称为 myoptions），它记录在构造时建立的选项  
  
 默认构造的 recursive\_directory\_entry 类型对象在 mystack.top\(\).first 处具有序列末迭代器并表示该序列末迭代器。例如，给定具有条目 def（一个目录）、def\/ghi 和 jkl 的目录 abc，则该代码：  
  
```  
for (recursive_directory_iterator next(path("abc")), end; next != end; ++next)  
    visit(next->path());  
  
```  
  
 将使用参数 `path("abc/def/ghi") and path("abc/jkl").` 发起访问 可使用以下两种方式，通过目录子树限定排序：  
  
1.  仅当构造值为 directory\_options::follow\_directory\_symlink 的 recursive\_directory\_iterator with a directory\_options 参数时，才会扫描目录符号链接。  
  
2.  如果调用 disable\_recursion\_pending，则不会以递归方式扫描在增量过程中遇到的后续目录。  
  
## recursive\_directory\_iterator::depth  
  
```  
int depth() const;  
```  
  
 返回 mystack.size\(\) \- 1，因此 pval 深度为零。  
  
## recursive\_directory\_iterator::disable\_recursion\_pending  
  
```  
void disable_recursion_pending();  
```  
  
 成员函数在 no\_push 中存储为 true。  
  
## recursive\_directory\_iterator::operator\!\=  
  
```  
bool operator!=(const recursive_directory_iterator& right) const;  
  
```  
  
 该成员运算符返回 \!\(\*this \=\= right\)。  
  
## recursive\_directory\_iterator::operator\=  
  
```  
recursive_directory_iterator& operator=(const recursive_directory_iterator&) = default;  
recursive_directory_iterator& operator=(recursive_directory_iterator&&) noexcept = default;  
  
```  
  
 默认成员赋值运算符的行为符合预期。  
  
## recursive\_directory\_iterator::operator\=\=  
  
```  
bool operator==(const recursive_directory_iterator& right) const;  
```  
  
 仅当 \*this 和 right 均为序列末迭代器或均不为序列末迭代器时，此成员运算符才返回 true。  
  
## recursive\_directory\_iterator::operator\*  
  
```  
const directory_entry& operator*() const;  
  
```  
  
 该成员运算符将返回 myentry。  
  
## recursive\_directory\_iterator::operator\-\>  
  
```  
const directory_entry *operator->() const;  
```  
  
 返回 &\*\*this。  
  
## recursive\_directory\_iterator::operator\+\+  
  
```  
recursive_directory_iterator& operator++();  
recursive_directory_iterator& operator++(int);  
  
```  
  
 第一个成员函数调用 increment\(\)，然后返回 \*this。 第二个成员函数复制该对象，并调用 increment\(\)，然后返回副本。  
  
## recursive\_directory\_iterator::options  
  
```  
directory_options options() const;  
```  
  
 返回 myoptions。  
  
## recursive\_directory\_iterator::pop  
  
```  
void pop();  
```  
  
 如果 depth\(\) \=\= 0，则该对象成为序列末迭代器。 否则，该成员函数将终止当前（最深）目录的扫描，并在下一较浅深度继续扫描。  
  
## recursive\_directory\_iterator::recursion\_pending  
  
```  
bool recursion_pending() const;  
```  
  
 返回 \!no\_push。  
  
## recursive\_directory\_iterator::recursive\_directory\_iterator  
  
```  
recursive_directory_iterator() noexcept;  
explicit recursive_directory_iterator(const path& pval);  
recursive_directory_iterator(const path& pval,  
    error_code& ec) noexcept;  
recursive_directory_iterator(const path& pval,  
    directory_options opts);  
recursive_directory_iterator(const path& pval,  
    directory_options opts,  
    error_code& ec) noexcept;  
recursive_directory_iterator(const recursive_directory_iterator&) = default;  
recursive_directory_iterator(recursive_directory_iterator&&) noexcept = default;  
  
```  
  
 第一个构造函数将生成序列末迭代器。 第二个和第三个构造函数在 myoptions 中的 no\_push and directory\_options::none 中存储为 false，然后尝试将 pval 作为目录打开和读取。 如果成功，则它们将初始化 mystack 和 myentry 以指定嵌套序列中的第一个非目录文件名；否则它们将生成一个序列末迭代器。  
  
 第四个和第五个构造函数的行为与第二个和第三个类似，只不过它们首先将 opt 存储在 myoptions 中。 默认构造函数的行为符合预期。  
  
## recursive\_directory\_iterator::increment  
  
```  
recursive_directory_iterator& increment(  
    error_code& ec) noexcept;  
```  
  
 该函数尝试推进到嵌套序列中的下一个文件名。 如果成功，它会将该文件名存储在 myentry 中；否则它会生成一个序列末迭代器。  
  
## 要求  
 **标头：**filesystem  
  
 **命名空间：**std::tr2::sys  
  
## 请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [\<filesystem\>](../standard-library/filesystem.md)   
 [文件系统导航 \(C\+\+\)](../standard-library/file-system-navigation.md)
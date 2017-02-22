---
title: "&lt;filesystem&gt; | Microsoft Docs"
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
  - "filesystem/std::tr2::sys::recursive_directory_iterator"
  - "filesystem/std::tr2::sys::path"
  - "filesystem/std::tr2::sys::filesystem_error"
  - "filesystem/std::tr2::sys::directory_iterator"
  - "<filesystem>"
dev_langs: 
  - "C++"
ms.assetid: 5005753b-46fa-43e1-8d4e-1b38617d3cfd
caps.latest.revision: 27
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 27
---
# &lt;filesystem&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

包含标头 \<filesystem\>，用于访问操作和检索有关路径、文件和目录的信息的类和函数。  
  
## 语法  
  
```cpp  
#include <filesystem>  
using namespace std::tr2::sys;  
```  
  
> [!IMPORTANT]
>  到 C\+\+ 14 为止，\<filesystem\> 标头尚不是 C\+\+ 标准，虽然它预计会在 C\+\+ 17 期限内采用近似其当前形式的形式进行标准化。  
  
 此标头支持两大类主机操作系统（即 Microsoft Windows 和 Posix）之一的文件系统。  
  
 虽然这两种操作系统的大多数功能均相同，但本文档将介绍它们之间存在的差异。 例如：  
  
-   Windows 支持多个根名称，例如 c: 或 \\\\network\_name。 因此文件系统由树林组成，每个树都有其自己的根目录（例如 c:\\ 或 \\\\network\_name\\），且每个树都有其自己的当前目录，用于完善相对路径名（非绝对路径名）。  
  
-   Posix 支持不具有根名称的单个树、单个根目录 \/ 和单个当前目录。  
  
 另一个重要差异是路径名的本机表示方式：  
  
-   Windows 使用以 null 结尾的 wchar\_t 序列，编码为 UTF\-16（每个字符一个或两个元素）。  
  
-   Posix 使用以 null 结尾的 char 序列，编码为 UTF\-8（每个字符一个或多个元素）。  
  
-   类路径的对象以本机形式存储路径名，但支持在此存储形式与多种外部形式之间进行简单转换：  
  
    -   以 null 结尾的 char 序列，编码为操作系统偏好的形式。  
  
    -   以 null 结尾的 char 序列，编码为 UTF\-8。  
  
    -   以 null 结尾的 wchar\_t 序列，编码为操作系统偏好的形式。  
  
    -   以 null 结尾的 char16\_t 序列，编码为 UTF\-16。  
  
    -   以 null 结尾的 char32\_t 序列，编码为 UTF\-32。  
  
 通过使用一个或多个 codecvt facet，按需调节这些表示形式之间的相互转换。 如果未指定特定的区域设置对象，则将从全局区域设置获取这些 facet。  
  
 另一个差别是每个操作系统允许你用于指定文件或目录访问权限的详细信息：  
  
1.  Windows 记录文件是只读还是可写，此属性对于目录没有意义。  
  
2.  Posix 记录文件是否可由所有者、所有者组或任何人读取、写入或执行（若为目录则还记录是否可扫描），以及一些其他权限。  
  
 两个系统的共同点是通过根名称后施加于路径名的结构。 对于路径名 c:\/abc\/xyz\/def.ext：  
  
-   根名称为 c:。  
  
-   根目录为 \/。  
  
-   根路径为 c:\/。  
  
-   相对路径为 abc\/xyz\/def.ext。  
  
-   父路径为 c:\/abc\/xyz。  
  
-   文件名为 def.ext。  
  
-   主干为 def。  
  
-   扩展名为 .ext。  
  
 一个细微的差别是路径名中目录序列之间的**首选分隔符**。 两个操作系统都允许写入正斜杠 \/，但在某些上下文中 Windows 偏好反斜杠 \\。  
  
 最后，路径对象的一项重要功能是，当参数调用的文件名为标头 \<fstream\> 中定义的类所需时，即可使用这些对象。  
  
 有关详细信息和代码示例，请参阅 [文件系统导航 \(C\+\+\)](../standard-library/file-system-navigation.md)。  
  
## 类  
  
|名称|说明|  
|--------|--------|  
|directory\_entry 类|描述由 directory\_iterator 或 recursive\_directory\_iterator 返回并包含相关信息的对象|  
|directory\_iterator 类|描述通过文件系统目录中的文件名排序的输入迭代器。|  
|filesystem\_error 类|所引发以报告低级系统溢出的异常的基类。|  
|path 类|定义一个类，该类存储适合用作文件名的模板类型 `String` 的对象。|  
|recursive\_directory\_iterator 类|描述通过文件系统目录中的文件名排序的输入迭代器。 迭代器还可以降到子目录中。|  
|[file\_status 类](../standard-library/file-status-class.md)|包装 `file_type`。|  
  
## 结构  
  
|名称|说明|  
|--------|--------|  
|[space\_info 结构](../standard-library/space-info-structure.md)|保存有关卷的信息。|  
  
## 函数  
 [\<filesystem\> 函数](../standard-library/filesystem-functions.md)  
  
## 运算符  
 [\<文件系统\> 运算符](../standard-library/filesystem-operators.md)  
  
## 枚举  
  
|名称|说明|  
|--------|--------|  
|[copy\_option 枚举](../Topic/copy_option%20Enumeration%20%3Cfilesystem%3E.md)|如果目标文件已存在，则与 [copy\_file](http://msdn.microsoft.com/zh-cn/4af7a9b0-8861-45ed-b84e-0307f0669d60) 一起使用的枚举将决定行为。|  
|[directory\_options 枚举](../Topic/directory_options%20Enumeration.md)|为目录迭代器指定选项的枚举。|  
|[file\_type 枚举](../Topic/file_type%20Enumeration.md)|文件类型的枚举。|  
|[perms 枚举](../Topic/perms%20Enumeration.md)|用于传达权限和权限选项的位掩码类型|  
  
## 请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)
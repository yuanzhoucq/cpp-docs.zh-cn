---
title: "basic_ifstream 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "basic_ifstream"
  - "fstream/std::basic_ifstream"
  - "std::basic_ifstream"
  - "std.basic_ifstream"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "basic_ifstream 类"
ms.assetid: 366cd9a7-efc4-4b7f-ba10-c8271e47ffcf
caps.latest.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 23
---
# basic_ifstream 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述一个对象，该对象可控制从 [basic\_filebuf](../standard-library/basic-filebuf-class.md)\<`Elem``Tr`\> 类的流缓冲区提取元素和编码对象，其中 `Elem` 类型的元素的字符特征由 `Tr` 类确定。  
  
## 语法  
  
```  
template <class Elem, class Tr = char_traits<Elem> >  
    class basic_ifstream : public basic_istream<Elem, Tr>  
```  
  
#### 参数  
 `Elem`  
 文件缓冲区的基本元素。  
  
 `Tr`  
 文件缓冲区的基本元素的特征（通常是 `char_traits`\<`Elem`\>）。  
  
## 备注  
 该对象存储 `basic_filebuf`\<`Elem`, `Tr`\> 类的对象。  
  
## 示例  
 下面的示例说明了如何读取文件中的文本。  
  
```  
// basic_ifstream_class.cpp  
// compile with: /EHsc  
  
#include <fstream>  
#include <iostream>  
  
using namespace std;  
  
int main(int argc, char **argv)  
{  
    ifstream ifs("basic_ifstream_class.txt");  
    if (!ifs.bad())  
    {  
        // Dump the contents of the file to cout.  
        cout << ifs.rdbuf();  
        ifs.close();  
    }  
}  
```  
  
## Input: basic\_ifstream\_class.txt  
  
```  
This is the contents of basic_ifstream_class.txt.  
```  
  
## 输出  
  
```  
This is the contents of basic_ifstream_class.txt.  
```  
  
### 构造函数  
  
|||  
|-|-|  
|[basic\_ifstream](../Topic/basic_ifstream::basic_ifstream.md)|初始化 `basic_ifstream` 对象的新实例。|  
  
### 成员函数  
  
|||  
|-|-|  
|[关闭](../Topic/basic_ifstream::close.md)|关闭文件。|  
|[is\_open](../Topic/basic_ifstream::is_open.md)|确定文件是否打开。|  
|[打开](../Topic/basic_ifstream::open.md)|打开文件。|  
|[rdbuf](../Topic/basic_ifstream::rdbuf.md)|返回存储的流缓冲区的地址。|  
|[swap](../Topic/basic_ifstream::swap.md)|为所提供 `basic_ifstream` 的内容交换此 `basic_ifstream` 的内容。|  
  
### 运算符  
  
|||  
|-|-|  
|[operator \=](../Topic/basic_ifstream::operator=.md)|分配此流对象的内容。  这是一种移动赋值，所涉及的 `rvalue` 不会留下副本。|  
  
## 要求  
 **标头：**\<fstream\>  
  
 **命名空间:** std  
  
## 请参阅  
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 编程](../standard-library/iostream-programming.md)   
 [iostreams 约定](../standard-library/iostreams-conventions.md)
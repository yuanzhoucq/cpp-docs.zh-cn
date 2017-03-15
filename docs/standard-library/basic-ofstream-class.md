---
title: "basic_ofstream 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::basic_ofstream"
  - "basic_ofstream"
  - "std.basic_ofstream"
  - "fstream/std::basic_ofstream"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "basic_ofstream 类"
ms.assetid: 3bcc9c51-6dfc-4844-8fcc-22ef57c9dff1
caps.latest.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 24
---
# basic_ofstream 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述一个对象，该对象可控制将元素和编码对象插入 [basic\_filebuf](../standard-library/basic-filebuf-class.md)\<`Elem`, `Tr`\> 类的流缓冲区，其中 `Elem` 类型的元素的字符特征由 `Tr` 类确定。  
  
## 语法  
  
```  
template <class Elem, class Tr = char_traits<Elem> >  
    class basic_ofstream : public basic_ostream<Elem, Tr>  
```  
  
#### 参数  
 `Elem`  
 文件缓冲区的基本元素。  
  
 `Tr`  
 文件缓冲区的基本元素的特征（通常是 `char_traits`\<`Elem`\>）。  
  
## 备注  
 当将 `basic_ofstream` 的 `wchar_t` 专用化写入文件时，如果在文本模式下打开该文件，则它将编写 MBCS 序列。  内部表示形式将使用 `wchar_t` 字符的缓冲区。  
  
 该对象存储 `basic_filebuf`\<`Elem`, `Tr`\> 类的对象。  
  
## 示例  
 下面的示例演示了如何创建 `basic_ofstream` 对象和向其写入文本。  
  
```  
// basic_ofstream_class.cpp  
// compile with: /EHsc  
#include <fstream>  
  
using namespace std;  
  
int main(int argc, char **argv)  
{  
    ofstream ofs("ofstream.txt");  
    if (!ofs.bad())  
    {  
        ofs << "Writing to a basic_ofstream object..." << endl;  
        ofs.close();  
    }  
}  
```  
  
### 构造函数  
  
|||  
|-|-|  
|[basic\_ofstream](../Topic/basic_ofstream::basic_ofstream.md)|创建 `basic_ofstream` 类型的对象。|  
  
### 成员函数  
  
|||  
|-|-|  
|[关闭](../Topic/basic_ofstream::close.md)|关闭文件。|  
|[is\_open](../Topic/basic_ofstream::is_open.md)|确定文件是否打开。|  
|[打开](../Topic/basic_ofstream::open.md)|打开文件。|  
|[rdbuf](../Topic/basic_ofstream::rdbuf.md)|返回存储的流缓冲区的地址。|  
|[swap](../Topic/basic_ofstream::swap.md)|将此 `basic_ofstream` 的内容与提供的 `basic_ofstream` 的内容进行交换。|  
  
### 运算符  
  
|||  
|-|-|  
|[operator \=](../Topic/basic_ofstream::operator=.md)|分配此流对象的内容。  这是一种移动赋值，所涉及的 `rvalue reference` 不会留下副本。|  
  
## 要求  
 **标头：**\<fstream\>  
  
 **命名空间:** std  
  
## 请参阅  
 [basic\_ostream 类](../standard-library/basic-ostream-class.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 编程](../standard-library/iostream-programming.md)   
 [iostreams 约定](../standard-library/iostreams-conventions.md)
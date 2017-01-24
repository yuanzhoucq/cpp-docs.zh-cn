---
title: "basic_fstream 类 | Microsoft Docs"
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
  - "std::basic_fstream"
  - "basic_fstream"
  - "fstream/std::basic_fstream"
  - "std.basic_fstream"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "basic_fstream 类"
ms.assetid: 8473817e-42a4-430b-82b8-b476c86bcf8a
caps.latest.revision: 24
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# basic_fstream 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述一个对象，该对象使用类 [basic\_filebuf](../standard-library/basic-filebuf-class.md)\<`Elem`, `Tr`\> 的流缓冲区来控制元素和编码对象的插入和提取，该流缓冲区具有 `Elem` 类型的元素，其字符特征由类 `Tr` 确定。  
  
## 语法  
  
```  
template <class Elem, class Tr = char_traits<Elem> >  
    class basic_fstream : public basic_iostream<Elem, Tr>  
```  
  
#### 参数  
 `Elem`  
 文件缓冲区的基本元素。  
  
 `Tr`  
 文件缓冲区的基本元素的特征（通常是 `char_traits`\<`Elem`\>）。  
  
## 备注  
 该对象存储 `basic_filebuf`\<`Elem`, `Tr`\> 类的对象。  
  
> [!NOTE]
>  fstream 对象的 get 指针和 put 指针**不**相互独立。  如果 get 指针移动，put 指针也将移动。  
  
## 示例  
 下面的示例演示如何创建能够对其进行读取和写入的 `basic_fstream` 对象。  
  
```  
// basic_fstream_class.cpp  
// compile with: /EHsc  
  
#include <fstream>  
#include <iostream>  
  
using namespace std;  
  
int main(int argc, char **argv)  
{  
    fstream fs("fstream.txt", ios::in | ios::out | ios::trunc);  
    if (!fs.bad())  
    {  
        // Write to the file.  
        fs << "Writing to a basic_fstream object..." << endl;  
        fs.close();  
  
        // Dump the contents of the file to cout.  
        fs.open("fstream.txt", ios::in);  
        cout << fs.rdbuf();  
        fs.close();  
    }  
}  
```  
  
  **正在写入 basic\_fstream 对象...**   
### 构造函数  
  
|||  
|-|-|  
|[basic\_fstream](../Topic/basic_fstream::basic_fstream.md)|构造 `basic_fstream` 类型的对象。|  
  
### 成员函数  
  
|||  
|-|-|  
|[关闭](../Topic/basic_fstream::close.md)|关闭文件。|  
|[is\_open](../Topic/basic_fstream::is_open.md)|确定文件是否打开。|  
|[打开](../Topic/basic_fstream::open.md)|打开文件。|  
|[rdbuf](../Topic/basic_fstream::rdbuf.md)|将指针类型的已存储流缓冲区的地址返回到 [basic\_filebuf](../standard-library/basic-filebuf-class.md)\<`Elem`, `Tr`\>。|  
|[swap](../Topic/basic_fstream::swap.md)|将此对象的内容与另一个 `basic_fstream` 对象的内容进行交换。|  
  
## 要求  
 **标头：**\<fstream\>  
  
 **命名空间:** std  
  
## 请参阅  
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 编程](../standard-library/iostream-programming.md)   
 [iostreams 约定](../standard-library/iostreams-conventions.md)
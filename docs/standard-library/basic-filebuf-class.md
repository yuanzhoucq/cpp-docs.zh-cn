---
title: "basic_filebuf 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.basic_filebuf"
  - "fstream/std::basic_filebuf"
  - "std::basic_filebuf"
  - "basic_filebuf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "basic_filebuf 类"
ms.assetid: 3196ba5c-bf38-41bd-9a95-70323ddfca1a
caps.latest.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 24
---
# basic_filebuf 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述对 `Elem` 类型的元素（其字符特征由类 `Tr` 确定）与外部文件中存储的元素序列之间的来回传输进行控制的流缓冲区。  
  
## 语法  
  
```  
template <class Elem, class Tr = char_traits<Elem> >  
    class basic_filebuf : public basic_streambuf<Elem, Tr>  
```  
  
#### 参数  
 `Elem`  
 文件缓冲区的基本元素。  
  
 `Tr`  
 文件缓冲区的基本元素的特征（通常是 `char_traits`\<`Elem`\>）。  
  
## 备注  
 该模板类描述对 `Elem` 类型的元素（其字符特征由类 `Tr` 确定）与外部文件中存储的元素序列之间的来回传输进行控制的流缓冲区。  
  
> [!NOTE]
>  `basic_filebuf` 类型的对象使用 `char *` 类型的内部缓冲区创建（不考虑由类型参数 `Elem` 指定的 `char_type`）。  这意味着，Unicode 字符串（包含 `wchar_t` 字符）会在写入内部缓冲区之前转换为 ANSI 字符串（包含 `char` 字符）。  若要在缓冲区中存储 Unicode 字符串，请创建 `wchar_t` 类型的新缓冲区，并使用 [basic\_streambuf::pubsetbuf](../Topic/basic_streambuf::pubsetbuf.md)`()` 方法设置它。  若要查看演示此行为的示例，请参阅下面的内容。  
  
 类 `basic_filebuf`\<`Elem`, `Tr`\> 的对象会存储文件指针，它指定的 `FILE` 对象控制与打开的文件关联的流。  它还存储指向两个文件转换方面的指针，以供受保护的成员函数 [overflow](../Topic/basic_filebuf::overflow.md) 和 [underflow](../Topic/basic_filebuf::underflow.md) 使用。  有关详细信息，请参阅 [basic\_filebuf::open](../Topic/basic_filebuf::open.md)。  
  
## 示例  
 下面的示例演示如何通过调用 `pubsetbuf()` 方法来强制 `basic_filebuf<wchar_t>` 类型的对象将 Unicode 字符存储在其内部缓冲区中。  
  
```  
// unicode_basic_filebuf.cpp  
// compile with: /EHsc  
  
#include <iostream>  
#include <string>  
#include <fstream>  
#include <iomanip>  
#include <memory.h>  
#include <string.h>  
  
#define IBUFSIZE 16  
  
using namespace std;  
  
void hexdump(const string& filename);  
  
int main()  
{  
    wchar_t* wszHello = L"Hello World";  
    wchar_t wBuffer[128];  
  
    basic_filebuf<wchar_t> wOutFile;  
  
    // Open a file, wcHello.txt, then write to it, then dump the  
    // file's contents in hex  
    wOutFile.open("wcHello.txt",  
        ios_base::out | ios_base::trunc | ios_base::binary);  
    if(!wOutFile.is_open())  
    {  
        cout << "Error Opening wcHello.txt\n";  
        return -1;  
    }  
    wOutFile.sputn(wszHello, (streamsize)wcslen(wszHello));  
    wOutFile.close();  
    cout << "Hex Dump of wcHello.txt - note that output is ANSI chars:\n";  
    hexdump(string("wcHello.txt"));  
  
    // Open a file, wwHello.txt, then set the internal buffer of  
    // the basic_filebuf object to be of type wchar_t, then write  
    // to the file and dump the file's contents in hex  
    wOutFile.open("wwHello.txt",  
        ios_base::out | ios_base::trunc | ios_base::binary);  
    if(!wOutFile.is_open())  
    {  
        cout << "Error Opening wwHello.txt\n";  
        return -1;  
    }  
    wOutFile.pubsetbuf(wBuffer, (streamsize)128);  
    wOutFile.sputn(wszHello, (streamsize)wcslen(wszHello));  
    wOutFile.close();  
    cout << "\nHex Dump of wwHello.txt - note that output is wchar_t chars:\n";  
    hexdump(string("wwHello.txt"));  
  
    return 0;  
}  
  
// dump contents of filename to stdout in hex  
void hexdump(const string& filename)  
{  
    fstream ifile(filename.c_str(),  
        ios_base::in | ios_base::binary);  
    char *ibuff = new char[IBUFSIZE];  
    char *obuff = new char[(IBUFSIZE*2)+1];  
    int i;  
  
    if(!ifile.is_open())  
    {  
        cout << "Cannot Open " << filename.c_str()  
             << " for reading\n";  
        return;  
    }  
    if(!ibuff || !obuff)  
    {  
        cout << "Cannot Allocate buffers\n";  
        ifile.close();  
        return;  
    }  
  
    while(!ifile.eof())  
    {  
        memset(obuff,0,(IBUFSIZE*2)+1);  
        memset(ibuff,0,IBUFSIZE);  
        ifile.read(ibuff,IBUFSIZE);  
  
        // corner case where file is exactly a multiple of  
        // 16 bytes in length  
        if(ibuff[0] == 0 && ifile.eof())  
            break;  
  
        for(i = 0; i < IBUFSIZE; i++)  
        {  
            if(ibuff[i] >= ' ')  
                obuff[i] = ibuff[i];  
            else  
                obuff[i] = '.';  
  
            cout << setfill('0') << setw(2) << hex  
                 << (int)ibuff[i] << ' ';  
        }  
        cout << "  " << obuff << endl;  
    }  
    ifile.close();  
}  
```  
  
  **wcHello.txt 的十六进制转储 \- 请注意，输出是 ANSI 字符：**  
**48 65 6c 6c 6f 20 57 6f 72 6c 64 00 00 00 00 00   Hello World.....  wwHello.txt 的十六进制转储 \- 请注意，输出是 wchar\_t 字符：**  
**48 00 65 00 6c 00 6c 00 6f 00 20 00 57 00 6f 00   H.e.l.l.o.  .W.o.  72 00 6c 00 64 00 00 00 00 00 00 00 00 00 00 00   r.l.d...........**    
### 构造函数  
  
|||  
|-|-|  
|[basic\_filebuf](../Topic/basic_filebuf::basic_filebuf.md)|构造 `basic_filebuf` 类型的对象。|  
  
### Typedef  
  
|||  
|-|-|  
|[char\_type](../Topic/basic_filebuf::char_type.md)|将类型名与 `Elem` 模板参数关联。|  
|[int\_type](../Topic/basic_filebuf::int_type.md)|使 `basic_filebuf` 范围中的此类型等效于 `Tr` 范围中具有相同名称的类型。|  
|[off\_type](../Topic/basic_filebuf::off_type.md)|使 `basic_filebuf` 范围中的此类型等效于 `Tr` 范围中具有相同名称的类型。|  
|[pos\_type](../Topic/basic_filebuf::pos_type.md)|使 `basic_filebuf` 范围中的此类型等效于 `Tr` 范围中具有相同名称的类型。|  
|[traits\_type](../Topic/basic_filebuf::traits_type.md)|将类型名与 `Tr` 模板参数关联。|  
  
### 成员函数  
  
|||  
|-|-|  
|[关闭](../Topic/basic_filebuf::close.md)|关闭文件。|  
|[is\_open](../Topic/basic_filebuf::is_open.md)|指示文件是否打开。|  
|[打开](../Topic/basic_filebuf::open.md)|打开文件。|  
|[Overflow — 溢出](../Topic/basic_filebuf::overflow.md)|将新字符插入到已满缓冲区时可以调用的受保护虚函数。|  
|[pbackfail](../Topic/basic_filebuf::pbackfail.md)|受保护虚拟成员函数尝试将元素放回到输入流中，随后使它成为当前元素（由下一个指针指向）。|  
|[seekoff](../Topic/basic_filebuf::seekoff.md)|受保护虚拟成员函数尝试更改受控制流的当前位置。|  
|[seekpos](../Topic/basic_filebuf::seekpos.md)|受保护虚拟成员函数尝试更改受控制流的当前位置。|  
|[setbuf](../Topic/basic_filebuf::setbuf.md)|受保护虚拟成员函数执行特定于每个派生流缓冲区的操作。|  
|[Swap](../Topic/basic_filebuf::swap.md)|为提供的 `basic_filebuf` 参数的内容交换此 `basic_filebuf` 的内容。|  
|[sync](../Topic/basic_filebuf::sync.md)|受保护虚函数尝试将受控制流与任何关联的外部流同步。|  
|[uflow](../Topic/basic_streambuf::uflow.md)|受保护虚函数从输入流中提取当前元素。|  
|[underflow](../Topic/basic_filebuf::underflow.md)|受保护虚函数从输入流中提取当前元素。|  
  
## 要求  
 **标头：**\<fstream\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<fstream\>](../standard-library/fstream.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 编程](../standard-library/iostream-programming.md)   
 [iostreams 约定](../standard-library/iostreams-conventions.md)
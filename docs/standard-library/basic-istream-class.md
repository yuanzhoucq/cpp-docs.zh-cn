---
title: "basic_istream 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "basic_istream"
  - "istream/std::basic_istream"
  - "std::basic_istream"
  - "std.basic_istream"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "basic_istream 类"
ms.assetid: c7c27111-de6d-42b4-95a3-a7e65259bf17
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# basic_istream 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述一个对象，它控制从具有类型为 `Elem` 的元素的流缓冲区提取元素和编码对象的操作，其中该类型也称为 [char\_type](../Topic/basic_ios::char_type.md)，其字符特征由类 *Tr*（也称为 [traits\_type](../Topic/basic_ios::traits_type.md)）决定。  
  
## 语法  
  
```  
  
     template <class   
     Elem  
     , class   
     Tr  
      = char  
     _  
     traits<  
     Elem  
     > >  
class basic_istream  
   : virtual public basic_ios<Elem, Tr>  
```  
  
## 备注  
 大多数重载 [operator\>\>](../Topic/basic_istream::operator%3E%3E.md) 的成员函数都是格式化的输入函数。  它们遵循以下模式：  
  
```  
iostate state = goodbit;  
const sentry ok(*this);  
if (ok)  
    {try  
        {<extract elements and convert  
        accumulate flags in state  
        store a successful conversion> }  
    catch (...)  
        {try  
            {setstate(badbit); }  
        catch (...)  
            {}  
        if ((exceptions( ) & badbit) != 0)  
            throw; }}  
setstate(state);  
return (*this);  
```  
  
 许多其他成员函数是未格式化的输入函数。  它们遵循以下模式：  
  
```  
iostate state = goodbit;  
count = 0;    // the value returned by gcount  
const sentry ok(*this, true);  
if (ok)  
    {try  
        {<extract elements and deliver  
        count extracted elements in count  
        accumulate flags in state> }  
    catch (...)  
        {try  
            {setstate(badbit); }  
        catch (...)  
            {}  
        if ((exceptions( ) & badbit) != 0)  
            throw; }}  
setstate(state);  
```  
  
 如果它们在提取元素时遇到文件末尾，两组函数都调用 [setstate](../Topic/basic_ios::setstate.md)\(**eofbit**\)。  
  
 类 `basic_istream`\<`Elem`, *Tr*\> 的对象将存储：  
  
-   类 [basic\_ios](../standard-library/basic-ios-class.md)\<`Elem`, *Tr*\>`.` 的虚拟公共基对象  
  
-   最后一个未格式化的输入操作的提取计数（在之前的代码中被称为**计数**）。  
  
## 示例  
 请参阅 [basic\_ifstream 类](../standard-library/basic-ifstream-class.md)的示例，了解输入流的详细信息。  
  
### 构造函数  
  
|||  
|-|-|  
|[basic\_istream](../Topic/basic_istream::basic_istream.md)|构造 `basic_istream` 类型的对象。|  
  
### 成员函数  
  
|||  
|-|-|  
|[gcount](../Topic/basic_istream::gcount.md)|返回在最后一个未格式化输入期间读取的字符数。|  
|[get](../Topic/basic_istream::get.md)|从输入流中读取一个或多个字符。|  
|[getline](../Topic/basic_istream::getline.md)|从输入流中读取一行。|  
|[忽略](../Topic/basic_istream::ignore.md)|导致从当前读取位置跳过大量元素。|  
|[peek](../Topic/basic_istream::peek.md)|返回要读取的下一字符。|  
|[putback](../Topic/basic_istream::putback.md)|将指定的字符放入流。|  
|[read](../Topic/basic_istream::read.md)|从流中读取指定数目的字符，并将其存储到数组中。|  
|[readsome](../Topic/basic_istream::readsome.md)|仅从缓冲区读取。|  
|[seekg](../Topic/basic_istream::seekg.md)|在流中移动读取位置。|  
|[sentry](../Topic/basic_istream::sentry.md)|嵌套类描述一个其声明构造了格式化和未格式化的输入函数的对象。|  
|[swap](../Topic/basic_istream::swap.md)|将此 `basic_istream` 对象与所提供的 `basic_istream` 对象参数进行交换。|  
|[sync](../Topic/basic_istream::sync.md)|将与流关联的输入设备与流的缓冲区进行同步。|  
|[tellg](../Topic/basic_istream::tellg.md)|报告流中的当前读取位置。|  
|[unget](../Topic/basic_istream::unget.md)|将最近读取的字符放回流中。|  
  
### 运算符  
  
|||  
|-|-|  
|[运算符 \>\>](../Topic/basic_istream::operator%3E%3E.md)|调用输入流上的函数或从输入流中读取格式化数据。|  
|[operator \=](../Topic/basic_istream::operator=.md)|将运算符右侧上的 `basic_istream` 分配给此对象。  这是涉及不会留下副本的 `rvalue` 引用的移动赋值运算符。|  
  
## 要求  
 **标头：**\<istream\>  
  
 **命名空间:** std  
  
## 请参阅  
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 编程](../standard-library/iostream-programming.md)   
 [iostreams 约定](../standard-library/iostreams-conventions.md)
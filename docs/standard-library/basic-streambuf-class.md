---
title: "basic_streambuf 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "basic_streambuf"
  - "streambuf/std::basic_streambuf"
  - "std.basic_streambuf"
  - "std::basic_streambuf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "basic_streambuf 类"
ms.assetid: 136af6c3-13bf-4501-9288-b93da26efac7
caps.latest.revision: 27
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 27
---
# basic_streambuf 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述一个用于派生流缓冲区的抽象基类，该缓冲区控制元素与特定的流表示形式的来回传输。  
  
## 语法  
  
```  
template<class Elem, class Tr = char_traits<Elem> >  
   class basic_streambuf;  
```  
  
#### 参数  
 `Elem`  
 一个 [char\_type](../Topic/basic_streambuf::char_type.md)。  
  
 `Tr`  
 字符 [traits\_type](../Topic/basic_streambuf::traits_type.md)。  
  
## 备注  
 此模板类描述一个用于派生流缓冲区的抽象基类，该缓冲区控制元素与特定的流表示形式的来回传输。  `basic_streambuf` 类的对象有助于控制具有 `Tr` 类型（也称为 [char\_type](../Topic/basic_streambuf::char_type.md)）的元素的流，该类型的字符特征由 [char\_traits](../standard-library/char-traits-struct.md) 类（也称为 [traits\_type](../Topic/basic_streambuf::traits_type.md)）决定。  
  
 从概念上来说，每个流缓冲区控制两个独立的流：一个用于提取（输入），另一个用于插入（输出）。  但是，特定的表示形式可能会导致这些流中的一个或两个不可访问。  通常，它在两个流之间保持有某种关系。  例如，向 [basic\_stringbuf](../standard-library/basic-stringbuf-class.md)\<`Elem`, `Tr`\> 对象的输出流插入的内容，就是之后从其输入流中提取的内容。  当定位 [basic\_filebuf](../standard-library/basic-filebuf-class.md)\<`Elem`, `Tr`\> 对象的一个流时，将同时定位其他流。  
  
 模板类 `basic_streambuf` 的公共接口提供对所有流缓冲区通用但又专用的操作。  受保护的接口提供特定流的表示形式完成其工作所需的操作。  受保护的虚拟成员函数允许你为特定的流表示形式定制派生流缓冲区的行为。  此库中的每个派生流缓冲区描述它如何专用化其受保护虚拟成员函数的行为。  本主题中描述了基类的默认行为，基类通常不执行任何操作。  
  
 剩余的受保护成员函数控制将内容复制到任何存储以及从此类存储中复制内容的操作，这类存储用于缓冲出入流的传输。  例如，输入缓冲区的特征是：  
  
-   [eback](../Topic/basic_streambuf::eback.md)，指向缓冲区的开头的指针。  
  
-   [gptr](../Topic/basic_streambuf::gptr.md)，指向要读取的下一个元素的指针。  
  
-   [egptr](../Topic/basic_streambuf::egptr.md)，刚超出缓冲区末尾的指针。  
  
 同样，输出缓冲区的特征是：  
  
-   [pbase](../Topic/basic_streambuf::pbase.md)，指向缓冲区开头的指针。  
  
-   [pptr](../Topic/basic_streambuf::pptr.md)，指向要写入的下一个元素的指针。  
  
-   [epptr](../Topic/basic_streambuf::epptr.md)，刚超出缓冲区末尾的指针。  
  
 对于任何缓冲区，使用以下协议：  
  
-   如果下一个指针为 null，则不存在缓冲区。  否则，所有三个指针都将指向相同的序列。  可以安全地比较它们的顺序。  
  
-   对于输出缓冲区，如果下一个指针与结束指针相比较小，则可以在下一个指针指定的写入位置处存储元素。  
  
-   对于输入缓冲区，如果下一个指针与结束指针相比较小，则可以在下一个指针指定的读取位置处读取元素。  
  
-   对于输入缓冲区，如果开始指针与下一个指针相比较小，则可以在递减的下一个指针指定的放回位置处放回元素。  
  
 为派生自 `basic_streambuf`\<`Elem``Tr`\> 的类编写的任何受保护虚拟成员函数必须共同协作来维护此协议。  
  
 `basic_streambuf`\<`Elem``Tr`\> 类的对象将存储前面所述的六个指针。  该对象还会将区域设置对象存储于类型 [locale](../standard-library/locale-class.md) 的对象中，以可供派生的流缓冲区使用。  
  
### 构造函数  
  
|||  
|-|-|  
|[basic\_streambuf](../Topic/basic_streambuf::basic_streambuf.md)|构造 `basic_streambuf` 类型的对象。|  
  
### Typedef  
  
|||  
|-|-|  
|[char\_type](../Topic/basic_streambuf::char_type.md)|将类型名与 `Elem` 模板参数关联。|  
|[int\_type](../Topic/basic_streambuf::int_type.md)|将 `basic_streambuf` 范围内的类型名称与 `Elem`模板参数 关联。|  
|[off\_type](../Topic/basic_streambuf::off_type.md)|将 `basic_streambuf` 范围内的类型名称与 `Elem`模板参数 关联。|  
|[pos\_type](../Topic/basic_streambuf::pos_type.md)|将 `basic_streambuf` 范围内的类型名称与 `Elem`模板参数 关联。|  
|[traits\_type](../Topic/basic_streambuf::traits_type.md)|将类型名与 `Tr` 模板参数关联。|  
  
### 成员函数  
  
|||  
|-|-|  
|[eback](../Topic/basic_streambuf::eback.md)|一个受保护的函数，该函数返回指向输入缓冲区开头的指针。|  
|[egptr](../Topic/basic_streambuf::egptr.md)|一个受保护的函数，该函数返回刚超出输入缓冲区末尾的指针。|  
|[epptr](../Topic/basic_streambuf::epptr.md)|一个受保护的函数，该函数返回刚超出输出缓冲区末尾的指针。|  
|[gbump](../Topic/basic_streambuf::gbump.md)|一个受保护的函数，该函数将 `_Count` 添加到输入缓冲区的下一个指针。|  
|[getloc](../Topic/basic_streambuf::getloc.md)|获取 `basic_streambuf` 对象的区域设置。|  
|[gptr](../Topic/basic_streambuf::gptr.md)|一个受保护的函数，该函数返回指向输入缓冲区的下一个元素的指针。|  
|[imbue](../Topic/basic_streambuf::imbue.md)|由 [pubimbue](../Topic/basic_streambuf::pubimbue.md) 调用的受保护虚拟函数。|  
|[in\_avail](../Topic/basic_streambuf::in_avail.md)|返回可随时从缓冲区读取的元素数目。|  
|[Overflow — 溢出](../Topic/basic_streambuf::overflow.md)|将新字符插入到已满缓冲区时可以调用的受保护虚函数。|  
|[pbackfail](../Topic/basic_streambuf::pbackfail.md)|一个受保护虚拟成员函数，该函数尝试将元素放回输入流中，随后使它成为当前元素（由下一个指针指向）。|  
|[pbase](../Topic/basic_streambuf::pbase.md)|一个受保护的函数，该函数返回指向输出缓冲区开头的指针。|  
|[pbump](../Topic/basic_streambuf::pbump.md)|一个受保护的函数，该函数将 `count` 添加到输出缓冲区的下一个指针。|  
|[pptr](../Topic/basic_streambuf::pptr.md)|一个受保护的函数，该函数返回指向输出缓冲区的下一个元素的指针。|  
|[pubimbue](../Topic/basic_streambuf::pubimbue.md)|设置 `basic_streambuf` 对象的区域设置。|  
|[pubseekoff](../Topic/basic_streambuf::pubseekoff.md)|调用 [seekoff](../Topic/basic_streambuf::seekoff.md)，它是在派生类中进行了重写的受保护虚拟函数。|  
|[pubseekpos](../Topic/basic_streambuf::pubseekpos.md)|调用 [seekpos](../Topic/basic_streambuf::seekpos.md)，它是在派生类中进行了重写并且重置了当前指针位置的受保护虚拟函数。|  
|[pubsetbuf](../Topic/basic_streambuf::pubsetbuf.md)|调用 [setbuf](../Topic/basic_streambuf::setbuf.md)，它是在派生类中进行了重写的受保护虚拟函数。|  
|[pubsync](../Topic/basic_streambuf::pubsync.md)|调用 [sync](../Topic/basic_streambuf::sync.md)，它是在派生类中进行了重写并且更新了与此缓冲区关联的外部流的受保护虚拟函数。|  
|[sbumpc](../Topic/basic_streambuf::sbumpc.md)|读取并返回当前元素，从而移动流指针。|  
|[seekoff](../Topic/basic_streambuf::seekoff.md)|受保护虚拟成员函数尝试更改受控制流的当前位置。|  
|[seekpos](../Topic/basic_streambuf::seekpos.md)|受保护虚拟成员函数尝试更改受控制流的当前位置。|  
|[setbuf](../Topic/basic_streambuf::setbuf.md)|受保护虚拟成员函数执行特定于每个派生流缓冲区的操作。|  
|[setg](../Topic/basic_streambuf::setg.md)|一个受保护的函数，该函数将 `_Gbeg` 存储到开始指针，将 `_Gnext` 存储到下一个指针，并将 `_Gend` 存储到输入缓冲区的结束指针。|  
|[setp](../Topic/basic_streambuf::setp.md)|一个受保护的函数，该函数将 `_Pbeg` 存储到开始指针，并将 `_Pend` 存储到输出缓冲区的结束指针。|  
|[sgetc](../Topic/basic_streambuf::sgetc.md)|返回当前元素，但不更改流中的位置。|  
|[sgetn](../Topic/basic_streambuf::sgetn.md)|返回读取的元素数目。|  
|[showmanyc](../Topic/basic_streambuf::showmanyc.md)|一个受保护的虚拟成员函数，该函数返回可以从输入流中提取并确保该程序将不需要无限期等待的字符数计数。|  
|[snextc](../Topic/basic_streambuf::snextc.md)|读取当前元素并返回以下元素。|  
|[sputbackc](../Topic/basic_streambuf::sputbackc.md)|将 `char_type` 放入流中。|  
|[sputc](../Topic/basic_streambuf::sputc.md)|将一个字符放入流中。|  
|[sputn](../Topic/basic_streambuf::sputn.md)|将一个字符串放入流中。|  
|[stossc](../Topic/basic_streambuf::stossc.md)|越过流中的当前元素。|  
|[sungetc](../Topic/basic_streambuf::sungetc.md)|从流中获取字符。|  
|[swap](../Topic/basic_streambuf::swap.md)|将此对象中的值与所提供 `basic_streambuf` 对象参数中的值进行交换。|  
|[sync](../Topic/basic_streambuf::sync.md)|一个受保护的虚拟函数，它尝试将受控流与任何关联的外部流同步。|  
|[uflow](../Topic/basic_streambuf::uflow.md)|一个受保护的虚拟函数，它从输入流中提取当前元素。|  
|[underflow](../Topic/basic_streambuf::underflow.md)|一个受保护的虚拟函数，它从输入流中提取当前元素。|  
|[xsgetn](../Topic/basic_streambuf::xsgetn.md)|一个受保护的虚拟函数，它从输入流中提取元素。|  
|[xsputn](../Topic/basic_streambuf::xsputn.md)|一个受保护的虚拟函数，它将元素插入到输出流中。|  
  
### 运算符  
  
|||  
|-|-|  
|[operator \=](../Topic/basic_streambuf::operator=.md)|从另一个 `basic_streambuf` 对象为此对象赋值。|  
  
## 要求  
 **标头：**\<streambuf\>  
  
 **命名空间:** std  
  
## 请参阅  
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 编程](../standard-library/iostream-programming.md)   
 [iostreams 约定](../standard-library/iostreams-conventions.md)
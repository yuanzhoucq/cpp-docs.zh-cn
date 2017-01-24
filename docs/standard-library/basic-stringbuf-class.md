---
title: "basic_stringbuf 类 | Microsoft Docs"
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
  - "basic_stringbuf"
  - "sstream/std::basic_stringbuf"
  - "std.basic_stringbuf"
  - "std::basic_stringbuf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "basic_stringbuf 类"
ms.assetid: 40c85f9e-42a5-4a65-af5c-23c8e3bf8113
caps.latest.revision: 28
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# basic_stringbuf 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述对 `Elem` 类型的元素（其字符特征由类 `Tr` 确定）与数组对象中存储的元素序列之间的来回传输进行控制的流缓冲区。  
  
## 语法  
  
```  
template <class Elem, class Tr = char_traits<Elem>,   
   class Alloc = allocator<Elem>   
>  
   class basic_stringbuf : public basic_streambuf<Elem, Tr>  
```  
  
#### 参数  
 `Alloc`  
 allocator 类。  
  
 `Elem`  
 字符串的基本元素的类型。  
  
 `Tr`  
 字符串的基本元素上专用的字符特征。  
  
## 备注  
 对象根据需要进行分配、扩展和释放以适应序列中的更改。  
  
 类 basic\_stringbuf\<`Elem`, `Tr`, `Alloc`\> 的对象将来自其构造函数的 `ios_base::`[openmode](../Topic/ios_base::openmode.md) 参数的副本作为其 `stringbuf` 模式 **mode** 进行存储：  
  
-   如果 `mode & ios_base::in` 不是零，则输入缓冲区可以访问。 有关详细信息，请参阅[basic\_streambuf 类](../standard-library/basic-streambuf-class.md)。  
  
-   如果 `mode & ios_base::out` 不是零，则输出缓冲区可以访问。  
  
### 构造函数  
  
|||  
|-|-|  
|[basic\_stringbuf](../Topic/basic_stringbuf::basic_stringbuf.md)|构造 `basic_stringbuf` 类型的对象。|  
  
### Typedef  
  
|||  
|-|-|  
|[allocator\_type](../Topic/basic_stringbuf::allocator_type.md)|类型是模板参数 `Alloc` 的同义词。|  
|[char\_type](../Topic/basic_stringbuf::char_type.md)|将类型名与 `Elem` 模板参数关联。|  
|[int\_type](../Topic/basic_stringbuf::int_type.md)|使 `basic_filebuf` 范围中的此类型等效于 `Tr` 范围中具有相同名称的类型。|  
|[off\_type](../Topic/basic_stringbuf::off_type.md)|使 `basic_filebuf` 范围中的此类型等效于 `Tr` 范围中具有相同名称的类型。|  
|[pos\_type](../Topic/basic_stringbuf::pos_type.md)|使 `basic_filebuf` 范围中的此类型等效于 `Tr` 范围中具有相同名称的类型。|  
|[traits\_type](../Topic/basic_stringbuf::traits_type.md)|将类型名与 `Tr` 模板参数关联。|  
  
### 成员函数  
  
|||  
|-|-|  
|[Overflow — 溢出](../Topic/basic_stringbuf::overflow.md)|将新字符插入到已满缓冲区时可以调用的受保护虚函数。|  
|[pbackfail](../Topic/basic_stringbuf::pbackfail.md)|受保护虚拟成员函数尝试将元素放回到输入缓冲区中，随后使它成为当前元素（由下一个指针指向）。|  
|[seekoff](../Topic/basic_stringbuf::seekoff.md)|受保护虚拟成员函数尝试更改受控制流的当前位置。|  
|[seekpos](../Topic/basic_stringbuf::seekpos.md)|受保护虚拟成员函数尝试更改受控制流的当前位置。|  
|[str](../Topic/basic_stringbuf::str.md)|设置或获取字符串缓冲区中的文本，而无需更改写入位置。|  
|swap||  
|[underflow](../Topic/basic_stringbuf::underflow.md)|从输入流中提取当前元素的受保护虚拟成员函数。|  
  
## 要求  
 **标头：**\<sstream\>  
  
 **命名空间:** std  
  
## 请参阅  
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 编程](../standard-library/iostream-programming.md)   
 [iostreams 约定](../standard-library/iostreams-conventions.md)
---
title: "istreambuf_iterator 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "istreambuf_iterator"
  - "std.istreambuf_iterator"
  - "std::istreambuf_iterator"
  - "streambuf/std::istreambuf_iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "istreambuf_iterator 类"
ms.assetid: 39002da2-61a6-48a5-9d0c-5df8271f6038
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# istreambuf_iterator 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

模板类 istreambuf\_iterator 描述输入迭代器对象，此对象可从输入流缓冲区（通过它存储的对象访问）提取指向 `basic_streambuf`\<**CharType**, **Traits**\> 的类型指针的字符元素。  
  
## 语法  
  
```  
  
      template <   
   class CharType  
   class Traits = char_traits<CharType>  
>  
class istreambuf_iterator  
: public iterator<input_iterator_tag, CharType, typename Traits::off_type, CharType *, CharType&>  
```  
  
#### 参数  
 `CharType`  
 一种类型，此类型表示 istreambuf\_iterator 的字符类型。  
  
 `Traits`  
 一种类型，此类型表示 istreambuf\_iterator 的字符类型。  此参数为可选参数，默认值为 `char_traits`\<*CharType\>*。  
  
## 备注  
 istreambuf\_iterator 类必须满足输入迭代器的要求。  
  
 构造或递增带有非 null 存储指针的 istreambuf\_iterator 类对象后，此对象将有效尝试从关联的输入流提取和存储 **CharType** 类型的对象。  不过，提取可能会延迟到实际取消引用对象或复制对象后进行。  如果提取失败，对象将使用 null 指针有效替换存储指针，从而设置序列末尾指示符。  
  
### 构造函数  
  
|||  
|-|-|  
|[istreambuf\_iterator](../Topic/istreambuf_iterator::istreambuf_iterator.md)|构造初始化为从输入流读取字符的 `istreambuf_iterator`。|  
  
### Typedef  
  
|||  
|-|-|  
|[char\_type](../Topic/istreambuf_iterator::char_type.md)|为 `ostreambuf_iterator` 的字符类型提供的类型。|  
|[int\_type](../Topic/istreambuf_iterator::int_type.md)|为 `istreambuf_iterator` 提供整数类型的类型。|  
|[istream\_type](../Topic/istreambuf_iterator::istream_type.md)|为 `istream_iterator` 的流类型提供的类型。|  
|[streambuf\_type](../Topic/istreambuf_iterator::streambuf_type.md)|为 `istreambuf_iterator` 的流类型提供的类型。|  
|[traits\_type](../Topic/istream_iterator::traits_type.md)|为 `istream_iterator` 的字符特征类型提供的类型。|  
  
### 成员函数  
  
|||  
|-|-|  
|[equal](../Topic/istreambuf_iterator::equal.md)|对于两个输入流缓冲区迭代器是否相等的测试。|  
  
### 运算符  
  
|||  
|-|-|  
|[operator\*](../Topic/istreambuf_iterator::operator*.md)|取消引用运算符将返回流中的下一字符。|  
|[operator\+\+](../Topic/istreambuf_iterator::operator++.md)|返回输入流中的下一字符或者在递增对象前复制对象并返回副本。|  
|[operator\-\>](../Topic/istreambuf_iterator::operator-%3E.md)|返回成员的值（如果有）。|  
  
## 要求  
 **标头：**\<iterator\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [iterator 结构](../standard-library/iterator-struct.md)   
 [\<iterator\>](../standard-library/iterator.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [标准模板库](../misc/standard-template-library.md)
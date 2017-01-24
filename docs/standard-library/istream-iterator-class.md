---
title: "istream_iterator 类 | Microsoft Docs"
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
  - "iterator/std::istream_iterator"
  - "std.istream_iterator"
  - "std::istream_iterator"
  - "istream_iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "istream_iterator 类"
ms.assetid: fb52a8cd-7f71-48d1-b73e-4b064e2a8d16
caps.latest.revision: 18
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# istream_iterator 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述一个输入迭代器对象。  它可以从输入流中提取 `Type` 类的对象，并通过其存储的、指向 `basic_istream`\<`CharType`, `Traits`\> 的 `pointer` 类型对象进行访问。  
  
## 语法  
  
```  
template<class Type,  
    class CharType = char,  
    class Traits = char_traits<CharType>,  
    class Distance = ptrdiff_t,  
> class istream_iterator  
 : public iterator<  
        input_iterator_tag,  
        Type,   
        Distance,   
        const Type *,  
        const Type&  
    >;  
```  
  
#### 参数  
 `Type`  
 要从输入流中提取的对象的类型。  
  
 `CharType`  
 表示 `istream_iterator` 字符类型的类型。  此参数为可选参数，默认值为 `char`。  
  
 `Traits`  
 表示 `istream_iterator` 字符类型的类型。  此参数为可选参数，默认值为 `char_traits`\<`CharType`\>。  
  
 `Distance`  
 表示 `istream_iterator` 差异类型的带符号的整数类型。  此参数为可选参数，默认值为 `ptrdiff_t`。  
  
 构造或递增带有非 null 存储指针的 istream\_iterator 类对象后，此对象将尝试从关联的输入流提取和存储 `Type` 类型的对象。  如果提取失败，对象将使用 null 指针有效替换存储指针，从而设置序列末尾指示符。  
  
### 构造函数  
  
|||  
|-|-|  
|[istream\_iterator](../Topic/istream_iterator::istream_iterator.md)|构造一个流结尾迭代器作为默认的 `istream_iterator`，或作为一个 `istream_iterator`，以便初始化为它开始读取的迭代器流类型。|  
  
### Typedef  
  
|||  
|-|-|  
|[char\_type](../Topic/istream_iterator::char_type.md)|为 `istream_iterator` 的字符类型提供的类型。|  
|[istream\_type](../Topic/istream_iterator::istream_type.md)|为 `istream_iterator` 的流类型提供的类型。|  
|[traits\_type](../Topic/istream_iterator::traits_type.md)|为 `istream_iterator` 的字符特征类型提供的类型。|  
  
### 运算符  
  
|||  
|-|-|  
|[operator\*](../Topic/istream_iterator::operator*.md)|此解引用运算符返回由 `istream_iterator` 定址的、`Type` 类型的存储对象。|  
|[operator\-\>](../Topic/istream_iterator::operator-%3E.md)|返回成员的值（如果有）。|  
|[operator\+\+](../Topic/istream_iterator::operator++.md)|从输入流提取增量对象，或在递增对象之前复制对象并返回副本。|  
  
## 要求  
 **标头：**\<iterator\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [input\_iterator\_tag 结构](../standard-library/input-iterator-tag-struct.md)   
 [iterator 结构](../standard-library/iterator-struct.md)   
 [\<iterator\>](../standard-library/iterator.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [标准模板库](../misc/standard-template-library.md)
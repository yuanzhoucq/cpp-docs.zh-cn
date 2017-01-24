---
title: "ostreambuf_iterator 类 | Microsoft Docs"
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
  - "std.ostreambuf_iterator"
  - "streambuf/std::ostreambuf_iterator"
  - "ostreambuf_iterator"
  - "std::ostreambuf_iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ostreambuf_iterator 类"
ms.assetid: dad1e624-2f45-4e94-8887-a885e95f9071
caps.latest.revision: 16
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ostreambuf_iterator 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

模板类 ostreambuf\_iterator 描述一个输出迭代器对象，该对象使用提取运算符 **\>\>** 将连续的字符元素写入输出流。  `ostreambuf_iterator` 与 [ostream\_iterator 类](../standard-library/ostream-iterator-class.md)迭代器的不同之处在于，要插入输出流的对象类型为字符而不是泛型类型。  
  
## 语法  
  
```  
  
      template <   
   class CharType = char  
   class Traits = char_traits<CharType>  
>  
```  
  
#### 参数  
 `CharType`  
 表示 ostreambuf\_iterator 字符类型的类型。  此参数为可选参数，默认值为 `char`。  
  
 `Traits`  
 表示 ostreambuf\_iterator 字符类型的类型。  此参数为可选参数，默认值为 `char_traits`\<*CharType\>*。  
  
## 备注  
 ostreambuf\_iterator 类必须满足输出迭代器的要求。  可使用 `ostreambuf_iterator` 直接向输出流中写入算法。  此类可提供一种低级别流迭代器，允许访问字符形式的原始（未格式化）I\/O 流，并且能够绕过与高级别流迭代器相关联的缓冲和字符转换。  
  
### 构造函数  
  
|||  
|-|-|  
|[ostreambuf\_iterator](../Topic/ostreambuf_iterator::ostreambuf_iterator.md)|构造一个 `ostreambuf_iterator`，以便经初始化后向输出流写入字符。|  
  
### Typedef  
  
|||  
|-|-|  
|[char\_type](../Topic/ostreambuf_iterator::char_type.md)|为 `ostreambuf_iterator` 的字符类型提供的类型。|  
|[ostream\_type](../Topic/ostreambuf_iterator::ostream_type.md)|为 `ostream_iterator` 的流类型提供的类型。|  
|[streambuf\_type](../Topic/ostreambuf_iterator::streambuf_type.md)|为 `ostreambuf_iterator` 的流类型提供的类型。|  
|[traits\_type](../Topic/ostreambuf_iterator::traits_type.md)|为 `ostream_iterator` 的字符特征类型提供的类型。|  
  
### 成员函数  
  
|||  
|-|-|  
|[failed](../Topic/ostreambuf_iterator::failed.md)|测试插入到输出流缓冲区的操作是否失败。|  
  
### 运算符  
  
|||  
|-|-|  
|[operator\*](../Topic/ostreambuf_iterator::operator*.md)|用于实现输出迭代器表达式 \*`i` \= `x` 的取消引用运算符。|  
|[operator\+\+](../Topic/ostreambuf_iterator::operator++.md)|一种非功能性递增运算符，可向调用该运算之前所处理的同一对象返回 `ostreambuf_iterator`。|  
|[operator\=](../Topic/ostreambuf_iterator::operator=.md)|此运算符会将一个字符插入到关联的流缓冲区。|  
  
## 要求  
 **标头：**\<iterator\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [\<iterator\>](../standard-library/iterator.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [标准模板库](../misc/standard-template-library.md)
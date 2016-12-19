---
title: "ostream_iterator 类 | Microsoft Docs"
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
  - "ostream_iterator"
  - "std.ostream_iterator"
  - "std::ostream_iterator"
  - "iterator/std::ostream_iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ostream_iterator 类"
ms.assetid: 24d842d3-9f45-4bf6-a697-62f5968f5a03
caps.latest.revision: 17
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ostream_iterator 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

模板类 ostream\_iterator 描述一个输出迭代器对象，该对象使用提取**运算符 \<\<** 将连续的元素写入输出流。  
  
## 语法  
  
```  
  
      template <  
   class Type   
   class CharType = char  
   class Traits = char_traits<CharType>  
>  
class ostream_iterator  
```  
  
#### 参数  
 *类型*  
 要插入到输出流的对象的类型。  
  
 `CharType`  
 表示 `ostream_iterator` 字符类型的类型。  此参数为可选参数，默认值为 `char`。  
  
 `Traits`  
 表示 `ostream_iterator` 字符类型的类型。  此参数为可选参数，默认值为 `char_traits`\<*CharType\>*。  
  
 ostream\_iterator 类必须满足对输出迭代器的要求。  可使用 `ostream_iterator` 直接向输出流中写入算法。  
  
### 构造函数  
  
|||  
|-|-|  
|[ostream\_iterator](../Topic/ostream_iterator::ostream_iterator.md)|构造已初始化并限定写入输出流的 `ostream_iterator`。|  
  
### Typedef  
  
|||  
|-|-|  
|[char\_type](../Topic/ostream_iterator::char_type.md)|为 `ostream_iterator` 的字符类型提供的类型。|  
|[ostream\_type](../Topic/ostream_iterator::ostream_type.md)|为 `ostream_iterator` 的流类型提供的类型。|  
|[traits\_type](../Topic/ostream_iterator::traits_type.md)|为 `ostream_iterator` 的字符特征类型提供的类型。|  
  
### 运算符  
  
|||  
|-|-|  
|[operator\*](../Topic/ostream_iterator::operator*.md)|用于实现输出迭代器表达式 \*`i` \= `x` 的取消引用运算符。|  
|[operator\+\+](../Topic/ostream_iterator::operator++.md)|一种非功能性递增运算符，可向调用该运算之前所处理的同一对象返回 `ostream_iterator`。|  
|[operator\=](../Topic/ostream_iterator::operator=.md)|用于实现输出迭代器表达式 \*`i` \= `x` 以写入输出流的赋值运算符。|  
  
## 要求  
 **标头：**\<iterator\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [\<iterator\>](../standard-library/iterator.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [标准模板库](../misc/standard-template-library.md)
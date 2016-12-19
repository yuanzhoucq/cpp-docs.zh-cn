---
title: "basic_iostream 类 | Microsoft Docs"
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
  - "istream/std::basic_iostream"
  - "std.basic_iostream"
  - "basic_iostream"
  - "std::basic_iostream"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "basic_iostream 类"
ms.assetid: 294b680b-eb49-4066-8db2-6d52dac9d6e3
caps.latest.revision: 22
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# basic_iostream 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以完成输入和输出的流类。  
  
## 语法  
  
```  
template <class Elem, class Tr = char_traits<Elem> >  
    class basic_iostream : public basic_istream<Elem, Tr>,  
        public basic_ostream<Elem, Tr>  
{  
public:  
    explicit basic_iostream(basic_streambuf<Elem, Tr> *_Strbuf);  
    virtual ~basic_iostream();  
};  
```  
  
## 备注  
 此模板类描述一个对象，该对象通过其基类 [basic\_ostream](../standard-library/basic-ostream-class.md)\<`Elem`, `Tr`\> 控制插入并通过其基类 [basic\_istream](../standard-library/basic-istream-class.md)\<`Elem`, `Tr`\> 控制提取。  两个对象共享一个公共的虚拟基类 [basic\_ios](../standard-library/basic-ios-class.md)\<`Elem`, `Tr`\>。  他们还管理通用流缓冲区与类型为 `Elem` 的元素，其字符特征由类 `Tr` 确定。  构造函数会通过 `basic_istream`\(**strbuf**\) 和`basic_ostream`\(**strbuf**\) 初始化其基类。  
  
### 构造函数  
  
|||  
|-|-|  
|[basic\_iostream](../Topic/basic_iostream::basic_iostream.md)|创建 `basic_iostream` 对象。|  
  
### 成员函数  
  
|||  
|-|-|  
|[swap](../Topic/basic_iostream::swap.md)|将提供的 `basic_iostream` 对象的内容交换为此对象的内容。|  
  
### 运算符  
  
|||  
|-|-|  
|[operator \=](../Topic/basic_iostream::operator=.md)|将指定的 `basic_iostream` 对象的值分配给此对象。  这是一种移动赋值，所涉及的 `rvalue` 不会留下副本。|  
  
## 要求  
 **标头：**\<istream\>  
  
 **命名空间:** std  
  
## 请参阅  
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 编程](../standard-library/iostream-programming.md)   
 [iostreams 约定](../standard-library/iostreams-conventions.md)
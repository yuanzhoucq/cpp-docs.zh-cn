---
title: "char_traits 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::char_traits"
  - "std.char_traits"
  - "iosfwd/std::char_traits"
  - "char_traits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "char_traits 类"
  - "char_traits 结构"
ms.assetid: 568e59f0-4521-4207-9223-9dcf6a16d620
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# char_traits 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Char\_traits 结构描述与一个字符相关联的特性。  
  
## 语法  
  
```  
template <  
   class CharType  
> struct char_traits;  
```  
  
#### 参数  
 `CharType`  
 元素数据类型。  
  
## 备注  
 模板结构描述类型 **CharType** 的各种字符特征。  模板类 [basic\_string](../standard-library/basic-string-class.md) 以及若干 iostream 模板类（包括 [basic\_ios](../standard-library/basic-ios-class.md)）使用此信息来操作类型为 **CharType** 的元素。  此元素类型不得要求显式构造或析构。  它必须提供带预期语义的默认构造函数、复制构造函数和赋值运算符。  按位复制必须具有与赋值相同的效果。  结构 char\_traits 的任何成员函数均无法引发异常。  
  
### Typedef  
  
|||  
|-|-|  
|[char\_type](../Topic/char_traits::char_type.md)|一种字符类型。|  
|[int\_type](../Topic/char_traits::int_type.md)|一种整数类型，该类型可以表示类型为 `char_type` 的字符或文件尾 \(EOF\) 字符。|  
|[off\_type](../Topic/char_traits::off_type.md)|一种整数类型，该类型可以表示流中两个位置之间的偏移量。|  
|[pos\_type](../Topic/char_traits::pos_type.md)|一种整数类型，该类型可以表示流中的位置。|  
|[state\_type](../Topic/char_traits::state_type.md)|一种类型，该类型表示流中的多字节字符的转换状态。|  
  
### 成员函数  
  
|||  
|-|-|  
|[assign](../Topic/char_traits::assign.md)|将一个字符值分配给另一个。|  
|[compare](../Topic/char_traits::compare.md)|将两个字符串中指定数量的字符进行比较。|  
|[copy](../Topic/char_traits::copy.md)|将指定数量的字符从一个字符串复制到另一个字符串。  已否决。  改为使用 [char\_traits::\_Copy\_s](../Topic/char_traits::_Copy_s.md)。|  
|[\_Copy\_s](../Topic/char_traits::_Copy_s.md)|将指定数量的字符从一个字符串复制到另一个字符串。|  
|[eof](../Topic/char_traits::eof.md)|返回文件尾 \(EOF\) 字符。|  
|[eq](../Topic/char_traits::eq.md)|测试两个 `char_type` 字符是否相等。|  
|[eq\_int\_type](../Topic/char_traits::eq_int_type.md)|测试两个表示为 `int_type` 的字符是否相等。|  
|[find](../Topic/char_traits::find.md)|在字符范围中搜索指定字符的第一个匹配项。|  
|[length](../Topic/char_traits::length.md)|返回字符串的长度。|  
|[lt](../Topic/char_traits::lt.md)|测试一个字符是否小于另一个。|  
|[move](../Topic/char_traits::move.md)|将指定数量的字符从一个字符串复制到另一个字符串，可能会发生重叠。  已否决。  改为使用 [char\_traits::\_Move\_s](../Topic/char_traits::_Move_s.md)。|  
|[\_Move\_s](../Topic/char_traits::_Move_s.md)|将指定数量的字符从一个字符串复制到另一个字符串，可能会发生重叠。|  
|[not\_eof](../Topic/char_traits::not_eof.md)|测试字符是否为文件尾 \(EOF\) 字符。|  
|[to\_char\_type](../Topic/char_traits::to_char_type.md)|将 `int_type` 字符转换为相应的 `char_type` 字符，并返回结果。|  
|[to\_int\_type](../Topic/char_traits::to_int_type.md)|将 `char_type` 字符转换为相应的 `int_type` 字符，并返回结果。|  
  
## 要求  
 **标头：**\<string\>  
  
 **命名空间:** std  
  
## 请参阅  
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
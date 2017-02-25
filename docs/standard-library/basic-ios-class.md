---
title: "basic_ios 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.basic_ios"
  - "ios/std::basic_ios"
  - "basic_ios"
  - "std::basic_ios"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "basic_ios 类"
ms.assetid: 4fdcd8e1-62d2-4611-8a70-1e4f58434007
caps.latest.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 24
---
# basic_ios 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此模板类描述了依赖于模板参数的输入流（属于模板类 [basic\_istream](../standard-library/basic-istream-class.md)）和输出流（属于模板类 [basic\_ostream](../standard-library/basic-ostream-class.md)）通用的存储和成员函数。  （[ios\_base](../standard-library/ios-base-class.md) 类描述不依赖于模板参数的通用内容。） **basic\_ios\<class Elem, class Traits\>** 类的对象帮助控制具有 **Elem** 类型元素的流，其字符特征由 **Traits** 类确定。  
  
## 语法  
  
```  
  
     template <class   
     Elem  
     , class   
     Traits  
     >  
class basic_ios : public ios_base  
```  
  
#### 参数  
 `Elem`  
 一种类型。  
  
 `Traits`  
 `char_traits` 类型的变量。  
  
## 备注  
 **basic\_ios\<class Elem, class Traits\>** 类的对象存储：  
  
-   指向 [basic\_istream](../standard-library/basic-istream-class.md)**\<Elem, Traits\>** 类型的对象的关系指针。  
  
-   指向 [basic\_streambuf](../standard-library/basic-streambuf-class.md)**\<Elem, Traits \>** 类型的对象的流缓冲区指针。  
  
-   [格式设置信息](../standard-library/ios-base-class.md)。  
  
-   [ios\_base](../standard-library/ios-base-class.md) 类型的基对象中的[流状态信息](../standard-library/ios-base-class.md)。  
  
-   `char_type` 类型的对象中的填充字符。  
  
### 构造函数  
  
|||  
|-|-|  
|[basic\_ios](../Topic/basic_ios::basic_ios.md)|构造 `basic_ios` 类。|  
  
### Typedef  
  
|||  
|-|-|  
|[char\_type](../Topic/basic_ios::char_type.md)|模板参数 `Elem` 的同义词。|  
|[int\_type](../Topic/basic_ios::int_type.md)|`Traits::int_type` 的同义词。|  
|[off\_type](../Topic/basic_ios::off_type.md)|`Traits::off_type` 的同义词。|  
|[pos\_type](../Topic/basic_ios::pos_type.md)|`Traits::pos_type` 的同义词。|  
|[traits\_type](../Topic/basic_ios::traits_type.md)|模板参数 `Traits` 的同义词。|  
  
### 成员函数  
  
|||  
|-|-|  
|[bad](../Topic/basic_ios::bad.md)|指示流缓冲区的完整性损失。|  
|[清除](../Topic/basic_ios::clear.md)|清除所有错误标志。|  
|[copyfmt](../Topic/basic_ios::copyfmt.md)|将标志从一个流复制到另一个流。|  
|[eof](../Topic/basic_ios::eof.md)|指示是否已到达流的结尾。|  
|[异常](../Topic/basic_ios::exceptions.md)|指示流将引发哪些异常。|  
|[fail](../Topic/basic_ios::fail.md)|指示从流中提取有效字段失败。|  
|[fill](../Topic/basic_ios::fill.md)|指定或返回在文本宽度小于流宽度时将使用的字符。|  
|[good](../Topic/basic_ios::good.md)|指示流处于良好状态。|  
|[imbue](../Topic/basic_ios::imbue.md)|更改区域设置。|  
|[init](../Topic/basic_ios::init.md)|通过 `basic_ios` 构造函数调用。|  
|[move](../Topic/basic_ios::move.md)|将所有值（指向流缓冲区的指针除外）从参数移动到当前对象。|  
|[narrow](../Topic/basic_ios::narrow.md)|查找给定 `char_type` 的等效字符型。|  
|[rdbuf](../Topic/basic_ios::rdbuf.md)|将流路由到指定缓冲区。|  
|[rdstate](../Topic/basic_ios::rdstate.md)|读取标志的位状态。|  
|[set\_rdbuf](../Topic/basic_ios::set_rdbuf.md)|分配流缓冲区作为此流对象的读取缓冲区。|  
|[setstate](../Topic/basic_ios::setstate.md)|设置其他标志。|  
|[swap](../Topic/basic_ios::swap.md)|将此 `basic_ios` 对象中的值与另一个 `basic_ios` 对象中的值进行交换。  不会交换指向流缓冲区的指针。|  
|[tie](../Topic/basic_ios::tie.md)|确保依次处理流。|  
|[widen](../Topic/basic_ios::widen.md)|查找给定字符型的等效 `char_type`。|  
  
### 运算符  
  
|||  
|-|-|  
|[显式运算符 bool](../Topic/basic_ios::operator%20bool.md)|允许将 `basic_ios` 对象作为作 `bool`。  禁用自动类型转换以防止产生常见的意外副作用。|  
|[运算符 void \*](../Topic/basic_ios::operator%20void%20*.md)|指示流是否仍处于良好状态。|  
|[运算符 \!](../Topic/basic_ios::operator!.md)|指示流是否完好无损。|  
  
## 要求  
 **标头：**\<ios\>  
  
 **命名空间:** std  
  
## 请参阅  
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 编程](../standard-library/iostream-programming.md)   
 [iostreams 约定](../standard-library/iostreams-conventions.md)
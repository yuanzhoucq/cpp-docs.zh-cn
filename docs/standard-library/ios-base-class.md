---
title: "ios_base 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ios_base"
  - "std.ios_base"
  - "std::ios_base"
  - "xiosbase/std::ios_base"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ios_base 类"
ms.assetid: 0f9e0abc-f70f-49bc-aa1f-003859f56cfe
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# ios_base 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此类描述了不依赖模板参数的输入和输出流通用的存储和成员函数。  （模板类 [basic\_ios](../standard-library/basic-ios-class.md) 描述了什么是通用对象以及什么依赖于模板参数。）  
  
 Ios\_base 类的对象存储格式设置信息，其中包括：  
  
-   [fmtflags](../Topic/ios_base::fmtflags.md) 类型的对象中的格式标志。  
  
-   [iostate](../Topic/ios_base::iostate.md) 类型的对象中的异常掩码。  
  
-   `int`  *类型的对象中的字段宽度。*  
  
-   `int` 类型的对象中的显示精度。  
  
-   **locale** 类型的对象中的区域设置对象。  
  
-   两个可扩展数组，包含 **long** 类型的元素和 `void` 指针。  
  
 Ios\_base 类的对象还将流状态信息存储在 [iostate](../Topic/ios_base::iostate.md) 类型的对象和回调堆栈中。  
  
### 构造函数  
  
|||  
|-|-|  
|[ios\_base](../Topic/ios_base::ios_base.md)|构造 `ios_base` 对象。|  
  
### Typedef  
  
|||  
|-|-|  
|[event\_callback](../Topic/ios_base::event_callback.md)|描述传递到 [register\_call](../Topic/ios_base::register_callback.md) 的函数。|  
|[fmtflags](../Topic/ios_base::fmtflags.md)|用于指定输出外观的常数。|  
|[iostate](../Topic/ios_base::iostate.md)|定义描述流状态的常数。|  
|[openmode](../Topic/ios_base::openmode.md)|介绍如何与流进行交互。|  
|[seekdir](../Topic/ios_base::seekdir.md)|指定偏移操作的起始点。|  
  
### 枚举  
  
|||  
|-|-|  
|[事件](../Topic/ios_base::event.md)|指定事件类型。|  
  
### 常量  
  
|||  
|-|-|  
|[adjustfield](../Topic/ios_base::fmtflags.md)|一个定义为 `internal` 的位掩码                      &#124; `left` &#124; `right`.|  
|[app](../Topic/ios_base::openmode.md)|指定先查找到流末尾，再进行每个插入。|  
|[ate](../Topic/ios_base::openmode.md)|指定当首次创建其控制的对象时查找到流末尾。|  
|[badbit](../Topic/ios_base::iostate.md)|记录流缓冲区的完整性损失。|  
|[basefield](../Topic/ios_base::fmtflags.md)|一个定义为 `dec` 的位掩码                      &#124; `hex` &#124; `oct`.|  
|[beg](../Topic/ios_base::seekdir.md)|指定相对于序列的开头进行查找。|  
|[binary](../Topic/ios_base::openmode.md)|指定文件应读取为二进制流，而不是文本流。|  
|[boolalpha](../Topic/ios_base::fmtflags.md)|指定以名称（如 `true` 和`false`）而不是以数字值插入或提取 `bool` 类型的对象。|  
|[cur](../Topic/ios_base::seekdir.md)|指定相对于序列中的当前位置进行查找。|  
|[dec](../Topic/ios_base::fmtflags.md)|指定以十进制格式插入或提取整数值。|  
|[end](../Topic/ios_base::seekdir.md)|指定相对于序列的末尾进行查找。|  
|[eofbit](../Topic/ios_base::iostate.md)|从流中提取时，记录文件尾。|  
|[failbit](../Topic/ios_base::iostate.md)|记录一个从流中提取有效字段失败的操作。|  
|[固定](../Topic/ios_base::fmtflags.md)|指定以定点格式（无指数域）插入浮点值。|  
|[floatfield](../Topic/ios_base::fmtflags.md)|一个定义为 `fixed` 的位掩码                      &#124; `scientific`|  
|[goodbit](../Topic/ios_base::iostate.md)|清除所有状态位。|  
|[hex](../Topic/ios_base::fmtflags.md)|指定以十六进制格式插入或提取整数值。|  
|[in](../Topic/ios_base::openmode.md)|指定从流中提取。|  
|[internal](../Topic/ios_base::fmtflags.md)|通过在生成的数字字段内的某一点插入填充字符，填充字段宽度。|  
|[左](../Topic/ios_base::fmtflags.md)|指定左对齐。|  
|[oct](../Topic/ios_base::fmtflags.md)|指定以八进制格式插入或提取整数值。|  
|[out](../Topic/ios_base::openmode.md)|指定插入到流。|  
|[右](../Topic/ios_base::fmtflags.md)|指定右对齐。|  
|[科学](../Topic/ios_base::fmtflags.md)|指定以科学记数格式（具有一个指数域）插入浮点值。|  
|[showbase](../Topic/ios_base::fmtflags.md)|指定插入一个显示已生成整数字段的基的前缀。|  
|[showpoint](../Topic/ios_base::fmtflags.md)|指定在生成的浮点字段中无条件插入一个小数点。|  
|[showpos](../Topic/ios_base::fmtflags.md)|指定在生成的非负数字段中插入一个加号。|  
|[skipws](../Topic/ios_base::fmtflags.md)|指定在进行某些提取之前，先跳过前导空格。|  
|[trunc](../Topic/ios_base::openmode.md)|指定在创建其控制的对象后，删除现有文件的内容。|  
|[unitbuf](../Topic/ios_base::fmtflags.md)|将导致输出在每次插入后进行刷新。|  
|[全部大写](../Topic/ios_base::fmtflags.md)|指定在某些插入操作中插入小写字母的大写等效项。|  
  
### 成员函数  
  
|||  
|-|-|  
|[失败](../Topic/ios_base::failure.md)|成员类用作 [basic\_ios](../standard-library/basic-ios-class.md) 模板类中的 [clear](../Topic/basic_ios::clear.md) 成员函数引发的所有异常的基类。|  
|[标志](../Topic/ios_base::flags.md)|设置或返回当前的标志设置。|  
|[getloc](../Topic/ios_base::getloc.md)|返回存储的区域设置对象。|  
|[imbue](../Topic/ios_base::imbue.md)|更改区域设置。|  
|[Init](../Topic/ios_base::Init.md)|在构造时创建标准 iostream 对象。|  
|[iword](../Topic/ios_base::iword.md)|分配将存储为 `iword` 的值。|  
|[精度](../Topic/ios_base::precision.md)|指定浮点数中显示的位数。|  
|[pword](../Topic/ios_base::pword.md)|分配将存储为 `pword` 的值。|  
|[register\_callback](../Topic/ios_base::register_callback.md)|指定一个回调函数。|  
|[setf](../Topic/ios_base::setf.md)|设置指定标志。|  
|[sync\_with\_stdio](../Topic/ios_base::sync_with_stdio.md)|确保 iostream 和 C 运行时库操作按照它们在源代码中出现的顺序发生。|  
|[unsetf](../Topic/ios_base::unsetf.md)|将导致指定的标志处于关闭状态。|  
|[宽度](../Topic/ios_base::width.md)|设置输出流的长度。|  
|[xalloc](../Topic/ios_base::xalloc.md)|指定变量应为流的一部分。|  
  
### 运算符  
  
|||  
|-|-|  
|[operator \=](../Topic/ios_base::operator=.md)|`ios_base` 对象的赋值运算符。|  
  
## 要求  
 **标头：**\<ios\>  
  
 **命名空间:** std  
  
## 请参阅  
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 编程](../standard-library/iostream-programming.md)   
 [iostreams 约定](../standard-library/iostreams-conventions.md)
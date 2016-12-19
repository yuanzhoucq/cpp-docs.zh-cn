---
title: "&lt;ios&gt; | Microsoft Docs"
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
  - "std.<ios>"
  - "std::<ios>"
  - "<ios>"
  - "ios/std::<ios>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ios 标头"
ms.assetid: d3d4c161-2f37-4f04-93cc-0a2a89984a9c
caps.latest.revision: 20
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt;ios&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定义作为 iostreams 操作的基础的多种类型和函数。  此标头通常包含在另一 iostream 标头中；很少会直接包含它。  
  
## 语法  
  
```  
  
#include <ios>  
  
```  
  
## 备注  
 一大组函数为操控器。  在 \< ios \> 中声明的操控器可更改存储在其 [ios\_base](../standard-library/ios-base-class.md) 类的参数对象中的值。  其他操控器对由对象（其类型派生自此类）控制的流执行操作，如其中一个模板类 [basic\_istream](../standard-library/basic-istream-class.md) 或 [basic\_ostream](../standard-library/basic-ostream-class.md) 的专用化。  例如，[noskipws](../Topic/noskipws.md)\(**str**\) 清除 **str** 对象中的格式标志 `ios_base::skipws`，它可以是以下类型之一。  
  
 还可以通过将操控器插入到输出流中或从输入流提取操控器对其进行调用，原因是为派生自 `ios_base` 的类提供了专门的插入和提取操作。  例如:  
  
```  
istr >> noskipws;  
```  
  
 调用 [noskipws](../Topic/noskipws.md)\(**istr**\)。  
  
### Typedef  
  
|||  
|-|-|  
|[ios](../Topic/ios.md)|支持旧 iostream 库中的 ios 类。|  
|[streamoff](../Topic/streamoff.md)|支持内部操作。|  
|[streampos](../Topic/streampos.md)|保留缓冲区指针或文件指针的当前位置。|  
|[streamsize](../Topic/streamsize.md)|指定流的大小。|  
|[wios](../Topic/wios.md)|支持旧 iostream 库中的 wios 类。|  
|[wstreampos](../Topic/wstreampos.md)|保留缓冲区指针或文件指针的当前位置。|  
  
### 操控器  
  
|||  
|-|-|  
|[boolalpha](../Topic/boolalpha.md)|指定类型为 [bool](../cpp/bool-cpp.md) 的变量在流中显示为 **true** 或 **false**。|  
|[dec](../Topic/dec.md)|指定以十进制计数法形式显示整数变量。|  
|[defaultfloat](../Topic/%3Cios%3E%20defaultfloat.md)|配置 `ios_base` 对象的标记以使用浮点值的默认显示格式。|  
|[固定](../Topic/fixed.md)|指定浮点数以自动设置小数点表示法显示。|  
|[hex](../Topic/hex.md)|指定以十六进制计数法形式显示整数变量。|  
|[internal](../Topic/internal%20\(Standard%20C++%20Library\).md)|导致数字的符号左对齐，数字右对齐。|  
|[左](../Topic/left.md)|导致宽度比输出宽度短的文本在流刷新过程中显示时带有左边距。|  
|[noboolalpha](../Topic/noboolalpha.md)|指定类型为 [bool](../cpp/bool-cpp.md) 的变量在流中显示为 1 或 0。|  
|[noshowbase](../Topic/noshowbase.md)|关闭显示数字所采用的进制的指示。|  
|[noshowpoint](../Topic/noshowpoint.md)|仅显示浮点数（其小数部分为零）的整数部分。|  
|[noshowpos](../Topic/noshowpos.md)|导致正数不显式带有符号。|  
|[noskipws](../Topic/noskipws.md)|导致输入流读取空格。|  
|[nounitbuf](../Topic/nounitbuf.md)|导致缓冲区已满时缓冲和处理输出。|  
|[nouppercase](../Topic/nouppercase.md)|指定十六进制数字和科学计数法形式的指数以小写形式显示。|  
|[oct](../Topic/oct%20\(%3Cios%3E\).md)|指定以八进制计数法形式显示整数变量。|  
|[右](../Topic/right.md)|导致宽度比输出宽度短的文本在流刷新过程中显示时带有右边距。|  
|[科学](../Topic/scientific.md)|导致使用科学表示法显示浮点数。|  
|[showbase](../Topic/showbase.md)|指示显示数字所采用的进制。|  
|[showpoint](../Topic/showpoint.md)|显示浮点数的整数部分和小数点右侧的数字，即使小数部分为零。|  
|[showpos](../Topic/showpos.md)|导致正数显式带有符号。|  
|[skipws](../Topic/skipws.md)|导致输入流不读取空格。|  
|[unitbuf](../Topic/unitbuf.md)|导致在缓冲区未满时处理输出。|  
|[全部大写](../Topic/uppercase.md)|指定十六进制数字和科学计数法形式的指数以大写形式显示。|  
  
### 类  
  
|||  
|-|-|  
|[basic\_ios](../standard-library/basic-ios-class.md)|此模板类描述了依赖于模板参数的输入流（属于模板类 [basic\_istream](../standard-library/basic-istream-class.md)）和输出流（属于模板类 [basic\_ostream](../standard-library/basic-ostream-class.md)）通用的存储和成员函数。|  
|[fpos](../standard-library/fpos-class.md)|此模板类描述了一个对象，该对象可存储还原任何流内的任意文件位置指示器所需的所有信息。|  
|[ios\_base](../standard-library/ios-base-class.md)|此类描述了不依赖模板参数的输入和输出流通用的存储和成员函数。|  
  
## 请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 编程](../standard-library/iostream-programming.md)   
 [iostreams 约定](../standard-library/iostreams-conventions.md)
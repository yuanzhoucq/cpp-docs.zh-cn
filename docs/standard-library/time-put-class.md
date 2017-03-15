---
title: "time_put 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::time_put"
  - "time_put"
  - "xloctime/std::time_put"
  - "std.time_put"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "time_put 类"
ms.assetid: df79493e-3331-48d2-97c3-ac3a745f0791
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# time_put 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此模板类描述一个对象来充当区域设置 facet，以便控制时间值向 `CharType` 类型序列的转换。  
  
## 语法  
  
```  
template <  
   class CharType,  
   class OutputIterator = ostreambuf_iterator<CharType>  
> class time_put : public locale::facet;  
```  
  
#### 参数  
 `CharType`  
 在程序中用于对字符进行编码的类型。  
  
 `OutputIterator`  
 供时间放置函数写入其输出结果的迭代器类型。  
  
## 备注  
 对于任何区域设置 facet，静态对象 ID 的初始存储值为零。  首次尝试访问其存储值后，将在 **id** 中存储唯一正值。  
  
### 构造函数  
  
|||  
|-|-|  
|[time\_put](../Topic/time_put::time_put.md)|`time_put` 类型的对象的构造函数。|  
  
### Typedef  
  
|||  
|-|-|  
|[char\_type](../Topic/time_put::char_type.md)|一种类型，此类型用于描述区域设置使用的字符。|  
|[iter\_type](../Topic/time_put::iter_type.md)|一种类型，此类型描述输出迭代器。|  
  
### 成员函数  
  
|||  
|-|-|  
|[do\_put](../Topic/time_put::do_put.md)|一种以 `CharType` 序列的形式输出时间和日期信息的虚拟函数。|  
|[put](../Topic/time_put::put.md)|以 `CharType` 的形式输出时间和日期信息。|  
  
## 要求  
 **标头：**\<locale\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [\<locale\>](../standard-library/locale.md)   
 [time\_base 类](../standard-library/time-base-class.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
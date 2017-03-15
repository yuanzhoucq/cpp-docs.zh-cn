---
title: "time_get 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.time_get"
  - "xloctime/std::time_get"
  - "time_get"
  - "std::time_get"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "time_get 类"
ms.assetid: 869d5f5b-dbab-4628-8333-bdea7e272023
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# time_get 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此模板类描述可用作区域设置 facet 的对象，此对象用于控制 `CharType` 类型序列到时间值的转换。  
  
## 语法  
  
```  
template <  
   class CharType,  
   class InputIterator = istreambuf_iterator<CharType>  
> class time_get : public time_base;  
```  
  
#### 参数  
 `CharType`  
 在程序中用于对字符进行编码的类型。  
  
 `InputIterator`  
 从中读取时间值的迭代器。  
  
## 备注  
 对于任何区域设置 facet，静态对象 ID 的初始存储值为零。  首次尝试访问其存储值后，将在 **id** 中存储唯一正值。  
  
### 构造函数  
  
|||  
|-|-|  
|[time\_get](../Topic/time_get::time_get.md)|`time_get` 类型的对象的构造函数。|  
  
### Typedef  
  
|||  
|-|-|  
|[char\_type](../Topic/time_get::char_type.md)|一种类型，此类型用于描述区域设置使用的字符。|  
|[iter\_type](../Topic/time_get::iter_type.md)|一种类型，此类型描述输入迭代器。|  
  
### 成员函数  
  
|||  
|-|-|  
|[date\_order](../Topic/time_get::date_order.md)|返回 facet 使用的日期顺序。|  
|[do\_date\_order](../Topic/time_get::do_date_order.md)|为返回 facet 使用的日期顺序而调用的受保护虚拟成员函数。|  
|[do\_get](../Topic/time_get::do_get.md)|读取字符数据并转换为时间值。|  
|[do\_get\_date](../Topic/time_get::do_get_date.md)|一种受保护的虚拟成员函数，通过调用此函数可分析作为 `strftime` 的 `x` 说明符所生成日期的字符串。|  
|[do\_get\_monthname](../Topic/time_get::do_get_monthname.md)|为分析作为月份名称的字符串而调用的受保护虚拟函数。|  
|[do\_get\_time](../Topic/time_get::do_get_time.md)|一种受保护的虚拟成员函数，通过调用此函数可分析作为 `strftime` 的 `X` 说明符所生成日期的字符串。|  
|[do\_get\_weekday](../Topic/time_get::do_get_weekday.md)|为分析作为周日期名称的字符串而调用的受保护虚拟成员函数。|  
|[do\_get\_year](../Topic/time_get::do_get_year.md)|为分析作为年份名称的字符串而调用的受保护虚拟成员函数。|  
|[get](../Topic/time_get::get.md)|从字符数据源读取，并将此数据转换为存储在时间结构中的时间。|  
|[get\_date](../Topic/time_get::get_date.md)|分析作为 `strftime` 的 `x` 说明符所生成日期的字符串。|  
|[get\_monthname](../Topic/time_get::get_monthname.md)|分析作为月份名称的字符串。|  
|[get\_time](../Topic/time_get::get_time.md)|分析作为 `strftime` 的 `X` 说明符所生成日期的字符串。|  
|[get\_weekday](../Topic/time_get::get_weekday.md)|分析作为周日期名称的字符串。|  
|[get\_year](../Topic/time_get::get_year.md)|分析作为年份名称的字符串。|  
  
## 要求  
 **标头：**\<locale\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [\<locale\>](../standard-library/locale.md)   
 [time\_base 类](../standard-library/time-base-class.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
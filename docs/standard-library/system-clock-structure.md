---
title: "system_clock 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "chrono/std::chrono::system_clock"
dev_langs: 
  - "C++"
ms.assetid: a97bd46e-267a-4836-9f7d-af1f664e99ae
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# system_clock 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示基于系统实时时钟的*时钟类型*。  
  
## 语法  
  
```  
struct system_clock;  
```  
  
## 备注  
 *时钟类型*用于获取作为 UTC 的当前时间。  该类型包含[持续时间](../standard-library/duration-class.md)的实例化和类模板 [time\_point](../standard-library/time-point-class.md)，并定义返回时间的静态成员函数 `now()`。  
  
 如果首次调用 `now()` 返回的值始终小于或等于后续调用 `now()` 返回的值，则为*单调*时钟。  
  
 如果它是*单调*时钟并且时钟计时周期之间的时间是常量，则为*稳定*时钟。  
  
 在此实现中，`system_clock` 与 `high_resolution_clock` 是同义词。  
  
## 成员  
  
### 公共 Typedef  
  
|名称|描述|  
|--------|--------|  
|`system_clock::duration`|`duration<rep, period>` 的同义词。|  
|`system_clock::period`|该类型的同义词，用于表示在包含的 `duration` 的实例化中的时钟周期。|  
|`system_clock::rep`|该类型的同义词，用于表示在包含的 `duration` 的实例化中的时钟计时周期数。|  
|`system_clock::time_point`|`time_point<Clock, duration>` 的同义词，其中 `Clock` 是时钟类型本身的同义词，或是另一种基于同一时期并具有相同嵌套 `duration` 类型的时钟类型的同义词。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[system\_clock::from\_time\_t 方法](../Topic/system_clock::from_time_t%20Method.md)|静态。  返回最接近指定的时间的 `time_point`。|  
|[system\_clock::now Method](../Topic/system_clock::now%20Method.md)|静态。  返回当前日期。|  
|[system\_clock::to\_time\_t 方法](../Topic/system_clock::to_time_t%20Method.md)|静态。  返回最接近指定 `time_point` 的 `time_t` 对象。|  
  
### 公共常量  
  
|名称|说明|  
|--------|--------|  
|[system\_clock::is\_monotonic 常量](../Topic/system_clock::is_monotonic%20Constant.md)|指定时钟类型是否为单调。|  
|[system\_clock::is\_steady 常量](../Topic/system_clock::is_steady%20Constant.md)|指定时钟类型是否为稳定。|  
  
## 要求  
 **标头：**chrono  
  
 **命名空间：**std::chrono  
  
## 请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [\<chrono\>](../standard-library/chrono.md)   
 [steady\_clock 结构](../standard-library/steady-clock-struct.md)
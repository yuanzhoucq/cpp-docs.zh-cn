---
title: "time_point 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "chrono/std::chrono::time_point"
dev_langs: 
  - "C++"
ms.assetid: 18be1e52-57b9-489a-8a9b-f58894f0aaad
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# time_point 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`time_point` 描述表示时间点的类型。  它保留存储时间，因为由模板参数 `Clock`的时间点表示类型“持续时间” [](../standard-library/duration-class.md "duration Class") 的。  
  
## 语法  
  
```  
template<  
   class Clock,  
   class Duration = typename Clock::duration  
>  
class time_point;  
```  
  
## 成员  
  
### 公共 Typedef  
  
|Name|说明|  
|----------|--------|  
|`time_point::clock`|模板参数 `Clock`的同义词。|  
|`time_point::duration`|模板参数 `Duration`的同义词。|  
|`time_point::period`|嵌套类型名称 `duration::period`的同义词。|  
|`time_point::rep`|嵌套类型名称 `duration::rep`的同义词。|  
  
### 公共构造函数  
  
|Name|说明|  
|----------|--------|  
|[time\_point::time\_point 构造函数](../Topic/time_point::time_point%20Constructor.md)|构造 `time_point` 对象。|  
  
### 公共方法  
  
|Name|说明|  
|----------|--------|  
|[time\_point::max 方法](../Topic/time_point::max%20Method.md)|为 `time_point::ref`指定了上限。|  
|[time\_point::min 方法](../Topic/time_point::min%20Method.md)|为 `time_point::ref`指定了下限。|  
|[time\_point::time\_since\_epoch 方法](../Topic/time_point::time_since_epoch%20Method.md)|返回存储的 `duration` 值。|  
  
### 公共运算符  
  
|Name|说明|  
|----------|--------|  
|[time\_point::operator\+\= 运算符](../Topic/time_point::operator+=%20Operator.md)|为存储值添加指定值。|  
|[time\_point::operator\-\= 运算符](../Topic/time_point::operator-=%20Operator.md)|从存储的值减去指定的值。|  
  
## 要求  
 **Header:** chrono  
  
 **Namespace:** std::chrono  
  
## 请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [\<chrono\>](../standard-library/chrono.md)
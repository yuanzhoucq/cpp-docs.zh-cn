---
title: "steady_clock 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "chrono/std::chrono::steady_clock"
dev_langs: 
  - "C++"
ms.assetid: 970d12ec-fc80-4391-a2f7-b57b2aec668d
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# steady_clock 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示 `steady` 时钟。  
  
## 语法  
  
```  
struct steady_clock;  
```  
  
## 备注  
 在 Windows 上，steady\_clock 会包装 QueryPerformanceCounter 函数。  
  
 如果首次调用 `now()` 返回的值始终小于或等于后续调用 `now()` 返回的值，则为*单调*时钟。  
  
 如果它是*单调*时钟并且时钟计时周期之间的时间是常量，则为*稳定*时钟。  
  
 High\_resolution\_clock 是 steady\_clock 的 typdef。  
  
## 公共函数  
  
|函数|描述|  
|--------|--------|  
|现在|返回当前时间作为 time\_point 值。|  
  
## 公共常量  
  
|名称|描述|  
|--------|--------|  
|`system_clock::is_steady`|保存 `true`。  `steady_clock` 是*稳定的*。|  
  
## 要求  
 **标头：**chrono  
  
 **命名空间：**std::chrono  
  
## 请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [\<chrono\>](../standard-library/chrono.md)   
 [system\_clock 结构](../standard-library/system-clock-structure.md)
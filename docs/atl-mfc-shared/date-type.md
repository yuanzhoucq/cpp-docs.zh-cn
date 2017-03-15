---
title: "DATE Type | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "DATE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "日期数据类型"
  - "日期数据类型, about Date data type"
  - "日期数据类型, 实现"
  - "DATE type"
  - "hour values representation"
  - "MFC, 日期和时间"
ms.assetid: 695853ed-b614-4575-b793-b8c287372038
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# DATE Type
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用 8 字节浮点数，**DATE** 类型实现。  天数由启动整数的增量表示为 1899 年十二月 30 日午夜时，为零。  小时数值表示为该数字的小数部分的绝对值。  下表与其 **DATE** 类型数字等效。演示了几个日期：  
  
|日期和时间|表示形式|  
|-----------|----------|  
|1899 年十二月 30 日午夜，|0.00|  
|1900 年一月 1 日午夜，|2.00|  
|1900 年一月 4 日午夜，|5.00|  
|1900 年一月 4 日，6 AM..|5.25|  
|1900 年一月 4 日，中午|5.50|  
|1900 年一月 4 日，9 PM..|5.875|  
  
 **DATE** 日期类型，以及 `COleDateTime` 选件类，表示日期和时间作为一传统数字行。  `COleDateTime` 选件类来回其他常规日期格式包含操作的日期值几个方法，包括转换。  
  
 以下问题应该注意，在处理这些可以在自动测试时的日期和时间格式：  
  
-   日期在本地时间指定；，当使用日期不同的时区时，必须手动执行同步。  
  
-   日期类型不考虑夏时制时间。  
  
-   日期时间线变为不连续的日期小于 0 的值 \(在 1899 年十二月 30 日之前\)。  这是因为，日期值的整数部分将签名，而该节的节视为无符号。  换言之，而日期值的小数部分总是添加到整个逻辑日期，日期值的整数部件可以是正值或负值。  下表阐释了几个示例：  
  
|日期和时间|表示形式|  
|-----------|----------|  
|1899 年十二月 27 日午夜，|\-3.00|  
|1899 年十二月 28 日，中午|\-2.50|  
|1899 年十二月 28 日午夜，|\-2.00|  
|1899 年十二月 29 日午夜，|\-1.00|  
|1899 年十二月 30 日，6 PM..|\-0.75|  
|1899 年十二月 30 日，中午|\-0.50|  
|1899 年十二月 30 日，6 AM..|\-0.25|  
|1899 年十二月 30 日午夜，|0.00|  
|1899 年十二月 30 日，6 AM..|0.25|  
|1899 年十二月 30 日，中午|0.50|  
|1899 年十二月 30 日，6 PM..|0.75|  
|1899 年十二月 31 日午夜，|1.00|  
|1900 年一月 1 日午夜，|2.00|  
|1900 年一月 1 日，中午|2.50|  
|1900 年一月 2 日午夜，|3.00|  
  
> [!CAUTION]
>  请注意，由于凌晨 6:00 由一部分的值 0.25 高于表示在同一日的 **DATE** 始终表示无论表示日的该整数是否为正数的 \(在 1899 年十二月 30 日更高版本\) 或负 \(在 1899 年十二月 30 日之前\)，一个简单的浮点比较将不正确排序表示凌晨 6:00 的所有 *later* 日期早于 **DATE** 12\/30\/1899 为凌晨 7:00。  
  
 更多信息问题与 **DATE**，并 `COleDateTime` 类型可以位于 [COleDateTime Class](../atl-mfc-shared/reference/coledatetime-class.md) 和 [Date and Time: Automation Support](../atl-mfc-shared/date-and-time-automation-support.md)下。  
  
## 请参阅  
 [Date and Time](../atl-mfc-shared/date-and-time.md)   
 [COleDateTime Class](../atl-mfc-shared/reference/coledatetime-class.md)
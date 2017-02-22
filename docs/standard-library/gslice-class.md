---
title: "gslice 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::gslice"
  - "std.gslice"
  - "gslice"
  - "valarray/std::gslice"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "gslice 类"
ms.assetid: f47cffd0-ea59-4b13-848b-7a5ce1d7e2a3
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# gslice 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

对多维定义子集 valarray 的 valarray 的公共类。  如果 valarray 视为带任何元素的矩阵，则多维数组中提取切片矢量从多维数组。  
  
## 备注  
 类用于存储分析类型 [gslice\_array](../standard-library/gslice-array-class.md) 对象的参数。  当类 gslice 对象显示为类 [valarray](../Topic/valarray::operator.md)**\<类型\>**时，一个对象子集 valarray 间接参数构造。  部分指定的存储的值。valarray 的父选择包括：  
  
-   一个起始索引。  
  
-   类  **valarray\<size\_t\>** 长度矢量。  
  
-   类  **valarray\<size\_t\>** 跨距矢量。  
  
 两个矢量必须具有相同长度。  
  
 如果 gslice 定义的集合是的子集 valarray 常数，则 gslice 新 valarray。  如果 gslice 定义的集合是的子集 valarray 一个常数，则 gslice 具有引用语义对于 valarray 的原始。  常数的计算 valarrays 机制保存时间和内存。  
  
 在 valarrays 操作，确保仅 gslices 定义的源和目标中部分是不同的，并且所有索引都有效。  
  
### 构造函数  
  
|||  
|-|-|  
|[gslice](../Topic/gslice::gslice.md)|定义包含 `valarray` 的多个切片所有开始的指定元素 `valarray` 的子集。|  
  
### 成员函数  
  
|||  
|-|-|  
|[size](../Topic/gslice::size.md)|查找数组值指定元素个数 `valarray` 中的泛切片。|  
|[开始](../Topic/gslice::start.md)|查找 `valarray` 的泛切片的起始索引。|  
|[跨距](../Topic/gslice::stride.md)|查找在 `valarray` 中的泛切片元素之间的距离。|  
  
## 要求  
 **标头：**\<valarray\>  
  
 **命名空间:** std  
  
## 请参阅  
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
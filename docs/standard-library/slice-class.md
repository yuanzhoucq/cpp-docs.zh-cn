---
title: "slice 类 | Microsoft Docs"
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
  - "valarray/std::slice"
  - "std.slice"
  - "slice"
  - "std::slice"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "slice 类"
ms.assetid: 00f0b03d-d657-4b81-ba53-5a9034bb2bf2
caps.latest.revision: 23
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# slice 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

valarray 的实用程序类，用于定义父级 valarray 的一维子集。  如果 valarray 被视为一个其所有元素都在一个数组中的二维矩阵，则切片会将一个维度中的向量从二维数组中提取出来。  
  
## 备注  
 该类存储了将 [slice\_array](../standard-library/slice-array-class.md) 类型的对象特征化的参数。当类切片显示为 [valarray](../Topic/valarray::operator.md)**\<Type\>** 类的对象的参数时，会间接构造 valarray 的子集。  存储的值（用于指定从父级 valarray 选择的子集）包括：  
  
-   valarray 中的起始索引。  
  
-   总长度或切片中的元素数目。  
  
-   跨距，或 valarray 中元素的后续索引之间的距离。  
  
 如果由切片定义的集为常量 valarray 的子集，则该切片将是新的 valarray。  如果由切片定义的集为非常量 valarray 的子集，则该切片将具有对原始 valarray 的引用语义。  非常量 valarray 的评估机制节省了时间和内存。  
  
 仅当由切片定义的源和目标子集都是不重复的并且所有索引都是有效的，才可以保证对 valarray 的操作。  
  
### 构造函数  
  
|||  
|-|-|  
|[切片](../Topic/slice::slice.md)|定义 `valarray` 的一个子集，该 valarray 包含一些等距分隔的元素，并且在指定的元素开始。|  
  
### 成员函数  
  
|||  
|-|-|  
|[size](../Topic/slice::size.md)|查找 `valarray` 的切片中的元素数目。|  
|[开始](../Topic/slice::start.md)|查找 `valarray` 的切片的起始索引。|  
|[跨距](../Topic/slice::stride.md)|查找 `valarray` 的切片中元素之间的距离。|  
  
## 要求  
 **标头：**\<valarray\>  
  
 **命名空间:** std  
  
## 请参阅  
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
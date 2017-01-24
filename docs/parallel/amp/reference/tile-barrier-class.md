---
title: "tile_barrier 类 | Microsoft Docs"
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
  - "amp/Concurrency::tile_barrier"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "tile_barrier 类"
ms.assetid: b4ccdccb-0032-4e11-b7bd-dc9d43445dee
caps.latest.revision: 17
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# tile_barrier 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

通过使用 `wait` 方法同步在线程组（平铺）中运行的线程的执行。  只有运行时可以实例化此类。  
  
## 语法  
  
```  
class tile_barrier;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[tile\_barrier::tile\_barrier 构造函数](../Topic/tile_barrier::tile_barrier%20Constructor.md)|初始化 `tile_barrier` 类的新实例。|  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[tile\_barrier::wait 方法](../Topic/tile_barrier::wait%20Method.md)|指示线程组（图标）中所有线程停止执行，直到图标中的所有线程完成等待。|  
|[tile\_barrier::wait\_with\_all\_memory\_fence 方法](../Topic/tile_barrier::wait_with_all_memory_fence%20Method.md)|阻止平铺视图中所有线程的执行，直到所有内存访问都完成且该平铺视图内的所有线程都达到此调用。|  
|[tile\_barrier::wait\_with\_global\_memory\_fence 方法](../Topic/tile_barrier::wait_with_global_memory_fence%20Method.md)|阻止平铺视图中所有线程的执行，直到所有全局内存访问都完成且该平铺视图内的所有线程都达到此调用。|  
|[tile\_barrier::wait\_with\_tile\_static\_memory\_fence 方法](../Topic/tile_barrier::wait_with_tile_static_memory_fence%20Method.md)|阻止平铺视图中所有线程的执行，直到所有 `tile_static` 内存访问都完成且该平铺视图内的所有线程都达到此调用。|  
  
## 继承层次结构  
 `tile_barrier`  
  
## 要求  
 **标头：**amp.h  
  
 **命名空间：** 并发  
  
## 请参阅  
 [Concurrency 命名空间 \(C\+\+ AMP\)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)
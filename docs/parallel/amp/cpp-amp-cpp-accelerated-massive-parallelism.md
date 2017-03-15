---
title: "C++ AMP (C++ Accelerated Massive Parallelism) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C++ Accelerated Massive Parallelism, 入门"
  - "C++ AMP（请参见 C++ Accelerated Massive Parallelism）"
ms.assetid: e27824cb-3167-409b-8c3f-a0e476d8f349
caps.latest.revision: 22
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C++ AMP (C++ Accelerated Massive Parallelism)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

C\+\+ AMP \(C\+\+ Accelerated Massive Parallelism\) 可加速 C\+\+ 代码执行，方法是通过利用数据并行硬件（通常表示为离散图像卡上的图像处理单元 \(GPU\)）  C\+\+ AMP 编程模型包括对多维数组、索引，内存传输和平铺的支持。  它还包括数学函数库。  您可以使用 C\+\+ AMP 语言扩展控制数据在 CPU 和 GPU 之间相互移动的方式。  
  
## 相关主题  
  
|标题|描述|  
|--------|--------|  
|[C\+\+ AMP 概述](../../parallel/amp/cpp-amp-overview.md)|说明 C\+\+ AMP 和数学库的关键功能。|  
|[使用 Lambda 表达式、函数对象和受限函数](../../parallel/amp/using-lambdas-function-objects-and-restricted-functions.md)|说明在 [parallel\_for\_each](../Topic/parallel_for_each%20Function%20\(C++%20AMP\).md) 方法调用中，如何使用 lambda 表达式、函数对象和受限函数。|  
|[使用平铺](../../parallel/amp/using-tiles.md)|说明如何使用平铺以加速 C\+\+ AMP 代码。|  
|[使用 accelerator 和 accelerator\_view 对象](../../parallel/amp/using-accelerator-and-accelerator-view-objects.md)|说明如何使用加速器自定义 GPU 上代码的执行。|  
|[在 Windows 应用商店应用程序中使用 C\+\+ AMP](../../parallel/amp/using-cpp-amp-in-windows-store-apps.md)|说明如何在使用 Windows 运行时类型的 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序中使用 C\+\+ AMP。|  
|[图形 \(C\+\+ AMP\)](../../parallel/amp/graphics-cpp-amp.md)|说明如何使用 C\+\+ AMP 图形库。|  
|[演练：矩阵乘法](../../parallel/amp/walkthrough-matrix-multiplication.md)|使用 C\+\+ AMP 代码和平铺演示矩阵乘法。|  
|[演练：调试 C\+\+ AMP 应用程序](../../parallel/amp/walkthrough-debugging-a-cpp-amp-application.md)|说明如何创建和调试用平行缩减来合计大型整数数组的应用程序。|  
  
## 引用  
 [参考 \(C\+\+ AMP\)](../../parallel/amp/reference/reference-cpp-amp.md)  
  
 [tile\_static 关键字](../../cpp/tile-static-keyword.md)  
  
 [restrict \(C\+\+ AMP\)](../../cpp/restrict-cpp-amp.md)  
  
## 其他资源  
 [Parallel Programming in Native Code Blog](http://go.microsoft.com/fwlink/p/?LinkId=238472)（本机代码博客中的并行编程）  
  
 [用于下载的 C\+\+ AMP 示例项目](http://go.microsoft.com/fwlink/p/?LinkId=248508)  
  
 [Analyzing C\+\+ AMP Code with the Concurrency Visualizer](http://go.microsoft.com/fwlink/?LinkID=253987&clcid=0x409)（使用并发可视化工具分析 C\+\+ AMP 代码）
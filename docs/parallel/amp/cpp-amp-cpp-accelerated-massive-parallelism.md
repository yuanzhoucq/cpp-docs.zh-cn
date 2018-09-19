---
title: C + + AMP (c + + Accelerated Massive Parallelism) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- C++ AMP (see C++ Accelerated Massive Parallelism)
- C++ Accelerated Massive Parallelism, getting started
ms.assetid: e27824cb-3167-409b-8c3f-a0e476d8f349
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 340a21a3bbcb1853d66de01bddf9425fed0c8183
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2018
ms.locfileid: "43689839"
---
# <a name="c-amp-c-accelerated-massive-parallelism"></a>C++ AMP (C++ Accelerated Massive Parallelism)
C + + AMP (c + + Accelerated Massive Parallelism) 通过利用数据并行硬件的是通常表示为离散图像卡上的图形处理单元 (GPU) 加快了 c + + 代码的执行。 C + + AMP 编程模型包括对多维数组，索引，内存传输和平铺的支持。 它还包括数学函数库。 可以使用 c + + AMP 语言扩展控制数据移动方式从 CPU 到 GPU 和备份。  
  
## <a name="related-topics"></a>相关主题  
  
|标题|描述|  
|-----------|-----------------|  
|[C++ AMP 概述](../../parallel/amp/cpp-amp-overview.md)|介绍 c + + AMP 和数学库的主要功能。|  
|[使用 Lambda 表达式、函数对象和受限函数](../../parallel/amp/using-lambdas-function-objects-and-restricted-functions.md)|介绍如何使用 lambda 表达式、 函数对象和受限的函数在调用[parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each)方法。|  
|[使用平铺](../../parallel/amp/using-tiles.md)|介绍如何使用平铺以加速 c + + AMP 代码。|  
|[使用 accelerator 和 accelerator_view 对象](../../parallel/amp/using-accelerator-and-accelerator-view-objects.md)|介绍如何使用加速器自定义代码在 GPU 上执行。|  
|[在 UWP 应用中使用 C++ AMP](../../parallel/amp/using-cpp-amp-in-windows-store-apps.md)|介绍如何使用 Windows 运行时类型的通用 Windows 平台 (UWP) 应用中使用 c + + AMP。|  
|[图形 (C++ AMP)](../../parallel/amp/graphics-cpp-amp.md)|介绍如何使用 c + + AMP 图形库。|  
|[演练：矩阵乘法](../../parallel/amp/walkthrough-matrix-multiplication.md)|演示如何使用 c + + AMP 代码和平铺矩阵乘法。|  
|[演练：调试 C++ AMP 应用程序](../../parallel/amp/walkthrough-debugging-a-cpp-amp-application.md)|介绍如何创建和调试用平行缩减总结一下大型整数数组的应用程序。|  
  
## <a name="reference"></a>参考  

[参考 (c + + AMP)](../../parallel/amp/reference/reference-cpp-amp.md)    
[tile_static 关键字](../../cpp/tile-static-keyword.md)    
[restrict (C++ AMP)](../../cpp/restrict-cpp-amp.md)  
  
## <a name="other-resources"></a>其他资源  
 
[本机代码博客中的并行编程](http://go.microsoft.com/fwlink/p/?linkid=238472)  
[C + + AMP 示例项目下载](http://go.microsoft.com/fwlink/p/?linkid=248508)  
[使用并发可视化工具分析 c + + AMP 代码](https://blogs.msdn.microsoft.com/nativeconcurrency/2012/03/09/analyzing-c-amp-code-with-the-concurrency-visualizer/)
---
title: C + + AMP (c + + Accelerated Massive Parallelism) |Microsoft 文档
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
ms.openlocfilehash: 98ae6b6a5cd24a1ea146cca7ccb30fcbdc93ae75
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33705362"
---
# <a name="c-amp-c-accelerated-massive-parallelism"></a>C++ AMP (C++ Accelerated Massive Parallelism)
C + + AMP (c + + Accelerated Massive Parallelism) 通过利用通常显示为在离散图形卡的图形处理单元 (GPU) 的数据并行硬件加速执行 c + + 代码。 C + + AMP 编程模型包括支持多维数组，索引，内存传输和平铺。 它还包括数学函数库。 你可以使用 c + + AMP 语言扩展来控制如何数据移动 CPU 到 GPU 和备份。  
  
## <a name="related-topics"></a>相关主题  
  
|标题|描述|  
|-----------|-----------------|  
|[C++ AMP 概述](../../parallel/amp/cpp-amp-overview.md)|介绍 c + + AMP 和数学库的关键功能。|  
|[使用 Lambda 表达式、函数对象和受限函数](../../parallel/amp/using-lambdas-function-objects-and-restricted-functions.md)|描述如何在调用中使用 lambda 表达式、 函数对象和受限的函数[parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each)方法。|  
|[使用平铺](../../parallel/amp/using-tiles.md)|介绍如何使用磁贴来加快你的 c + + AMP 代码。|  
|[使用 accelerator 和 accelerator_view 对象](../../parallel/amp/using-accelerator-and-accelerator-view-objects.md)|介绍如何使用快捷键以便自定义你的代码在 GPU 上执行。|  
|[在 UWP 应用中使用 C++ AMP](../../parallel/amp/using-cpp-amp-in-windows-store-apps.md)|描述如何使用 Windows 运行时类型的通用 Windows 平台 (UWP) 应用中使用 c + + AMP。|  
|[图形 (C++ AMP)](../../parallel/amp/graphics-cpp-amp.md)|描述如何使用 c + + AMP 图形库。|  
|[演练：矩阵乘法](../../parallel/amp/walkthrough-matrix-multiplication.md)|演示如何使用 c + + AMP 代码和平铺的矩阵相乘。|  
|[演练：调试 C++ AMP 应用程序](../../parallel/amp/walkthrough-debugging-a-cpp-amp-application.md)|说明如何创建和调试的应用程序使用并行缩减来求和一个大整数的数组。|  
  
## <a name="reference"></a>参考  
 [参考 (C++ AMP)](../../parallel/amp/reference/reference-cpp-amp.md)  
  
 [tile_static 关键字](../../cpp/tile-static-keyword.md)  
  
 [restrict (C++ AMP)](../../cpp/restrict-cpp-amp.md)  
  
## <a name="other-resources"></a>其他资源  
 [在本机代码的博客中的并行编程](http://go.microsoft.com/fwlink/p/?linkid=238472)  
  
 [下载的 c + + AMP 示例项目](http://go.microsoft.com/fwlink/p/?linkid=248508)  
  
 [分析 c + + AMP 代码使用并发可视化工具](http://go.microsoft.com/fwlink/p/?linkid=253987&clcid=0x409)


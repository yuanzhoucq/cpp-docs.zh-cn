---
title: C++ AMP (C++ Accelerated Massive Parallelism)
ms.date: 11/04/2016
helpviewer_keywords:
- C++ AMP (see C++ Accelerated Massive Parallelism)
- C++ Accelerated Massive Parallelism, getting started
ms.assetid: e27824cb-3167-409b-8c3f-a0e476d8f349
ms.openlocfilehash: f8ac71023f66868a66fb8c54a5e86678225378a1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400690"
---
# <a name="c-amp-c-accelerated-massive-parallelism"></a>C++ AMP (C++ Accelerated Massive Parallelism)

C++A m P (C++ Accelerated Massive Parallelism) 后，更快的执行在C++通过利用的是通常表示为离散图像卡上的图形处理单元 (GPU) 的数据并行硬件的代码。 C++ AMP 编程模型包括对多维数组，索引，内存传输和平铺的支持。 它还包括数学函数库。 可以使用C++AMP 语言扩展控制数据移动的方式在 CPU 和 GPU 之间相互后。

## <a name="related-topics"></a>相关主题

|Title|描述|
|-----------|-----------------|
|[C++ AMP 概述](../../parallel/amp/cpp-amp-overview.md)|描述主要功能的C++AMP 和数学库。|
|[使用 Lambda 表达式、函数对象和受限函数](../../parallel/amp/using-lambdas-function-objects-and-restricted-functions.md)|介绍如何使用 lambda 表达式、 函数对象和受限的函数在调用[parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each)方法。|
|[使用平铺](../../parallel/amp/using-tiles.md)|介绍如何使用平铺以加速你C++AMP 代码。|
|[使用 accelerator 和 accelerator_view 对象](../../parallel/amp/using-accelerator-and-accelerator-view-objects.md)|介绍如何使用加速器自定义代码在 GPU 上执行。|
|[在 UWP 应用中使用 C++ AMP](../../parallel/amp/using-cpp-amp-in-windows-store-apps.md)|介绍如何使用C++使用 Windows 运行时类型的通用 Windows 平台 (UWP) 应用中的 AMP。|
|[图形 (C++ AMP)](../../parallel/amp/graphics-cpp-amp.md)|介绍如何使用C++AMP 图形库。|
|[演练：矩阵乘法](../../parallel/amp/walkthrough-matrix-multiplication.md)|演示如何使用矩阵乘法C++AMP 代码和平铺。|
|[演练：调试 C++ AMP 应用程序](../../parallel/amp/walkthrough-debugging-a-cpp-amp-application.md)|介绍如何创建和调试用平行缩减总结一下大型整数数组的应用程序。|

## <a name="reference"></a>参考

[参考 (C++ AMP)](../../parallel/amp/reference/reference-cpp-amp.md)<br/>
[tile_static 关键字](../../cpp/tile-static-keyword.md)<br/>
[restrict (C++ AMP)](../../cpp/restrict-cpp-amp.md)

## <a name="other-resources"></a>其他资源

[本机代码博客中的并行编程](http://go.microsoft.com/fwlink/p/?linkid=238472)<br/>
[C++AMP 示例项目下载](http://go.microsoft.com/fwlink/p/?linkid=248508)<br/>
[分析C++使用并发可视化工具的 AMP 代码](https://blogs.msdn.microsoft.com/nativeconcurrency/2012/03/09/analyzing-c-amp-code-with-the-concurrency-visualizer/)
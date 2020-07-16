---
title: C++ AMP (C++ Accelerated Massive Parallelism)
ms.date: 11/04/2016
helpviewer_keywords:
- C++ AMP (see C++ Accelerated Massive Parallelism)
- C++ Accelerated Massive Parallelism, getting started
ms.assetid: e27824cb-3167-409b-8c3f-a0e476d8f349
ms.openlocfilehash: 516b69a0371ceb9365e79d5465879711289076c0
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2020
ms.locfileid: "86404855"
---
# <a name="c-amp-c-accelerated-massive-parallelism"></a>C++ AMP (C++ Accelerated Massive Parallelism)

C++ AMP （C++ Accelerated Massive Parallelism）可利用通常以图形处理单元（GPU）形式出现在离散图形卡上的数据并行硬件，加速 c + + 代码的执行。 C++ AMP 编程模型包括对多维数组、索引、内存传输和平铺的支持。 它还包括一个数学函数库。 你可以使用 C++ AMP 语言扩展来控制数据在 CPU 和 GPU 之间的移动方式。

## <a name="related-topics"></a>相关主题

|Title|说明|
|-----------|-----------------|
|[C++ AMP 概述](../../parallel/amp/cpp-amp-overview.md)|介绍 C++ AMP 和数学库的主要功能。|
|[使用 Lambda、函数对象和受限函数](../../parallel/amp/using-lambdas-function-objects-and-restricted-functions.md)|介绍如何在对[parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each)方法的调用中使用 lambda 表达式、函数对象和受限函数。|
|[使用磁贴](../../parallel/amp/using-tiles.md)|描述如何使用磁贴加速 C++ AMP 代码。|
|[使用加速器和 accelerator_view 对象](../../parallel/amp/using-accelerator-and-accelerator-view-objects.md)|介绍如何使用加速器自定义在 GPU 上执行的代码。|
|[在 UWP 应用中使用 C++ AMP](../../parallel/amp/using-cpp-amp-in-windows-store-apps.md)|介绍如何在使用 Windows 运行时类型通用 Windows 平台（UWP）应用中使用 C++ AMP。|
|[图形 (C++ AMP)](../../parallel/amp/graphics-cpp-amp.md)|介绍如何使用 C++ AMP 图形库。|
|[演练：矩阵乘法](../../parallel/amp/walkthrough-matrix-multiplication.md)|使用 C++ AMP 代码和平铺演示矩阵乘法。|
|[演练：调试 C++ AMP 应用程序](../../parallel/amp/walkthrough-debugging-a-cpp-amp-application.md)|说明如何创建和调试一个应用程序，该应用程序使用并行减少来合计大型整数数组。|

## <a name="reference"></a>参考

[参考 (C++ AMP)](../../parallel/amp/reference/reference-cpp-amp.md)<br/>
[tile_static 关键字](../../cpp/tile-static-keyword.md)<br/>
[restrict (C++ AMP)](../../cpp/restrict-cpp-amp.md)

## <a name="other-resources"></a>其他资源

[本机代码中的并行编程博客](https://go.microsoft.com/fwlink/p/?linkid=238472)<br/>
[C++ AMP 可下载的示例项目](https://go.microsoft.com/fwlink/p/?linkid=248508)<br/>
[利用并发可视化工具分析 C++ AMP 代码](/archive/blogs/nativeconcurrency/analyzing-c-amp-code-with-the-concurrency-visualizer)

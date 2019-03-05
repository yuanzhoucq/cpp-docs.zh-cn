---
title: 参考 (C++ AMP)
ms.date: 11/04/2016
f1_keywords:
- amp/Concurrency::Reference (C++ AMP)
helpviewer_keywords:
- C++ Accelerated Massive Parallelism, reference
ms.assetid: 372a8aed-8a53-48c9-996f-9c3cf09c9fa8
ms.openlocfilehash: a334c7873675183dc06abfc2fe51472190996bf3
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57257502"
---
# <a name="reference-c-amp"></a>参考 (C++ AMP)

本部分包含有关 c + + Accelerated Massive Parallelism (c + + AMP) 运行时参考信息。

> [!NOTE]
>  C++ 语言标准将保留以下划线 (`_`) 字符开头的标识符，供实现（例如库）使用。 请勿在代码中使用以下划线开头的名称。 其名称遵循此约定的代码元素的行为尚未得到保证，在将来发布的版本中可能会有更改。 出于这些原因，此文档中省略了此类代码元素。

## <a name="in-this-section"></a>本节内容

[并发命名空间 (C++ AMP)](concurrency-namespace-cpp-amp.md)<br/>
提供类和启用的数据并行硬件上的 c + + 代码加速的函数。

[Concurrency::direct3d 命名空间](concurrency-direct3d-namespace.md)<br/>
提供支持 D3D 互操作性的函数。 启用无缝使用 D3D 资源在 AMP 代码中的计算和使用资源在 AMP 中创建在 D3D 代码中，而无需创建冗余的中间副本。 可以使用 c + + AMP 来增量加速您的 DirectX 应用程序的计算密集型部分，并使用从 AMP 计算生成的数据上的 D3D API。

[Concurrency::fast_math 命名空间](concurrency-fast-math-namespace.md)<br/>
中的函数`fast_math`命名空间不符合 C99 标准。 提供了每个函数仅单精度版本。 这些函数使用 DirectX 内部函数，其速度要快于中的相应函数`precise_math`命名空间并不需要扩展的双精度支持快捷键，但它们是不太准确。 有两个版本的每个函数与 C99 代码; 的源级别兼容性的这两个版本采用并返回单精度值。

[Concurrency::graphics 命名空间](concurrency-graphics-namespace.md)<br/>
为图形编程中提供类型和设计的功能。

[Concurrency::precise_math 命名空间](concurrency-precise-math-namespace.md)<br/>
中的函数`precise_math`命名空间是符合 C99。 包含每个函数的单精度和双精度版本。 这些函数，这包括单精度函数 — 需要扩展的双精度快捷键支持。

## <a name="related-sections"></a>相关章节

[C++ AMP (C++ Accelerated Massive Parallelism)](../../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
C + + AMP 可加速 c + + 代码的执行方法通过利用的是通常表示为离散图像卡上的图形处理单元 (GPU) 的数据并行硬件。

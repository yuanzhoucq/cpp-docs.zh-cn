---
title: 参考 (C++ AMP)
ms.date: 11/04/2016
f1_keywords:
- amp/Concurrency::Reference (C++ AMP)
helpviewer_keywords:
- C++ Accelerated Massive Parallelism, reference
ms.assetid: 372a8aed-8a53-48c9-996f-9c3cf09c9fa8
ms.openlocfilehash: ff7c2b0894a2fa3de7674a72bc93dd3f781398b9
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126404"
---
# <a name="reference-c-amp"></a>参考 (C++ AMP)

本部分包含有关加速的C++大规模并行度（C++ AMP）运行时的参考信息。

> [!NOTE]
> C++ 语言标准将保留以下划线 (`_`) 字符开头的标识符，供实现（例如库）使用。 请勿在代码中使用以下划线开头的名称。 其名称遵循此约定的代码元素的行为尚未得到保证，在将来发布的版本中可能会有更改。 出于这些原因，此文档中省略了此类代码元素。

## <a name="in-this-section"></a>本节内容

[并发命名空间 (C++ AMP)](concurrency-namespace-cpp-amp.md)<br/>
提供使C++代码在数据并行硬件上加速的类和函数。

[Concurrency::direct3d 命名空间](concurrency-direct3d-namespace.md)<br/>
提供支持 D3D 互操作性的函数。 允许无缝使用 D3D 资源来计算 AMP 代码和在 D3D 代码中创建的资源，而无需创建冗余的中间副本。 你可以使用C++ amp 增量加速 DirectX 应用程序的计算密集型部分，并在从 AMP 计算生成的数据上使用 D3D API。

[Concurrency::fast_math 命名空间](concurrency-fast-math-namespace.md)<br/>
`fast_math` 命名空间中的函数不符合 C99。 仅提供每个函数的单精度版本。 这些函数使用 DirectX 内部函数，该函数比 `precise_math` 命名空间中的对应函数快，并且不需要对加速器进行扩展的双精度支持，但它们不太准确。 每个函数的两个版本都适用于与 C99 代码进行源级别的兼容性。这两个版本都采用并返回单精度值。

[Concurrency::graphics 命名空间](concurrency-graphics-namespace.md)<br/>
提供专为图形编程设计的类型和函数。

[Concurrency::precise_math 命名空间](concurrency-precise-math-namespace.md)<br/>
`precise_math` 命名空间中的函数符合 C99。 每个函数的单精度和双精度版本都包括在内。 这些函数（包括单精度函数）需要对加速器进行扩展的双精度支持。

## <a name="related-sections"></a>相关章节

[C++ AMP (C++ Accelerated Massive Parallelism)](../../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
C++AMP 利用了数据并行硬件C++ （通常以图形处理单元（GPU）形式出现在离散图形卡上），加速了代码的执行。

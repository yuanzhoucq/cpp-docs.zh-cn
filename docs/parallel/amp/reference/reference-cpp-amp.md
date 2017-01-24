---
title: "参考 (C++ AMP) | Microsoft Docs"
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
  - "amp/Concurrency::Reference (C++ AMP)"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C++ Accelerated Massive Parallelism, 参考"
ms.assetid: 372a8aed-8a53-48c9-996f-9c3cf09c9fa8
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 参考 (C++ AMP)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

本节包含针对 C\+\+ Accelerated Massive Parallelism \(C\+\+ AMP\) 运行时的参考信息。  
  
> [!NOTE]
>  C\+\+ 语言标准将以下划线 \(`_`\) 字符开始的标识符保留给实现（如库）使用。  不要在您的代码中使用以下划线开头的名称。  不保证其名称遵循此约定的代码元素的行为，并且这类行为在将来发布的版本中可能会有所更改。  基于上述原因，此文档将省略这类代码元素。  
  
## 本节内容  
 [Concurrency 命名空间 \(C\+\+ AMP\)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)  
 提供在数据并行硬件上允许 C\+\+ 代码加速执行的类和函数。  
  
 [Concurrency::direct3d 命名空间](../../../parallel/amp/reference/concurrency-direct3d-namespace.md)  
 提供支持 D3D 互操作性的功能。  无缝使用 D3D 资源以在 AMP 代码中进行计算，并使用在 D3D 代码中的 AMP 中创建的资源，而不会创建冗余的中间副本。  可使用 C\+\+ AMP 来增量加速您的 DirectX 应用程序的计算密集型部分，并使用从 AMP 计算生成的数据上的 D3D API。  
  
 [Concurrency::fast\_math 命名空间](../../../parallel/amp/reference/concurrency-fast-math-namespace.md)  
 `fast_math` 命名空间中的函数与 C99 不相符。  只提供每个函数的单精度版本。  这些函数使用 DirectX 内部函数，速度比在 `precise_math` 命名空间的相应函数更快，并且不需要扩展的双精度快捷键支持，但精确度不够。  为了实现与 C99 代码的源级别兼容性，每个函数都有两个版本；这两个版本均使用并返回单精度值。  
  
 [Concurrency::graphics 命名空间](../../../parallel/amp/reference/concurrency-graphics-namespace.md)  
 提供专为图形编程设计的类型和功能。  
  
 [Concurrency::precise\_math 命名空间](../../../parallel/amp/reference/concurrency-precise-math-namespace.md)  
 `precise_math` 命名空间中的函数符合 C99。  包括了每个函数的单精度和双精度版本。  包含单精度函数的这些函数要求扩展的双精度快捷键支持。  
  
## 相关章节  
 [C\+\+ AMP \(C\+\+ Accelerated Massive Parallelism\)](../../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)  
 C\+\+ AMP 可加速 C\+\+ 代码执行，方法是通过利用数据并行硬件（通常表示为离散图像卡上的图像处理单元 \(GPU\)）。
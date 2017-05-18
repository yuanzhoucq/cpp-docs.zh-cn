---
title: "参考 (c + + AMP) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- amp/Concurrency::Reference (C++ AMP)
dev_langs:
- C++
helpviewer_keywords:
- C++ Accelerated Massive Parallelism, reference
ms.assetid: 372a8aed-8a53-48c9-996f-9c3cf09c9fa8
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 22ba62ab8b3b4f9d14953dbab3edd8228ea85193
ms.openlocfilehash: cc654cedd8639377ab7011c91454f1508c730247
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="reference-c-amp"></a>参考 (C++ AMP)
本部分包含有关 c + + Accelerated Massive Parallelism (c + + AMP) 运行库的参考信息。  
  
> [!NOTE]
>  C++ 语言标准将保留以下划线 (`_`) 字符开头的标识符，供实现（例如库）使用。 请勿在代码中使用以下划线开头的名称。 其名称遵循此约定的代码元素的行为尚未得到保证，在将来发布的版本中可能会有更改。 出于这些原因，此文档中省略了此类代码元素。  
  
## <a name="in-this-section"></a>本节内容  
 [并发 Namespace (c + + AMP)](concurrency-namespace-cpp-amp.md)  
 提供类和启用 c + + 代码，在数据并行硬件加速的函数。  
  
 [Concurrency:: direct3d Namespace](concurrency-direct3d-namespace.md)  
 提供了支持 D3D 互操作性的函数。 启用无缝使用 D3D 资源 AMP 代码中的计算和在 AMP 中创建在 D3D 代码中，而无需创建多余的中间副本的资源的使用。 C + + AMP 可用于以增量方式加速 DirectX 应用程序的需要进行大量计算部分和对数据产生的 AMP 计算中使用 D3D API。  
  
 [Concurrency:: fast_math Namespace](concurrency-fast-math-namespace.md)  
 中的函数`fast_math`命名空间不符合 C99 标准。 提供了只有单精度的每个函数的版本。 这些函数将使用 DirectX 内部函数，其速度要快于中的相应函数`precise_math`命名空间并不需要扩展的双精度支持加速器，但它们是不太准确。 有两个版本的每个函数的源代码级别与 C99 代码; 的兼容性这两个版本采用并返回单精度值。  
  
 [Concurrency:: graphics Namespace](concurrency-graphics-namespace.md)  
 图形编程提供类型和设计的函数。  
  
 [Concurrency:: precise_math Namespace](concurrency-precise-math-namespace.md)  
 中的函数`precise_math`命名空间是符合 C99。 每个函数的单精度和双精度版本不包括在内。 这些函数，其中包括单精度函数 — 需要扩展的双精度支持加速器。  
  
## <a name="related-sections"></a>相关章节  
 [C++ AMP (C++ Accelerated Massive Parallelism)](../../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)  
 C + + AMP 通过利用通常显示为在离散图形卡上的图形处理单元 (GPU) 的数据并行硬件加快了 c + + 代码的执行。







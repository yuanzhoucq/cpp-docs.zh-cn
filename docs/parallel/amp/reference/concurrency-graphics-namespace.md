---
title: "Concurrency::graphics 命名空间 | Microsoft Docs"
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
  - "amp_graphics/Concurrency::graphics"
  - "amp_short_vectors/Concurrency::graphics"
dev_langs: 
  - "C++"
ms.assetid: 4529d3b1-d7da-4ffb-82bf-080915e0f23e
caps.latest.revision: 14
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Concurrency::graphics 命名空间
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

图像命名空间提供转为图形编程设计的类型和功能。  
  
## 语法  
  
```  
namespace graphics;  
```  
  
## 成员  
  
### 命名空间  
  
|名称|描述|  
|--------|--------|  
|[Concurrency::graphics::direct3d 命名空间](../../../parallel/amp/reference/concurrency-graphics-direct3d-namespace.md)|提供 Direct3D 互操作功能。|  
  
### Typedef  
  
|名称|描述|  
|--------|--------|  
|`uint`|[uint\_2 类](../../../parallel/amp/reference/uint-2-class.md)、[uint\_3 类](../../../parallel/amp/reference/uint-3-class.md) 和 [uint\_4 类](../../../parallel/amp/reference/uint-4-class.md) 的元素类型。  定义为 `typedef unsigned int uint;`。|  
  
### 枚举  
  
|名称|描述|  
|--------|--------|  
|[address\_mode 枚举](../Topic/address_mode%20Enumeration.md)|指定纹理采样支持的地址模式。|  
|[filter\_mode 枚举](../Topic/filter_mode%20Enumeration.md)|指定纹理采样支持的筛选模式。|  
  
### 类  
  
|名称|描述|  
|--------|--------|  
|[texture 类](../../../parallel/amp/reference/texture-class.md)|纹理是在范围域中的 accelerator\_view 上的数据聚合。  它是变量集合，每个元素在范围域中。  每个变量都保留与 C\+\+ 基元类型（无符号整型、整型、浮点型、双精度浮点型）、标量类型 norm 或 unorm（在 concurrency::graphics 中定义）或在 concurrency::graphics 中定义的合格短向量类型相对应的值。|  
|[writeonly\_texture\_view 类](../../../parallel/amp/reference/writeonly-texture-view-class.md)|writeonly\_texture\_view 提供对纹理的 writeonly 访问。|  
|[double\_2 类](../../../parallel/amp/reference/double-2-class.md)|表示 2 个 `double` 值的短矢量。|  
|[double\_3 类](../../../parallel/amp/reference/double-3-class.md)|表示 3 个 `double` 值的短矢量。|  
|[double\_4 类](../../../parallel/amp/reference/double-4-class.md)|表示 4 个 `double` 值的短矢量。|  
|[float\_2 类](../../../parallel/amp/reference/float-2-class.md)|表示 2 个 `float` 值的短矢量。|  
|[float\_3 类](../../../parallel/amp/reference/float-3-class.md)|表示 3 个 `float` 值的短矢量。|  
|[float\_4 类](../../../parallel/amp/reference/float-4-class.md)|表示 4 个 `float` 值的短矢量。|  
|[int\_2 类](../../../parallel/amp/reference/int-2-class.md)|表示 2 个 `int` 值的短矢量。|  
|[int\_3 类](../../../parallel/amp/reference/int-3-class.md)|表示 3 个 `int` 值的短矢量。|  
|[int\_4 类](../../../parallel/amp/reference/int-4-class.md)|表示 4 个 `int` 值的短矢量。|  
|[norm\_2 类](../../../parallel/amp/reference/norm-2-class.md)|表示 2 个 `norm` 值的短矢量。|  
|[norm\_3 类](../../../parallel/amp/reference/norm-3-class.md)|表示 3 个 `norm` 值的短矢量。|  
|[norm\_4 类](../../../parallel/amp/reference/norm-4-class.md)|表示 4 个 `norm` 值的短矢量。|  
|[uint\_2 类](../../../parallel/amp/reference/uint-2-class.md)|表示 2 个 `uint` 值的短矢量。|  
|[uint\_3 类](../../../parallel/amp/reference/uint-3-class.md)|表示 3 个 `uint` 值的短矢量。|  
|[uint\_4 类](../../../parallel/amp/reference/uint-4-class.md)|表示 4 个 `uint` 值的短矢量。|  
|[unorm\_2 类](../../../parallel/amp/reference/unorm-2-class.md)|表示 2 个 `unorm` 值的短矢量。|  
|[unorm\_3 类](../../../parallel/amp/reference/unorm-3-class.md)|表示 3 个 `unorm` 值的短矢量。|  
|[unorm\_4 类](../../../parallel/amp/reference/unorm-4-class.md)|表示 4 个 `unorm` 值的短矢量。|  
|[sampler 类](../../../parallel/amp/reference/sampler-class.md)|表示用于纹理采样的采样器配置。|  
|[short\_vector 结构](../../../parallel/amp/reference/short-vector-structure.md)|提供较短向量值的基本实现。|  
|[short\_vector\_traits 结构](../../../parallel/amp/reference/short-vector-traits-structure.md)|提供简短向量的长度和类型的检索。|  
|[texture\_view 类](../../../parallel/amp/reference/texture-view-class.md)|提供纹理的读取和访问权限。|  
  
### 函数  
  
|名称|描述|  
|--------|--------|  
|[copy 函数](../Topic/copy%20Function.md)|已重载。  将源纹理的内容复制到目标托管缓冲区。|  
|[copy\_async 函数](../Topic/copy_async%20Function.md)|已重载。  异步复制源纹理的内容到目标托管缓冲区。|  
  
## 要求  
 **标头：**amp\_graphics.h  
  
 **命名空间：** 并发  
  
## 请参阅  
 [Concurrency 命名空间 \(C\+\+ AMP\)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)
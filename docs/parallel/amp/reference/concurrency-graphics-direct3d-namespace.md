---
title: "Concurrency::graphics::direct3d 命名空间 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "amp_graphics/Concurrency::graphics::direct3d"
  - "amp_short_vectors/Concurrency::graphics::direct3d"
dev_langs: 
  - "C++"
ms.assetid: be283331-07cf-46e4-91a1-e8aa85d4ec8e
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# Concurrency::graphics::direct3d 命名空间
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

提供 [get\_texture](../Topic/get_texture%20Function.md) 和 [make\_texture](../Topic/make_texture%20Function.md) 方法。  
  
## 语法  
  
```  
namespace direct3d;  
```  
  
## 成员  
  
### 函数  
  
|名称|描述|  
|--------|--------|  
|[get\_sampler 函数](../Topic/get_sampler%20Function.md)|从给定的加速器视图（表示指定的采样器对象）上获取 Direct3D 采样器状态接口。|  
|[get\_texture 函数](../Topic/get_texture%20Function.md)|获取指定[纹理](../../../parallel/amp/reference/texture-class.md)对象的基础 Direct3D 纹理接口。|  
|[make\_sampler 函数](../Topic/make_sampler%20Function.md)|从 Direct3D 采样器状态接口指针创建采样器。|  
|[make\_texture 函数](../Topic/make_texture%20Function.md)|使用指定参数创建[纹理](../../../parallel/amp/reference/texture-class.md)对象。|  
|[msad4 函数](../Topic/msad4%20Function.md)|比较 4 字节引用值和 8 字节源值，并累积 4 个和矢量。|  
  
## 要求  
 **标头：**amp\_graphics.h  
  
 **命名空间：**Concurrency::graphics  
  
## 请参阅  
 [Concurrency::graphics 命名空间](../../../parallel/amp/reference/concurrency-graphics-namespace.md)
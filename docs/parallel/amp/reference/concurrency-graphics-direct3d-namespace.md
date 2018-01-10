---
title: "Concurrency::graphics::direct3d Namespace |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- amp_graphics/Concurrency::graphics::direct3d
- amp_short_vectors/Concurrency::graphics::direct3d
dev_langs: C++
ms.assetid: be283331-07cf-46e4-91a1-e8aa85d4ec8e
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1e5d72b26167a51c6d25e2a9d569ab0424e097a9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="concurrencygraphicsdirect3d-namespace"></a>Concurrency::graphics::direct3d 命名空间
提供[get_texture](concurrency-graphics-direct3d-namespace-functions.md#get_texture)和[make_texture](concurrency-graphics-direct3d-namespace-functions.md#make_texture)方法。  
  
## <a name="syntax"></a>语法  
  
```  
namespace direct3d;  
```  
  
## <a name="members"></a>成员  
  
### <a name="functions"></a>函数  
  
|名称<br /><br /> 描述|  
|--------------------------|  
|[get_sampler](concurrency-graphics-direct3d-namespace-functions.md#get_sampler)<br /><br /> 获取给定的加速器上的 Direct3D 采样器状态接口查看表示的指定的采样器对象。|  
|[get_texture](concurrency-graphics-direct3d-namespace-functions.md#get_texture)<br /><br /> 获取 Direct3D 纹理接口基础指定[纹理](texture-class.md)对象。|  
|[make_sampler](concurrency-graphics-direct3d-namespace-functions.md#make_sampler)<br /><br /> 创建从 Direct3D 采样器状态的接口指针的采样器。|  
|[make_texture](concurrency-graphics-direct3d-namespace-functions.md#make_texture)<br /><br /> 创建[纹理](texture-class.md)通过使用指定的参数的对象。|  
|[msad4](concurrency-graphics-direct3d-namespace-functions.md#msad4)<br /><br /> 将 4 字节的引用值和一个 8 字节源值进行比较，并累积 4 总和向量。|  
  
## <a name="requirements"></a>惠?  
 **标头：** amp_graphics.h  
  
 **Namespace:** concurrency:: graphics  
  
## <a name="see-also"></a>请参阅  
 [Concurrency::graphics 命名空间](concurrency-graphics-namespace.md)

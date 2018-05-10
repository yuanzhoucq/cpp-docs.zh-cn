---
title: 并发命名空间常量 (AMP) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- amp/Concurrency::HLSL_MAX_NUM_BUFFERS
- amp/Concurrency::MODULENAME_MAX_LENGTH
dev_langs:
- C++
ms.assetid: 13a8e8cd-2eec-4e60-a91d-5d271072747b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: adc9aefd059be2932b6903f5c33ada05305d9ed1
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="concurrency-namespace-constants-amp"></a>并发命名空间常量 (AMP)
|||  
|-|-|  
|[HLSL_MAX_NUM_BUFFERS](#hlsl_max_num_buffers)|[MODULENAME_MAX_LENGTH](#modulename_max_length)|  
  
##  <a name="hlsl_max_num_buffers"></a>  HLSL_MAX_NUM_BUFFERS 常量  
 最大允许的 DirectX 的缓冲区数。  
  
```  
static const UINT HLSL_MAX_NUM_BUFFERS = 64 + 128;  
```  
  
##  <a name="modulename_max_length"></a>  MODULENAME_MAX_LENGTH 常量  
 将存储的模块名称的最大长度。 此值必须在编译器和运行时上相同。  
  
```  
static const UINT MODULENAME_MAX_LENGTH = 1024;  
```  
  
## <a name="see-also"></a>请参阅  
 [并发命名空间 (C++ AMP)](concurrency-namespace-cpp-amp.md)

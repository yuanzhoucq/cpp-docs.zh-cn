---
title: "Concurrency::direct3d 命名空间 | Microsoft Docs"
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
  - "amp/Concurrency::direct3d"
  - "amprt/Concurrency::direct3d"
  - "amp_short_vectors/Concurrency::direct3d"
  - "amp_graphics/Concurrency::direct3d"
  - "amp_math/Concurrency::direct3d"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "direct3d 命名空间"
ms.assetid: 9566a2f1-4d5f-43e4-a3ac-676643d38420
caps.latest.revision: 15
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Concurrency::direct3d 命名空间
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`direct3d` 命名空间提供支持 D3D 互操作性的函数。  它允许 D3D 资源在 AMP 中无缝地用于计算以及允许在 D3D 代码中使用 AMP 创建的资源，而无需创建冗余的中间副本。  可通过使用 C\+\+ AMP 来增量加速您的 DirectX 应用程序的计算密集型部分，并使用从 AMP 计算生成的数据上的 D3D API。  
  
## 语法  
  
```  
namespace direct3d;  
```  
  
## 成员  
  
### 类  
  
|名称|描述|  
|--------|--------|  
|[scoped\_d3d\_access\_lock 类](../../../parallel/amp/reference/scoped-d3d-access-lock-class.md)|`accelerator_view` 对象上的 D3D 访问锁的 RAII 包装器。|  
  
### 结构  
  
|名称|描述|  
|--------|--------|  
|[adopt\_d3d\_access\_lock\_t 结构](../../../parallel/amp/reference/adopt-d3d-access-lock-t-structure.md)|应采用而不是获取指示 D3D 访问锁定的标记类型。|  
  
### 函数  
  
|名称|描述|  
|--------|--------|  
|[abs 函数](../Topic/abs%20Function.md)|返回参数的绝对值|  
|[clamp 函数](../Topic/clamp%20Function.md)|已重载。  将 \_X 夹紧到指定的 \_Min 和 \_Max 范围|  
|[countbits 函数](../Topic/countbits%20Function.md)|对 \_X 中的设置位进行计数|  
|[create\_accelerator\_view 函数](../Topic/create_accelerator_view%20Function.md)|创建从指针到 Direct3D 设备接口的 [accelerator\_view 类](../../../parallel/amp/reference/accelerator-view-class.md)|  
|[d3d\_access\_lock 函数](../Topic/d3d_access_lock%20Function.md)|需要出于在与 accelerator\_view 共享的资源上安全执行 D3D 操作的目的锁定 accelerator\_view 视图|  
|[d3d\_access\_try\_lock 函数](../Topic/d3d_access_try_lock%20Function.md)|尝试获取 accelerator\_view 上的 D3D 访问锁,而不受阻止。|  
|[d3d\_access\_unlock 函数](../Topic/d3d_access_unlock%20Function.md)|在给定 accelerator\_view 中释放 D3D 访问锁。|  
|[firstbithigh 函数](../Topic/firstbithigh%20Function.md)|在 \_X 中获取第一组位的位置，从最高序位开始向下执行|  
|[firstbitlow 函数](../Topic/firstbitlow%20Function.md)|在 \_X 中获取第一组位的位置，从最低序位开始向上执行|  
|[get\_buffer 函数](../Topic/get_buffer%20Function.md)|获取数组的基础 D3D 缓冲区接口。|  
|[imax 函数](../Topic/imax%20Function.md)|比较两个值，返回其中较大的值。|  
|[imin 函数](../Topic/imin%20Function.md)|比较两个值，返回其中较小的值。|  
|[is\_timeout\_disabled 函数](../Topic/is_timeout_disabled%20Function.md)|返回布尔标识，该标识指示是否已禁用指定 accelerator\_view 的超时。|  
|[mad 函数](../Topic/mad%20Function.md)|已重载。  对三个参数执行算术乘\/加操作：\_X \* \_Y \+ \_Z|  
|[make\_array 函数](../Topic/make_array%20Function.md)|从 D3D 缓冲区接口指针创建一个数组。|  
|[noise 函数](../Topic/noise%20Function.md)|通过采用 Perlin 降噪算法生成一个随机值|  
|[radians 函数](../Topic/radians%20Function.md)|将 \_X 从度数转换为弧度|  
|[rcp 函数](../Topic/rcp%20Function.md)|快速计算出该参数的倒数的大约值|  
|[reversebits 函数](../Topic/reversebits%20Function.md)|颠倒 \_X 中的位的顺序|  
|[saturate 函数](../Topic/saturate%20Function.md)|将 \_X 夹紧在 0 到 1 之间|  
|[sign 函数](../Topic/sign%20Function.md)|已重载。  返回参数的符号。|  
|[smoothstep 函数](../Topic/smoothstep%20Function.md)|如果 \_X 在 \[\_Min, \_Max\] 的范围中，则返回 0 和 1 之间平滑的 Hermite 插值。|  
|[step 函数](../Topic/step%20Function.md)|比较两个值，根据比较结果返回 0 或 1。|  
|[umax 函数](../Topic/umax%20Function.md)|比较两个无符号的值，返回其中较大的值。|  
|[umin 函数](../Topic/umin%20Function.md)|比较两个无符号的值，返回其中较小的值。|  
  
## 要求  
 **标头：**amp.h  
  
 **命名空间：** 并发  
  
## 请参阅  
 [Concurrency 命名空间 \(C\+\+ AMP\)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)
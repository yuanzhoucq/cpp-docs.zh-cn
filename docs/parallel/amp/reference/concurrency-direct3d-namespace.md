---
title: "Concurrency:: direct3d Namespace |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- amp/Concurrency::direct3d
- amprt/Concurrency::direct3d
- amp_short_vectors/Concurrency::direct3d
- amp_graphics/Concurrency::direct3d
- amp_math/Concurrency::direct3d
dev_langs:
- C++
helpviewer_keywords:
- direct3d namespace
ms.assetid: 9566a2f1-4d5f-43e4-a3ac-676643d38420
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 607a3f25c2dfea5eee833f3608021547d8cd7c44
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="concurrencydirect3d-namespace"></a>Concurrency::direct3d 命名空间
`direct3d`命名空间提供支持 D3D 互操作性的函数。 它使 AMP 代码中的计算 D3D 资源的无缝利用以及允许在 AMP 中创建在 D3D 代码中，而无需创建冗余中间副本的资源的使用。 你可以以增量方式使用 c + + AMP 来加快 DirectX 应用程序的计算密集型部分上和使用 D3D API 从 AMP 计算生成数据。  
  
## <a name="syntax"></a>语法  
  
```  
namespace direct3d;  
```  
  
## <a name="members"></a>成员  
  
### <a name="classes"></a>类  
  
|名称|描述|  
|----------|-----------------|  
|[scoped_d3d_access_lock 类](scoped-d3d-access-lock-class.md)|一种 RAII 包装 D3D 访问锁`accelerator_view`对象。|  
  
### <a name="structures"></a>结构  
  
|名称|描述|  
|----------|-----------------|  
|[adopt_d3d_access_lock_t 结构](adopt-d3d-access-lock-t-structure.md)|而不获取，应采用标记类型以便指示 D3D 访问锁。|  
  
### <a name="functions"></a>函数  
  
|名称|描述|  
|----------|-----------------|  
|[abs](concurrency-direct3d-namespace-functions-amp.md#abs)|返回自变量的绝对值|  
|[clamp](concurrency-direct3d-namespace-functions-amp.md#clamp)|已重载。 Clamps 到指定的 _Min，_Max 范围的 _X|  
|[countbits](concurrency-direct3d-namespace-functions-amp.md#countbits)|计算 _X 中设置位的数目|  
|[create_accelerator_view](concurrency-direct3d-namespace-functions-amp.md#create_accelerator_view)|创建[accelerator_view 类](accelerator-view-class.md)从指向 Direct3D 设备接口的指针|  
|[d3d_access_lock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_lock)|获取上安全地执行与 accelerator_view 共享的资源执行 D3D 操作各种非法 accelerator_view 锁|  
|[d3d_access_try_lock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_try_lock)|尝试获取对 accelerator_view 的 D3D 访问锁定而不阻止。|  
|[d3d_access_unlock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_unlock)|释放 D3D 访问锁在给定的 accelerator_view 上。|  
|[firstbithigh](concurrency-direct3d-namespace-functions-amp.md#firstbithigh)|获取在 _X，从最高顺序位开始和向下使用第一个设置位的位置|  
|[firstbitlow](concurrency-direct3d-namespace-functions-amp.md#firstbitlow)|获取 _X，从最低顺序位开始并向上工作中的第一个设置位的位置|  
|[get_buffer](concurrency-direct3d-namespace-functions-amp.md#get_buffer)|获取基础数组 D3D 缓冲区接口。|  
|[imax](concurrency-direct3d-namespace-functions-amp.md#imax)|比较两个值，返回的值即更大。|  
|[imin](concurrency-direct3d-namespace-functions-amp.md#imin)|比较两个值，返回这是较小的值。|  
|[is_timeout_disabled](concurrency-direct3d-namespace-functions-amp.md#is_timeout_disabled)|返回一个布尔型标志，该值指示是否对指定 accelerator_view 禁用超时。|  
|[mad](concurrency-direct3d-namespace-functions-amp.md#mad)|已重载。 执行上三个自变量的算术乘法/加法操作： _X * _Y + _Z|  
|[make_array](concurrency-direct3d-namespace-functions-amp.md#make_array)|创建从 D3D 缓冲区接口指针的数组。|  
|[noise](concurrency-direct3d-namespace-functions-amp.md#noise)|通过使用 Perlin 噪音算法生成的随机值|  
|[弧度为单位](concurrency-direct3d-namespace-functions-amp.md#radians)|将 _X 从度数转换成弧度|  
|[rcp](concurrency-direct3d-namespace-functions-amp.md#rcp)|计算参数的快速、 近似相互|  
|[reversebits](concurrency-direct3d-namespace-functions-amp.md#reversebits)|_X 中位的顺序反转|  
|[saturate](concurrency-direct3d-namespace-functions-amp.md#saturate)|Clamps 的 0 到 1 范围内的 _X|  
|[sign](concurrency-direct3d-namespace-functions-amp.md#sign)|已重载。 返回自变量的符号|  
|[smoothstep](concurrency-direct3d-namespace-functions-amp.md#smoothstep)|如果 _X 处于范围 [_Min，_Max] 0 和 1 之间，返回平滑 Hermite 内插。|  
|[step](concurrency-direct3d-namespace-functions-amp.md#step)|比较两个值，返回 0 或 1 基于的值大于|  
|[umax](concurrency-direct3d-namespace-functions-amp.md#umax)|比较两个无符号的值，返回的值即更大。|  
|[umin](concurrency-direct3d-namespace-functions-amp.md#umin)|比较两个无符号的值，返回这是较小的值。|  

## <a name="requirements"></a>惠?  
 **标头：** amp.h  
  
 **命名空间：** 并发  
  
## <a name="see-also"></a>请参阅  
 [并发命名空间 (C++ AMP)](concurrency-namespace-cpp-amp.md)

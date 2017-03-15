---
title: "Concurrency:: direct3d Namespace |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 15
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
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: fe9121d6e054446d3adb70da9f78884f4198517e
ms.lasthandoff: 02/24/2017

---
# <a name="concurrencydirect3d-namespace"></a>Concurrency::direct3d 命名空间
`direct3d`命名空间提供支持 D3D 互操作性的函数。 它使无缝使用 D3D 资源 AMP 代码中的计算，以及允许在 AMP 中创建在 D3D 代码中，而无需创建多余的中间副本的资源的使用。 以增量方式可以通过使用 c + + AMP 加快 DirectX 应用程序的计算密集型部分，并对数据产生的 AMP 计算中使用 D3D API。  
  
## <a name="syntax"></a>语法  
  
```  
namespace direct3d;  
```  
  
## <a name="members"></a>成员  
  
### <a name="classes"></a>类  
  
|名称|说明|  
|----------|-----------------|  
|[scoped_d3d_access_lock 类](scoped-d3d-access-lock-class.md)|RAII 包装器上的 D3D 访问锁`accelerator_view`对象。|  
  
### <a name="structures"></a>结构  
  
|名称|描述|  
|----------|-----------------|  
|[adopt_d3d_access_lock_t 结构](adopt-d3d-access-lock-t-structure.md)|而不获取，应采用标记类型以便指示 D3D 访问锁。|  
  
### <a name="functions"></a>函数  
  
|名称|说明|  
|----------|-----------------|  
|[abs 函数](concurrency-direct3d-namespace-functions-amp.md#abs)|返回参数的绝对值|  
|[clamp 函数](concurrency-direct3d-namespace-functions-amp.md#clamp)|已重载。 Clamps 指定 _Min，_Max 范围的 _X|  
|[countbits 函数](concurrency-direct3d-namespace-functions-amp.md#countbits)|计算 _X 中设置位的数目|  
|[create_accelerator_view 函数](concurrency-direct3d-namespace-functions-amp.md#create_accelerator_view)|创建[accelerator_view 类](accelerator-view-class.md)从指向 Direct3D 设备接口的指针|  
|[d3d_access_lock 函数](concurrency-direct3d-namespace-functions-amp.md#d3d_access_lock)|获取用于安全地执行与 accelerator_view 共享资源上的 D3D 操作 accelerator_view 锁|  
|[d3d_access_try_lock 函数](concurrency-direct3d-namespace-functions-amp.md#d3d_access_try_lock)|尝试获取对 accelerator_view 的 D3D 访问锁定而无需阻止。|  
|[d3d_access_unlock 函数](concurrency-direct3d-namespace-functions-amp.md#d3d_access_unlock)|解锁 D3D 访问给定的 accelerator_view 上。|  
|[firstbithigh 函数](concurrency-direct3d-namespace-functions-amp.md#firstbithigh)|获取 _X，从最高顺序位开始并向下拖动工作中的第一个设置位的位置|  
|[firstbitlow 函数](concurrency-direct3d-namespace-functions-amp.md#firstbitlow)|获取 _X，从最低顺序位开始学习并且向上工作中的第一个设置位的位置|  
|[get_buffer 函数](concurrency-direct3d-namespace-functions-amp.md#get_buffer)|获取 D3D 缓冲区接口基础数组。|  
|[imax 函数](concurrency-direct3d-namespace-functions-amp.md#imax)|比较两个值，返回较大的值。|  
|[imin 函数](concurrency-direct3d-namespace-functions-amp.md#imin)|比较两个值，返回其中的较小的值。|  
|[is_timeout_disabled 函数](concurrency-direct3d-namespace-functions-amp.md#is_timeout_disabled)|返回一个布尔型标志，指示是否对指定 accelerator_view 禁用超时。|  
|[mad 函数](concurrency-direct3d-namespace-functions-amp.md#mad)|已重载。 执行三个参数的算术乘法/加法操作︰ _X * _Y + _Z|  
|[make_array 函数](concurrency-direct3d-namespace-functions-amp.md#make_array)|创建从 D3D 缓冲区接口指针的数组。|  
|[noise 函数](concurrency-direct3d-namespace-functions-amp.md#noise)|通过采用 Perlin 噪音算法生成一个随机值|  
|[radians 函数](concurrency-direct3d-namespace-functions-amp.md#radians)|将 _X 从度数转换成弧度|  
|[rcp 函数](concurrency-direct3d-namespace-functions-amp.md#rcp)|计算参数的快速、 近似倒数|  
|[reversebits 函数](concurrency-direct3d-namespace-functions-amp.md#reversebits)|_X 中位的顺序反转|  
|[saturate 函数](concurrency-direct3d-namespace-functions-amp.md#saturate)|Clamps 的 0 到 1 范围内的 _X|  
|[sign 函数](concurrency-direct3d-namespace-functions-amp.md#sign)|已重载。 返回参数的符号|  
|[smoothstep 函数](concurrency-direct3d-namespace-functions-amp.md#smoothstep)|如果 _X 处于范围 [_Min，_Max] 0 和 1 之间，返回平滑 Hermite 内插。|  
|[step 函数](concurrency-direct3d-namespace-functions-amp.md#step)|比较两个值，返回 0 或 1 根据哪个值为更高版本|  
|[umax 函数](concurrency-direct3d-namespace-functions-amp.md#umax)|比较两个无符号的值，返回较大的值。|  
|[umin 函数](concurrency-direct3d-namespace-functions-amp.md#umin)|比较两个无符号的值，返回其中的较小的值。|  

## <a name="requirements"></a>要求  
 **标头：** amp.h  
  
 **命名空间：** 并发  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace (c + + AMP)](concurrency-namespace-cpp-amp.md)


---
title: Concurrency::direct3d 命名空间
ms.date: 11/04/2016
f1_keywords:
- amp/Concurrency::direct3d
- amprt/Concurrency::direct3d
- amp_short_vectors/Concurrency::direct3d
- amp_graphics/Concurrency::direct3d
- amp_math/Concurrency::direct3d
helpviewer_keywords:
- direct3d namespace
ms.assetid: 9566a2f1-4d5f-43e4-a3ac-676643d38420
ms.openlocfilehash: e1374acbd7061afaba372100cf6e69d9d717da8a
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127028"
---
# <a name="concurrencydirect3d-namespace"></a>Concurrency::direct3d 命名空间

`direct3d` 命名空间提供支持 D3D 互操作性的函数。 它允许你使用 D3D 资源进行 AMP 代码计算。 它还允许使用 D3D 代码中创建的资源，而无需创建冗余的中间副本。 你可以使用C++ amp 增量加速 DirectX 应用程序的计算密集型部分，并在从 AMP 计算生成的数据上使用 D3D API。

## <a name="syntax"></a>语法

```cpp
namespace direct3d;
```

## <a name="members"></a>Members

### <a name="classes"></a>类

|名称|说明|
|----------|-----------------|
|[scoped_d3d_access_lock 类](scoped-d3d-access-lock-class.md)|`accelerator_view` 对象上的 D3D 访问锁的 RAII 包装器。|

### <a name="structures"></a>结构

|名称|说明|
|----------|-----------------|
|[adopt_d3d_access_lock_t 结构](adopt-d3d-access-lock-t-structure.md)|标记类型表示应采用 D3D 访问锁定，而不是获得。|

### <a name="functions"></a>函数

|名称|说明|
|----------|-----------------|
|[abs](concurrency-direct3d-namespace-functions-amp.md#abs)|返回参数的绝对值。|
|[固定](concurrency-direct3d-namespace-functions-amp.md#clamp)|已重载。 夹紧 _X 指定的 _Min 和 _Max 范围|
|[countbits](concurrency-direct3d-namespace-functions-amp.md#countbits)|计算 _X 中设置的位数|
|[create_accelerator_view](concurrency-direct3d-namespace-functions-amp.md#create_accelerator_view)|从指向 Direct3D 设备接口的指针创建[Accelerator_view 类](accelerator-view-class.md)|
|[d3d_access_lock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_lock)|获取 accelerator_view 上的锁，以安全地对与 accelerator_view 共享的资源执行 D3D 操作|
|[d3d_access_try_lock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_try_lock)|尝试在不阻止的情况下获取 accelerator_view 上的 D3D 访问锁。|
|[d3d_access_unlock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_unlock)|释放给定 accelerator_view 上的 D3D 访问锁。|
|[firstbithigh](concurrency-direct3d-namespace-functions-amp.md#firstbithigh)|获取 _X 中第一组位的位置，从最高序位开始，到下工作|
|[firstbitlow](concurrency-direct3d-namespace-functions-amp.md#firstbitlow)|获取 _X 中第一组位的位置，从最低顺序位开始，然后向上工作|
|[get_buffer](concurrency-direct3d-namespace-functions-amp.md#get_buffer)|获取数组基础的 D3D 缓冲区接口。|
|[imax](concurrency-direct3d-namespace-functions-amp.md#imax)|比较两个值，并返回大于的值。|
|[imin](concurrency-direct3d-namespace-functions-amp.md#imin)|比较两个值，并返回较小的值。|
|[is_timeout_disabled](concurrency-direct3d-namespace-functions-amp.md#is_timeout_disabled)|返回一个布尔标志，指示是否为指定的 accelerator_view 禁用超时。|
|[mad](concurrency-direct3d-namespace-functions-amp.md#mad)|已重载。 对三个参数执行算术乘法/add 运算： _X \* _Y + _Z|
|[make_array](concurrency-direct3d-namespace-functions-amp.md#make_array)|从 D3D 缓冲区接口指针创建一个数组。|
|[点](concurrency-direct3d-namespace-functions-amp.md#noise)|使用 Perlin 噪声算法生成随机值|
|[π](concurrency-direct3d-namespace-functions-amp.md#radians)|将 _X 从度转换为弧度|
|[rcp](concurrency-direct3d-namespace-functions-amp.md#rcp)|计算自变量的快速、近似倒数|
|[reversebits](concurrency-direct3d-namespace-functions-amp.md#reversebits)|反转 _X 中位的顺序|
|[饱和](concurrency-direct3d-namespace-functions-amp.md#saturate)|夹紧在0到1范围内 _X|
|[sign](concurrency-direct3d-namespace-functions-amp.md#sign)|已重载。 返回参数的符号|
|[smoothstep](concurrency-direct3d-namespace-functions-amp.md#smoothstep)|如果 _X 在 [_Min，_Max] 范围内，则返回介于0和1之间的平滑 Hermite 内插。|
|[分步](concurrency-direct3d-namespace-functions-amp.md#step)|比较两个值，根据哪个值更大返回0或1|
|[umax](concurrency-direct3d-namespace-functions-amp.md#umax)|比较两个无符号值，并返回大于的值。|
|[umin](concurrency-direct3d-namespace-functions-amp.md#umin)|比较两个无符号值，返回较小的值。|

## <a name="requirements"></a>要求

**标头：** amp.h

**命名空间：** 并发

## <a name="see-also"></a>另请参阅

[并发命名空间 (C++ AMP)](concurrency-namespace-cpp-amp.md)

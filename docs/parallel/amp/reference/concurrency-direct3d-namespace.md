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
ms.openlocfilehash: 6afbd7b3a3f4280ad658c1cb9d8802cc3251d0ed
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405477"
---
# <a name="concurrencydirect3d-namespace"></a>Concurrency::direct3d 命名空间

`direct3d`命名空间提供支持 D3D 互操作性的函数。 它可以无缝使用 D3D 资源在 AMP 代码中的计算以及允许使用的资源在 AMP 中创建在 D3D 代码中，而无需创建冗余的中间副本。 用户能够以增量方式加快 DirectX 应用程序的计算密集型部分，通过使用C++AMP，然后使用从 AMP 计算生成的数据上的 D3D API。

## <a name="syntax"></a>语法

```
namespace direct3d;
```

## <a name="members"></a>成员

### <a name="classes"></a>类

|名称|描述|
|----------|-----------------|
|[scoped_d3d_access_lock 类](scoped-d3d-access-lock-class.md)|上的 D3D 访问锁的 RAII 包装器`accelerator_view`对象。|

### <a name="structures"></a>结构

|名称|描述|
|----------|-----------------|
|[adopt_d3d_access_lock_t 结构](adopt-d3d-access-lock-t-structure.md)|而不获取，应采用标记类型，以指示 D3D 访问锁。|

### <a name="functions"></a>函数

|名称|描述|
|----------|-----------------|
|[abs](concurrency-direct3d-namespace-functions-amp.md#abs)|返回自变量的绝对值|
|[clamp](concurrency-direct3d-namespace-functions-amp.md#clamp)|已重载。 将指定的 _Min 和 _Max 范围内的 _X 夹紧|
|[countbits](concurrency-direct3d-namespace-functions-amp.md#countbits)|计算 _X 中的设置位的数目|
|[create_accelerator_view](concurrency-direct3d-namespace-functions-amp.md#create_accelerator_view)|创建[accelerator_view 类](accelerator-view-class.md)从指针到 Direct3D 设备接口|
|[d3d_access_lock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_lock)|获取出于安全执行 D3D 操作在与 accelerator_view 共享的资源锁|
|[d3d_access_try_lock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_try_lock)|尝试获取 accelerator_view 上的 D3D 访问锁而不会阻塞。|
|[d3d_access_unlock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_unlock)|发布给定 accelerator_view 上的 D3D 访问锁。|
|[firstbithigh](concurrency-direct3d-namespace-functions-amp.md#firstbithigh)|获取 _X，从最高顺序位开始，并向下处理中的第一组位的位置|
|[firstbitlow](concurrency-direct3d-namespace-functions-amp.md#firstbitlow)|获取 _X，从最低顺序位开始，并使用向上中第一组位的位置|
|[get_buffer](concurrency-direct3d-namespace-functions-amp.md#get_buffer)|获取数组的基础 D3D 缓冲区接口。|
|[imax](concurrency-direct3d-namespace-functions-amp.md#imax)|比较两个值，返回其中较大的值。|
|[imin](concurrency-direct3d-namespace-functions-amp.md#imin)|比较两个值，返回其中较小的值。|
|[is_timeout_disabled](concurrency-direct3d-namespace-functions-amp.md#is_timeout_disabled)|返回一个布尔标志，指示是否针对 accelerator_view 禁用超时。|
|[mad](concurrency-direct3d-namespace-functions-amp.md#mad)|已重载。 执行算术乘/加操作对三个参数： _X \* _Y + _Z|
|[make_array](concurrency-direct3d-namespace-functions-amp.md#make_array)|从 D3D 缓冲区接口指针创建一个数组。|
|[noise](concurrency-direct3d-namespace-functions-amp.md#noise)|通过采用 Perlin 噪音算法生成一个随机值|
|[radians](concurrency-direct3d-namespace-functions-amp.md#radians)|将 _X 从度数转换为弧度|
|[rcp](concurrency-direct3d-namespace-functions-amp.md#rcp)|计算参数的快速、 近似倒数|
|[reversebits](concurrency-direct3d-namespace-functions-amp.md#reversebits)|颠倒 _X 中位的顺序|
|[saturate](concurrency-direct3d-namespace-functions-amp.md#saturate)|将为 0 到 1 范围内的 _X 夹紧|
|[sign](concurrency-direct3d-namespace-functions-amp.md#sign)|已重载。 返回自变量的符号|
|[smoothstep](concurrency-direct3d-namespace-functions-amp.md#smoothstep)|如果 _X 处于范围 [_Min，_Max] 将返回介于 0 和 1 之间平滑的 Hermite 插值。|
|[step](concurrency-direct3d-namespace-functions-amp.md#step)|比较两个值，返回 0 或 1 基于的值大于|
|[umax](concurrency-direct3d-namespace-functions-amp.md#umax)|比较两个无符号的值，返回其中较大的值。|
|[umin](concurrency-direct3d-namespace-functions-amp.md#umin)|比较两个无符号的值，返回其中较小的值。|

## <a name="requirements"></a>要求

**标头：** amp.h

**命名空间：** 并发

## <a name="see-also"></a>请参阅

[并发命名空间 (C++ AMP)](concurrency-namespace-cpp-amp.md)

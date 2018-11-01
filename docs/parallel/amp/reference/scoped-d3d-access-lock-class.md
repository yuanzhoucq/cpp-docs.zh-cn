---
title: scoped_d3d_access_lock 类
ms.date: 11/04/2016
f1_keywords:
- scoped_d3d_access_lock
- AMPRT/scoped_d3d_access_lock
- AMPRT/concurrency::direct3d::scoped_d3d_access_lock::scoped_d3d_access_lock
ms.assetid: 0ad333e6-9839-4736-a722-16d95d70c4b1
ms.openlocfilehash: 08b6edc415d08d6dfb863fb90ff27bac6ce0960a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50598440"
---
# <a name="scopedd3daccesslock-class"></a>scoped_d3d_access_lock 类

视图对象上的 D3D 访问锁的 RAII 包装器。

### <a name="syntax"></a>语法

```
class scoped_d3d_access_lock;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[scoped_d3d_access_lock 构造函数](#ctor)|已重载。 构造 `scoped_d3d_access_lock` 对象。 当此对象超出范围时释放锁。|
|[~ scoped_d3d_access_lock 析构函数](#dtor)|释放关联的 D3D 访问锁`accelerator_view`对象。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[operator=](#operator_eq)|将从另一锁的所有权`scoped_d3d_access_lock`。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`scoped_d3d_access_lock`

## <a name="requirements"></a>要求

**标头：** amprt.h

**Namespace:** concurrency::direct3d

##  <a name="ctor"></a> scoped_d3d_access_lock

构造 `scoped_d3d_access_lock` 对象。 当此对象超出范围时释放锁。

```
explicit scoped_d3d_access_lock(// [1] constructor
    accelerator_view& _Av);

explicit scoped_d3d_access_lock(// [2] constructor
    accelerator_view& _Av,
    adopt_d3d_access_lock_t _T);

scoped_d3d_access_lock(// [3] move constructor
    scoped_d3d_access_lock&& _Other);
```

### <a name="parameters"></a>参数

*_Av*<br/>
`accelerator_view`为要采用的锁。

*_T*<br/>
`adopt_d3d_access_lock_t` 对象。

*_Other*<br/>
`scoped_d3d_access_lock`要移出现有锁对象。

## <a name="construction"></a>构造

[1] 构造函数上获取 D3D 访问锁给定[accelerator_view](accelerator-view-class.md)对象。 构造块，直到已获取锁。

[2] 构造函数采用 D3D 访问锁从给定[accelerator_view](accelerator-view-class.md)对象。

[3] 移动构造函数采用从另一个现有 D3D 访问锁`scoped_d3d_access_lock`对象。 构造不会阻止。

##  <a name="dtor"></a> ~scoped_d3d_access_lock

释放关联的 D3D 访问锁`accelerator_view`对象。

```
~scoped_d3d_access_lock();
```

## <a name="operator_eq"></a> 运算符 =

从另一个的 D3D 访问锁的所有权`scoped_d3d_access_lock`对象，释放上一个锁。

```
scoped_d3d_access_lock& operator= (scoped_d3d_access_lock&& _Other);
```

### <a name="parameters"></a>参数

*_Other*<br/>
它将移动 D3D 访问锁的 accelerator_view。

### <a name="return-value"></a>返回值

对此引用`scoped_accelerator_view_lock`。

## <a name="see-also"></a>请参阅

[Concurrency::direct3d 命名空间](concurrency-direct3d-namespace.md)

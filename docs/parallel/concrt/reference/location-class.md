---
title: location 类
ms.date: 11/04/2016
f1_keywords:
- location
- CONCRT/concurrency::location
- CONCRT/concurrency::location::location
- CONCRT/concurrency::location::current
- CONCRT/concurrency::location::from_numa_node
helpviewer_keywords:
- location class
ms.assetid: c3289f51-5bf1-4dff-a18d-d0dab8e5d9c7
ms.openlocfilehash: 848be3131e23ff53f2dec16364b132ee7c218195
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87182689"
---
# <a name="location-class"></a>location 类

硬件上物理位置的抽象。

## <a name="syntax"></a>语法

```cpp
class location;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[位置](#ctor)|已重载。 构造 `location` 对象。|
|[~ location 析构函数](#dtor)|销毁 `location` 对象。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[当前](#current)|返回表示调用线程执行的最具体位置的 `location` 对象。|
|[from_numa_node](#from_numa_node)|返回表示给定的 NUMA 节点的 `location` 对象。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[operator！ =](#operator_neq)|确定两个 `location` 对象是否表示不同的位置。|
|[operator =](#operator_eq)|将另一 `location` 对象的内容分配给此对象。|
|[operator = =](#operator_eq_eq)|确定两个 `location` 对象是否表示同一位置。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`location`

## <a name="requirements"></a>要求

**标头：** concrt

**命名空间：** 并发

## <a name="location"></a><a name="dtor"></a>~ location

销毁 `location` 对象。

```cpp
~location();
```

## <a name="current"></a><a name="current"></a>当前

返回表示调用线程执行的最具体位置的 `location` 对象。

```cpp
static location __cdecl current();
```

### <a name="return-value"></a>返回值

表示调用线程执行的最具体位置的位置。

## <a name="from_numa_node"></a><a name="from_numa_node"></a>from_numa_node

返回表示给定的 NUMA 节点的 `location` 对象。

```cpp
static location __cdecl from_numa_node(unsigned short _NumaNodeNumber);
```

### <a name="parameters"></a>参数

*_NumaNodeNumber*<br/>
要构造位置的 NUMA 节点号。

### <a name="return-value"></a>返回值

表示 `_NumaNodeNumber` 参数指定的 NUMA 节点的位置。

## <a name="location"></a><a name="ctor"></a>位置

构造 `location` 对象。

```cpp
location();

location(
    const location& _Src);

location(
    T _LocationType,
    unsigned int _Id,
    unsigned int _BindingId = 0,
    _Inout_opt_ void* _PBinding = NULL);
```

### <a name="parameters"></a>参数

*_Src*<br/>

*_LocationType*<br/>

*_Id*<br/>

*_BindingId*<br/>

*_PBinding*<br/>
可有可无绑定指针。

### <a name="remarks"></a>备注

默认构造的位置表示整个系统。

## <a name="operator"></a><a name="operator_neq"></a>operator！ =

确定两个 `location` 对象是否表示不同的位置。

```cpp
bool operator!= (const location& _Rhs) const;
```

### <a name="parameters"></a>参数

*_Rhs*<br/>
操作数 `location` 。

### <a name="return-value"></a>返回值

**`true`** 如果两个位置不同，则 **`false`** 为; 否则为。

## <a name="operator"></a><a name="operator_eq"></a>operator =

将另一 `location` 对象的内容分配给此对象。

```cpp
location& operator= (const location& _Rhs);
```

### <a name="parameters"></a>参数

*_Rhs*<br/>
源 `location` 对象。

### <a name="return-value"></a>返回值

## <a name="operator"></a><a name="operator_eq_eq"></a>operator = =

确定两个 `location` 对象是否表示同一位置。

```cpp
bool operator== (const location& _Rhs) const;
```

### <a name="parameters"></a>参数

*_Rhs*<br/>
操作数 `location` 。

### <a name="return-value"></a>返回值

**`true`** 如果两个位置相同，则 **`false`** 为; 否则为。

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)

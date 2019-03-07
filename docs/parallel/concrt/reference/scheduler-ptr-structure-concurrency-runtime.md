---
title: scheduler_ptr 结构
ms.date: 11/04/2016
f1_keywords:
- scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::get
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::operator bool
ms.assetid: e88c84af-c306-476d-aef1-f42a0fa0a80f
ms.openlocfilehash: 2373fe3bc8cac501d1b6b32ca66996eff47ba6f3
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57295040"
---
# <a name="schedulerptr-structure"></a>scheduler_ptr 结构

表示指向计划程序的指针。 此类存在是为了通过使用 shared_ptr 或无格式引用通过使用原始指针允许指定共享生存期。

## <a name="syntax"></a>语法

```
struct scheduler_ptr;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[scheduler_ptr::scheduler_ptr](#ctor)|已重载。 创建一个从 shared_ptr 到计划程序的计划程序指针|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[scheduler_ptr::get](#get)|返回指向计划程序的原始指针|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[scheduler_ptr::operator bool](#operator_bool)|测试计划程序指针是否为非 null|
|[scheduler_ptr::operator-&gt;](#operator_ptr)|行为类似于指针|

## <a name="inheritance-hierarchy"></a>继承层次结构

`scheduler_ptr`

## <a name="requirements"></a>要求

**标头：** pplinterface.h

**命名空间：** 并发

##  <a name="get"></a>  scheduler_ptr:: get 方法

返回到计划程序的原始指针。

```
scheduler_interface* get() const;
```

### <a name="return-value"></a>返回值

##  <a name="operator_bool"></a>  scheduler_ptr::operator bool

测试计划程序指针是否不为 null。

```
operator bool() const;
```

##  <a name="operator_ptr"></a>  scheduler_ptr::operator-&gt;

类似于指针的行为。

```
scheduler_interface* operator->() const;
```

### <a name="return-value"></a>返回值

##  <a name="ctor"></a>  scheduler_ptr:: scheduler_ptr 构造函数

从 shared_ptr 到计划程序创建的计划程序指针。

```
explicit scheduler_ptr(std::shared_ptr<scheduler_interface> scheduler);
explicit scheduler_ptr(_In_opt_ scheduler_interface* pScheduler);
```

### <a name="parameters"></a>参数

*scheduler*<br/>
计划程序进行转换。

*pScheduler*<br/>
要转换的计划程序指针。

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)

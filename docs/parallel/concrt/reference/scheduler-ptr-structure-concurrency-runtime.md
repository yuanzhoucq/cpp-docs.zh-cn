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
ms.openlocfilehash: fd044a6255a17882c26183223f71564f98c9f7b2
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142775"
---
# <a name="scheduler_ptr-structure"></a>scheduler_ptr 结构

表示指向计划程序的指针。 此类可用于通过使用 shared_ptr 或仅通过使用原始指针来指定共享生存期。

## <a name="syntax"></a>语法

```cpp
struct scheduler_ptr;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[scheduler_ptr：： scheduler_ptr](#ctor)|已重载。 创建一个从 shared_ptr 到计划程序的计划程序指针|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[scheduler_ptr：： get](#get)|返回指向计划程序的原始指针|

### <a name="public-operators"></a>公用運算子

|名称|说明|
|----------|-----------------|
|[scheduler_ptr：： operator bool](#operator_bool)|测试计划程序指针是否为非 null|
|[scheduler_ptr：： operator-&gt;](#operator_ptr)|行为类似于指针|

## <a name="inheritance-hierarchy"></a>继承层次结构

`scheduler_ptr`

## <a name="requirements"></a>要求

**标头：** pplinterface。h

**命名空间：** 并发

## <a name="get"></a>scheduler_ptr：： get 方法

返回指向计划程序的原始指针。

```cpp
scheduler_interface* get() const;
```

### <a name="return-value"></a>返回值

## <a name="operator_bool"></a>scheduler_ptr：： operator bool

测试计划程序指针是否为非 null。

```cpp
operator bool() const;
```

## <a name="operator_ptr"></a>scheduler_ptr：： operator-&gt;

的行为类似于指针。

```cpp
scheduler_interface* operator->() const;
```

### <a name="return-value"></a>返回值

## <a name="ctor"></a>scheduler_ptr：： scheduler_ptr 构造函数

创建从 shared_ptr 到计划程序的计划程序指针。

```cpp
explicit scheduler_ptr(std::shared_ptr<scheduler_interface> scheduler);
explicit scheduler_ptr(_In_opt_ scheduler_interface* pScheduler);
```

### <a name="parameters"></a>参数

*日程*<br/>
要转换的计划程序。

*pScheduler*<br/>
要转换的计划程序指针。

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)

---
title: scheduler_ptr结构
ms.date: 11/04/2016
f1_keywords:
- scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::get
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::operator bool
ms.assetid: e88c84af-c306-476d-aef1-f42a0fa0a80f
ms.openlocfilehash: 60d71a26e5dffcadfb900ef15c26a6d9dc6d6f8b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358772"
---
# <a name="scheduler_ptr-structure"></a>scheduler_ptr结构

表示指向计划程序的指针。 此类的存在是为了通过使用shared_ptr或仅使用原始指针进行简单引用来规范共享生存期。

## <a name="syntax"></a>语法

```cpp
struct scheduler_ptr;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[scheduler_ptr：：scheduler_ptr](#ctor)|已重载。 创建一个从 shared_ptr 到计划程序的计划程序指针|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[scheduler_ptr：获取](#get)|返回指向计划程序的原始指针|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[scheduler_ptr：：操作员布尔](#operator_bool)|测试计划程序指针是否为非 null|
|[scheduler_ptr：操作员-&gt;](#operator_ptr)|行为类似于指针|

## <a name="inheritance-hierarchy"></a>继承层次结构

`scheduler_ptr`

## <a name="requirements"></a>要求

**标题：** pplinterface.h

**命名空间：** 并发

## <a name="scheduler_ptrget-method"></a><a name="get"></a>scheduler_ptr：获取方法

返回指向计划程序的原始指针。

```cpp
scheduler_interface* get() const;
```

### <a name="return-value"></a>返回值

## <a name="scheduler_ptroperator-bool"></a><a name="operator_bool"></a>scheduler_ptr：：操作员布尔

测试计划程序指针是否为非空。

```cpp
operator bool() const;
```

## <a name="scheduler_ptroperator-gt"></a><a name="operator_ptr"></a>scheduler_ptr：操作员-&gt;

像指针一样。

```cpp
scheduler_interface* operator->() const;
```

### <a name="return-value"></a>返回值

## <a name="scheduler_ptrscheduler_ptr-constructor"></a><a name="ctor"></a>scheduler_ptr：scheduler_ptr构造函数

从shared_ptr创建计划程序指针到计划程序。

```cpp
explicit scheduler_ptr(std::shared_ptr<scheduler_interface> scheduler);
explicit scheduler_ptr(_In_opt_ scheduler_interface* pScheduler);
```

### <a name="parameters"></a>参数

*调度*<br/>
要转换的计划程序。

*p时间*<br/>
要转换的计划程序指针。

## <a name="see-also"></a>另请参阅

[concurrency 命名空间](concurrency-namespace.md)

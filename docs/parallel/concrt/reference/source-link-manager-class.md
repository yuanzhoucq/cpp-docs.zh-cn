---
title: source_link_manager 类
ms.date: 11/04/2016
f1_keywords:
- source_link_manager
- AGENTS/concurrency::source_link_manager
- AGENTS/concurrency::source_link_manager::source_link_manager
- AGENTS/concurrency::source_link_manager::add
- AGENTS/concurrency::source_link_manager::begin
- AGENTS/concurrency::source_link_manager::contains
- AGENTS/concurrency::source_link_manager::count
- AGENTS/concurrency::source_link_manager::reference
- AGENTS/concurrency::source_link_manager::register_target_block
- AGENTS/concurrency::source_link_manager::release
- AGENTS/concurrency::source_link_manager::remove
- AGENTS/concurrency::source_link_manager::set_bound
helpviewer_keywords:
- source_link_manager class
ms.assetid: 287487cf-e0fe-4c35-aa3c-24f081d1ddae
ms.openlocfilehash: d4979eaf9065183be646be72cfdd5a94500edf55
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57295196"
---
# <a name="sourcelinkmanager-class"></a>source_link_manager 类


  `source_link_manager` 对象管理到 `ISource` 块的消息块网络链接。

## <a name="syntax"></a>语法

```
template<class _LinkRegistry>
class source_link_manager;
```

#### <a name="parameters"></a>参数

*_LinkRegistry*<br/>
网络链接注册表中。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|描述|
|----------|-----------------|
|`const_pointer`|提供一个指针指向的类型`const`中的元素`source_link_manager`对象。|
|`const_reference`|提供对引用的类型`const`元素存储在`source_link_manager`用于读取和执行 const 操作的对象。|
|`iterator`|提供的迭代器的类型可读取或修改中的任何元素`source_link_manager`对象。|
|`type`|由链接注册表类型`source_link_manager`对象。|

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[source_link_manager](#ctor)|构造 `source_link_manager` 对象。|
|[~ source_link_manager 析构函数](#dtor)|销毁`source_link_manager`对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[add](#add)|添加源链接到`source_link_manager`对象。|
|[begin](#begin)|返回一个迭代器中的第一个元素到`source_link_manager`对象。|
|[contains](#contains)|搜索`network_link_registry`在此`source_link_manager`指定块的对象。|
|[count](#count)|中的链接块的计数`source_link_manager`对象。|
|[reference](#reference)|获取引用上`source_link_manager`对象。|
|[register_target_block](#register_target_block)|注册持有此目标块`source_link_manager`对象。|
|[release](#release)|在释放的引用`source_link_manager`对象。|
|[remove](#remove)|移除从链接`source_link_manager`对象。|
|[set_bound](#set_bound)|设置源链接，可以添加到此最大数目`source_link_manager`对象。|

## <a name="remarks"></a>备注

目前，源块是引用计数。 这是一个包装上`network_link_registry`对象，它允许对链接的并发访问，并提供能够引用通过回调的链接。 消息块 ( `target_block`s 或`propagator_block`s) 应使用此类用于其源链接。

## <a name="inheritance-hierarchy"></a>继承层次结构

`source_link_manager`

## <a name="requirements"></a>要求

**标头：** agents.h

**命名空间：** 并发

##  <a name="add"></a> add

添加源链接到`source_link_manager`对象。

```
void add(_EType _Link);
```

### <a name="parameters"></a>参数

*_Link*<br/>
指向要添加的块的指针。

##  <a name="begin"></a> begin

返回一个迭代器中的第一个元素到`source_link_manager`对象。

```
iterator begin();
```

### <a name="return-value"></a>返回值

中的第一个元素的迭代器`source_link_manager`对象。

### <a name="remarks"></a>备注

迭代器的最终状态由`NULL`链接。

##  <a name="contains"></a> 包含

搜索`network_link_registry`在此`source_link_manager`指定块的对象。

```
bool contains(_EType _Link);
```

### <a name="parameters"></a>参数

*_Link*<br/>
指向要在其中搜索中的块的指针`source_link_manager`对象。

### <a name="return-value"></a>返回值

**true**如果未找到指定的块， **false**否则为。

##  <a name="count"></a> count

中的链接块的计数`source_link_manager`对象。

```
size_t count();
```

### <a name="return-value"></a>返回值

在链接的块数`source_link_manager`对象。

##  <a name="reference"></a> 引用

获取引用上`source_link_manager`对象。

```
void reference();
```

##  <a name="register_target_block"></a> register_target_block

注册持有此目标块`source_link_manager`对象。

```
void register_target_block(_Inout_ ITarget<typename _Block::source_type>* _PTarget);
```

### <a name="parameters"></a>参数

*_PTarget*<br/>
持有此目标块`source_link_manager`对象。

##  <a name="release"></a> 版本

在释放的引用`source_link_manager`对象。

```
void release();
```

##  <a name="remove"></a> 删除

移除从链接`source_link_manager`对象。

```
bool remove(_EType _Link);
```

### <a name="parameters"></a>参数

*_Link*<br/>
指向块被删除，如果找到。

### <a name="return-value"></a>返回值

**true**找到该链接并将其删除，如果**false**否则为。

##  <a name="set_bound"></a> set_bound

设置源链接，可以添加到此最大数目`source_link_manager`对象。

```
void set_bound(size_t _MaxLinks);
```

### <a name="parameters"></a>参数

*_MaxLinks*<br/>
最大链接数。

##  <a name="ctor"></a> source_link_manager

构造 `source_link_manager` 对象。

```
source_link_manager();
```

##  <a name="dtor"></a> ~source_link_manager

销毁`source_link_manager`对象。

```
~source_link_manager();
```

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[single_link_registry 类](single-link-registry-class.md)<br/>
[multi_link_registry 类](multi-link-registry-class.md)

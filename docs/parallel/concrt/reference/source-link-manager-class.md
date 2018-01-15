---
title: "source_link_manager 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
helpviewer_keywords: source_link_manager class
ms.assetid: 287487cf-e0fe-4c35-aa3c-24f081d1ddae
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 67cf15c6681c989a2da2b4e6824fec6012c517bf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="sourcelinkmanager-class"></a>source_link_manager 类
`source_link_manager` 对象管理到 `ISource` 块的消息块网络链接。  
  
## <a name="syntax"></a>语法  
  
```
template<class _LinkRegistry>
class source_link_manager;
```  
  
#### <a name="parameters"></a>参数  
 `_LinkRegistry`  
 网络链接注册表中。  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|描述|  
|----------|-----------------|  
|`const_pointer`|提供指向的指针的类型`const`中的元素`source_link_manager`对象。|  
|`const_reference`|提供对引用的类型`const`元素存储在`source_link_manager`用于读取和执行 const 操作的对象。|  
|`iterator`|提供一个迭代器的类型，可读取或修改中的任意元素`source_link_manager`对象。|  
|`type`|一种由链接注册表`source_link_manager`对象。|  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[source_link_manager](#ctor)|构造 `source_link_manager` 对象。|  
|[~ source_link_manager 析构函数](#dtor)|销毁`source_link_manager`对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[add](#add)|将添加到的源链接`source_link_manager`对象。|  
|[begin](#begin)|返回的第一个元素的迭代器`source_link_manager`对象。|  
|[包含](#contains)|搜索`network_link_registry`在此`source_link_manager`对象指定的块。|  
|[count](#count)|计算中的链接块数目`source_link_manager`对象。|  
|[reference](#reference)|上获取引用`source_link_manager`对象。|  
|[register_target_block](#register_target_block)|注册持有此目标块`source_link_manager`对象。|  
|[release](#release)|在释放引用`source_link_manager`对象。|  
|[remove](#remove)|删除从链接`source_link_manager`对象。|  
|[set_bound](#set_bound)|设置的最大的源链接，可以添加到此`source_link_manager`对象。|  
  
## <a name="remarks"></a>备注  
 目前，源块均被引用计数。 这是包装上`network_link_registry`对象，允许对链接的并发访问并能够引用通过回调的链接。 消息块 ( `target_block`s 或`propagator_block`s) 应使用此类用于其源链接。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `source_link_manager`  
  
## <a name="requirements"></a>惠?  
 **标头：** agents.h  
  
 **命名空间：** 并发  
  
##  <a name="add"></a>添加 

 将添加到的源链接`source_link_manager`对象。  
  
```
void add(_EType _Link);
```  
  
### <a name="parameters"></a>参数  
 `_Link`  
 指向要添加的块的指针。  
  
##  <a name="begin"></a>开始 

 返回的第一个元素的迭代器`source_link_manager`对象。  
  
```
iterator begin();
```  
  
### <a name="return-value"></a>返回值  
 发现的第一个元素的迭代器`source_link_manager`对象。  
  
### <a name="remarks"></a>备注  
 迭代器的最终状态由`NULL`链接。  
  
##  <a name="contains"></a>包含 

 搜索`network_link_registry`在此`source_link_manager`对象指定的块。  
  
```
bool contains(_EType _Link);
```  
  
### <a name="parameters"></a>参数  
 `_Link`  
 指向要在其中搜索中的块的指针`source_link_manager`对象。  
  
### <a name="return-value"></a>返回值  
 `true`如果找到指定的块，`false`否则为。  
  
##  <a name="count"></a>计数 

 计算中的链接块数目`source_link_manager`对象。  
  
```
size_t count();
```  
  
### <a name="return-value"></a>返回值  
 中的链接块的数量`source_link_manager`对象。  
  
##  <a name="reference"></a>引用 

 上获取引用`source_link_manager`对象。  
  
```
void reference();
```  
  
##  <a name="register_target_block"></a>register_target_block 

 注册持有此目标块`source_link_manager`对象。  
  
```
void register_target_block(_Inout_ ITarget<typename _Block::source_type>* _PTarget);
```  
  
### <a name="parameters"></a>参数  
 `_PTarget`  
 目标块持有这`source_link_manager`对象。  
  
##  <a name="release"></a>版本 

 在释放引用`source_link_manager`对象。  
  
```
void release();
```  
  
##  <a name="remove"></a>删除 

 删除从链接`source_link_manager`对象。  
  
```
bool remove(_EType _Link);
```  
  
### <a name="parameters"></a>参数  
 `_Link`  
 指向块被删除，如果找到。  
  
### <a name="return-value"></a>返回值  
 `true`如果找到并移除了，链接`false`否则为。  
  
##  <a name="set_bound"></a>set_bound 

 设置的最大的源链接，可以添加到此`source_link_manager`对象。  
  
```
void set_bound(size_t _MaxLinks);
```  
  
### <a name="parameters"></a>参数  
 `_MaxLinks`  
 最大连接数。  
  
##  <a name="ctor"></a>source_link_manager 

 构造 `source_link_manager` 对象。  
  
```
source_link_manager();
```  
  
##  <a name="dtor"></a>~ source_link_manager 

 销毁`source_link_manager`对象。  
  
```
~source_link_manager();
```  
  
## <a name="see-also"></a>请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [single_link_registry 类](single-link-registry-class.md)   
 [multi_link_registry 类](multi-link-registry-class.md)

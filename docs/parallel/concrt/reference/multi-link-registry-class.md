---
title: multi_link_registry 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- multi_link_registry
- AGENTS/concurrency::multi_link_registry
- AGENTS/concurrency::multi_link_registry::multi_link_registry
- AGENTS/concurrency::multi_link_registry::add
- AGENTS/concurrency::multi_link_registry::begin
- AGENTS/concurrency::multi_link_registry::contains
- AGENTS/concurrency::multi_link_registry::count
- AGENTS/concurrency::multi_link_registry::remove
- AGENTS/concurrency::multi_link_registry::set_bound
dev_langs:
- C++
helpviewer_keywords:
- multi_link_registry class
ms.assetid: b2aa73a8-e8a6-4255-b117-d07530c328b2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5fbe52298f267fabb2ba326e3e1c7b66f4ad49ef
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33688929"
---
# <a name="multilinkregistry-class"></a>multi_link_registry 类
`multi_link_registry` 对象是管理多个源块或多个目标块的 `network_link_registry`。  
  
## <a name="syntax"></a>语法  
  
```
template<class _Block>
class multi_link_registry : public network_link_registry<_Block>;
```  
  
#### <a name="parameters"></a>参数  
 `_Block`  
 块数据类型存储在`multi_link_registry`对象。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[multi_link_registry](#ctor)|构造 `multi_link_registry` 对象。|  
|[~ multi_link_registry 析构函数](#dtor)|销毁`multi_link_registry`对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[add](#add)|将添加到链接`multi_link_registry`对象。 (重写[network_link_registry:: add](network-link-registry-class.md#add)。)|  
|[begin](#begin)|返回的第一个元素的迭代器`multi_link_registry`对象。 (重写[network_link_registry:: begin](network-link-registry-class.md#begin)。)|  
|[包含](#contains)|搜索`multi_link_registry`对象指定的块。 (重写[network_link_registry:: contains](network-link-registry-class.md#contains)。)|  
|[count](#count)|计算中的项的数目`multi_link_registry`对象。 (重写[network_link_registry:: count](network-link-registry-class.md#count)。)|  
|[remove](#remove)|删除从链接`multi_link_registry`对象。 (重写[network_link_registry:: remove](network-link-registry-class.md#remove)。)|  
|[set_bound](#set_bound)|上的链接数设置上限`multi_link_registry`对象可以保留。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [network_link_registry](network-link-registry-class.md)  
  
 `multi_link_registry`  
  
## <a name="requirements"></a>要求  
 **标头：** agents.h  
  
 **命名空间：** 并发  
  
##  <a name="add"></a> 添加 

 将添加到链接`multi_link_registry`对象。  
  
```
virtual void add(_EType _Link);
```  
  
### <a name="parameters"></a>参数  
 `_Link`  
 指向要添加的块的指针。  
  
### <a name="remarks"></a>备注  
 该方法将引发[invalid_link_target](invalid-link-target-class.md)异常如果链接已存在，则在注册表中，或如果绑定已设置与`set_bound`函数和链接已被删除。  
  
##  <a name="begin"></a> 开始 

 返回的第一个元素的迭代器`multi_link_registry`对象。  
  
```
virtual iterator begin();
```  
  
### <a name="return-value"></a>返回值  
 发现的第一个元素的迭代器`multi_link_registry`对象。  
  
### <a name="remarks"></a>备注  
 最终状态由`NULL`链接。  
  
##  <a name="contains"></a> 包含 

 搜索`multi_link_registry`对象指定的块。  
  
```
virtual bool contains(_EType _Link);
```  
  
### <a name="parameters"></a>参数  
 `_Link`  
 指向要在其中搜索中的块的指针`multi_link_registry`对象。  
  
### <a name="return-value"></a>返回值  
 `true` 如果找到指定的块，`false`否则为。  
  
##  <a name="count"></a> 计数 

 计算中的项的数目`multi_link_registry`对象。  
  
```
virtual size_t count();
```  
  
### <a name="return-value"></a>返回值  
 中的项的数目`multi_link_registry`对象。  
  
##  <a name="ctor"></a> multi_link_registry 

 构造 `multi_link_registry` 对象。  
  
```
multi_link_registry();
```  
  
##  <a name="dtor"></a> ~ multi_link_registry 

 销毁`multi_link_registry`对象。  
  
```
virtual ~multi_link_registry();
```  
  
### <a name="remarks"></a>备注  
 该方法将引发[invalid_operation](invalid-operation-class.md)异常之前将删除所有链接调用。  
  
##  <a name="remove"></a> 删除 

 删除从链接`multi_link_registry`对象。  
  
```
virtual bool remove(_EType _Link);
```  
  
### <a name="parameters"></a>参数  
 `_Link`  
 指向块被删除，如果找到。  
  
### <a name="return-value"></a>返回值  
 `true` 如果找到并移除了，链接`false`否则为。  
  
##  <a name="set_bound"></a> set_bound 

 上的链接数设置上限`multi_link_registry`对象可以保留。  
  
```
void set_bound(size_t _MaxLinks);
```  
  
### <a name="parameters"></a>参数  
 `_MaxLinks`  
 最大数链接`multi_link_registry`对象可以保留。  
  
### <a name="remarks"></a>备注  
 设置了界限后，取消某项的链接将导致 `multi_link_registry` 对象进入不可变状态，在该状态下进一步调用 `add` 将引发 `invalid_link_target` 异常。  
  
## <a name="see-also"></a>请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [single_link_registry 类](single-link-registry-class.md)

---
title: location 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- location
- CONCRT/concurrency::location
- CONCRT/concurrency::location::location
- CONCRT/concurrency::location::current
- CONCRT/concurrency::location::from_numa_node
dev_langs:
- C++
helpviewer_keywords:
- location class
ms.assetid: c3289f51-5bf1-4dff-a18d-d0dab8e5d9c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fdfb555375df4b9f791db25fa2dee47222f79063
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33688019"
---
# <a name="location-class"></a>location 类
硬件上物理位置的抽象。  
  
## <a name="syntax"></a>语法  
  
```
class location;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[location](#ctor)|已重载。 构造 `location` 对象。|  
|[~ location 析构函数](#dtor)|销毁 `location` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[current](#current)|返回表示调用线程执行的最具体位置的 `location` 对象。|  
|[from_numa_node](#from_numa_node)|返回表示给定的 NUMA 节点的 `location` 对象。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[operator!=](#operator_neq)|确定两个 `location` 对象是否表示不同的位置。|  
|[operator=](#operator_eq)|将另一 `location` 对象的内容分配给此对象。|  
|[operator==](#operator_eq_eq)|确定两个`location`对象表示相同的位置。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `location`  
  
## <a name="requirements"></a>要求  
 **标头：** concrt.h  
  
 **命名空间：** 并发  
  
##  <a name="dtor"></a> ~ 位置 

 销毁 `location` 对象。  
  
```
~location();
```  
  
##  <a name="current"></a> 当前 

 返回表示调用线程执行的最具体位置的 `location` 对象。  
  
```
static location __cdecl current();
```  
  
### <a name="return-value"></a>返回值  
 表示调用线程执行的最具体位置的位置。  
  
##  <a name="from_numa_node"></a> from_numa_node 

 返回表示给定的 NUMA 节点的 `location` 对象。  
  
```
static location __cdecl from_numa_node(unsigned short _NumaNodeNumber);
```  
  
### <a name="parameters"></a>参数  
 `_NumaNodeNumber`  
 要构造位置的 NUMA 节点号。  
  
### <a name="return-value"></a>返回值  
 表示 `_NumaNodeNumber` 参数指定的 NUMA 节点的位置。  
  
##  <a name="ctor"></a> 位置 

 构造 `location` 对象。  
  
```
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
 `_Src`  
 `_LocationType`  
 `_Id`  
 `_BindingId`  
 `_PBinding`  
  
### <a name="remarks"></a>备注  
 默认构造的位置表示整个系统。  
  
##  <a name="operator_neq"></a> 运算符 ！ = 

 确定两个 `location` 对象是否表示不同的位置。  
  
```
bool operator!= (const location& _Rhs) const;
```  
  
### <a name="parameters"></a>参数  
 `_Rhs`  
  
### <a name="return-value"></a>返回值  
 如果两个位置不同，则为 `true`；否则为 `false`。  
  
##  <a name="operator_eq"></a> 运算符 = 

 将另一 `location` 对象的内容分配给此对象。  
  
```
location& operator= (const location& _Rhs);
```  
  
### <a name="parameters"></a>参数  
 `_Rhs`  
 源 `location` 对象。  
  
### <a name="return-value"></a>返回值  
  
##  <a name="operator_eq_eq"></a> 运算符 = = 

 确定两个`location`对象表示相同的位置。  
  
```
bool operator== (const location& _Rhs) const;
```  
  
### <a name="parameters"></a>参数  
 `_Rhs`  
  
### <a name="return-value"></a>返回值  
 `true` 如果两个位置相同，和`false`否则为。  
  
## <a name="see-also"></a>请参阅  
 [并发命名空间](concurrency-namespace.md)

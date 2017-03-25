---
title: "network_link_registry 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- network_link_registry
- AGENTS/concurrency::network_link_registry
- AGENTS/concurrency::network_link_registry::add
- AGENTS/concurrency::network_link_registry::begin
- AGENTS/concurrency::network_link_registry::contains
- AGENTS/concurrency::network_link_registry::count
- AGENTS/concurrency::network_link_registry::remove
dev_langs:
- C++
helpviewer_keywords:
- network_link_registry class
ms.assetid: 3e7b4097-09f1-4252-964e-b15b8f7f7fc6
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: 28c13f1e2bf80624da3a7aba441944c051790d27
ms.lasthandoff: 03/17/2017

---
# <a name="networklinkregistry-class"></a>network_link_registry 类
`network_link_registry` 抽象基类管理源块和目标块之间的链接。  
  
## <a name="syntax"></a>语法  
  
```
template<class _Block>
class network_link_registry;
```  
  
#### <a name="parameters"></a>参数  
 `_Block`  
 块数据类型存储在`network_link_registry`。  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|描述|  
|----------|-----------------|  
|`const_pointer`|提供指向的指针的类型`const`中的元素`network_link_registry`对象。|  
|`const_reference`|提供对引用的类型`const`元素存储在`network_link_registry`用于读取和执行 const 操作的对象。|  
|`iterator`|提供的迭代器的类型可读取或修改中的任何元素`network_link_registry`对象。|  
|`type`|一种表示存储在的块类型`network_link_registry`对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[add](#add)|当在派生类中重写，将添加一个指向`network_link_registry`对象。|  
|[begin](#begin)|当在派生类中重写时返回的第一个元素的迭代器`network_link_registry`对象。|  
|[包含](#contains)|当在派生类中重写时搜索`network_link_registry`对象指定块。|  
|[count](#count)|当在派生类中重写返回中的项数`network_link_registry`对象。|  
|[remove](#remove)|如果在派生类中重写，将删除从指定的块`network_link_registry`对象。|  
  
## <a name="remarks"></a>备注  
 `network link registry`不是安全的并发访问。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `network_link_registry`  
  
## <a name="requirements"></a>要求  
 **标头：** agents.h  
  
 **命名空间：** 并发  
  
##  <a name="add"></a>添加 

 当在派生类中重写，将添加一个指向`network_link_registry`对象。  
  
```
virtual void add(_EType _Link) = 0;
```  
  
### <a name="parameters"></a>参数  
 `_Link`  
 指向要添加的块的指针。  
  
##  <a name="begin"></a>开始 

 当在派生类中重写时返回的第一个元素的迭代器`network_link_registry`对象。  
  
```
virtual iterator begin() = 0;
```  
  
### <a name="return-value"></a>返回值  
 发现的第一个元素的迭代器`network_link_registry`对象。  
  
### <a name="remarks"></a>备注  
 迭代器的最终状态由`NULL`链接。  
  
##  <a name="contains"></a>包含 

 当在派生类中重写时搜索`network_link_registry`对象指定块。  
  
```
virtual bool contains(_EType _Link) = 0;
```  
  
### <a name="parameters"></a>参数  
 `_Link`  
 在对进行搜索块的指针`network_link_registry`对象。  
  
### <a name="return-value"></a>返回值  
 `true`如果找到了指定块，`false`否则为。  
  
##  <a name="count"></a>计数 

 当在派生类中重写返回中的项数`network_link_registry`对象。  
  
```
virtual size_t count() = 0;
```  
  
### <a name="return-value"></a>返回值  
 中的项数`network_link_registry`对象。  
  
##  <a name="remove"></a>删除 

 如果在派生类中重写，将删除从指定的块`network_link_registry`对象。  
  
```
virtual bool remove(_EType _Link) = 0;
```  
  
### <a name="parameters"></a>参数  
 `_Link`  
 指向块被删除，如果找到。  
  
### <a name="return-value"></a>返回值  
 `true`如果找到该链接并将其删除，`false`否则为。  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [single_link_registry 类](single-link-registry-class.md)   
 [multi_link_registry 类](multi-link-registry-class.md)


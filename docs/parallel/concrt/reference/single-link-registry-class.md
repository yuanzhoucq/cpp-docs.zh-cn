---
title: "single_link_registry 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- agents/concurrency::single_link_registry
dev_langs:
- C++
helpviewer_keywords:
- single_link_registry class
ms.assetid: 09540a4e-c34e-4ff9-af49-21b8612b6ab3
caps.latest.revision: 19
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
ms.sourcegitcommit: fc190feb08d9b221cd1cc21a9c91ad567c86c848
ms.openlocfilehash: 3f4719881fac882611f68b36d410c0611f99ba01
ms.lasthandoff: 02/24/2017

---
# <a name="singlelinkregistry-class"></a>single_link_registry 类
`single_link_registry` 对象是仅管理单个源块或目标块的 `network_link_registry`。  
  
## <a name="syntax"></a>语法  
  
```
template<class _Block>
class single_link_registry : public network_link_registry<_Block>;
```  
  
#### <a name="parameters"></a>参数  
 `_Block`  
 块数据类型存储在`single_link_registry`对象。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[single_link_registry 构造函数](#ctor)|构造 `single_link_registry` 对象。|  
|[~ single_link_registry 析构函数](#dtor)|销毁`single_link_registry`对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[添加方法](#add)|将链接到添加`single_link_registry`对象。 (重写[network_link_registry:: add](network-link-registry-class.md#add)。)|  
|[begin 方法](#begin)|返回一个迭代中的第一个元素指向`single_link_registry`对象。 (重写[network_link_registry:: begin](network-link-registry-class.md#begin)。)|  
|[包含方法](#contains)|搜索`single_link_registry`对象指定块。 (重写[network_link_registry:: contains](network-link-registry-class.md#contains)。)|  
|[count 方法](#count)|中的项的计数`single_link_registry`对象。 (重写[network_link_registry:: count](network-link-registry-class.md#count)。)|  
|[remove 方法](#remove)|移除从链接`single_link_registry`对象。 (重写[network_link_registry:: remove](network-link-registry-class.md#remove)。)|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [network_link_registry](network-link-registry-class.md)  
  
 `single_link_registry`  
  
## <a name="requirements"></a>要求  
 **标头：** agents.h  
  
 **命名空间：** 并发  
  
##  <a name="a-nameadda-add"></a><a name="add"></a>添加 

 将链接到添加`single_link_registry`对象。  
  
```
virtual void add(_EType _Link);
```  
  
### <a name="parameters"></a>参数  
 `_Link`  
 指向要添加的块的指针。  
  
### <a name="remarks"></a>备注  
 该方法将引发[invalid_link_target](invalid-link-target-class.md)异常是否已存在一个链接到此注册表中。  
  
##  <a name="a-namebegina-begin"></a><a name="begin"></a>开始 

 返回一个迭代中的第一个元素指向`single_link_registry`对象。  
  
```
virtual iterator begin();
```  
  
### <a name="return-value"></a>返回值  
 发现的第一个元素的迭代器`single_link_registry`对象。  
  
### <a name="remarks"></a>备注  
 最终状态由`NULL`链接。  
  
##  <a name="a-namecontainsa-contains"></a><a name="contains"></a>包含 

 搜索`single_link_registry`对象指定块。  
  
```
virtual bool contains(_EType _Link);
```  
  
### <a name="parameters"></a>参数  
 `_Link`  
 指向要在其中搜索中的块的指针`single_link_registry`对象。  
  
### <a name="return-value"></a>返回值  
 `true`如果找到了指定链接，`false`否则为。  
  
##  <a name="a-namecounta-count"></a><a name="count"></a>计数 

 中的项的计数`single_link_registry`对象。  
  
```
virtual size_t count();
```  
  
### <a name="return-value"></a>返回值  
 中的项数`single_link_registry`对象。  
  
##  <a name="a-nameremovea-remove"></a><a name="remove"></a>删除 

 移除从链接`single_link_registry`对象。  
  
```
virtual bool remove(_EType _Link);
```  
  
### <a name="parameters"></a>参数  
 `_Link`  
 指向块被删除，如果找到。  
  
### <a name="return-value"></a>返回值  
 `true`如果找到该链接并将其删除，`false`否则为。  
  
##  <a name="a-namectora-singlelinkregistry"></a><a name="ctor"></a>single_link_registry 

 构造 `single_link_registry` 对象。  
  
```
single_link_registry();
```  
  
##  <a name="a-namedtora-singlelinkregistry"></a><a name="dtor"></a>~ single_link_registry 

 销毁`single_link_registry`对象。  
  
```
virtual ~single_link_registry();
```  
  
### <a name="remarks"></a>备注  
 该方法将引发[invalid_operation](invalid-operation-class.md)异常如果称为之前删除的链接。  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [multi_link_registry 类](multi-link-registry-class.md)


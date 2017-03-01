---
title: "affinity_partitioner 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ppl/concurrency::affinity_partitioner
dev_langs:
- C++
helpviewer_keywords:
- affinity_partitioner class
ms.assetid: 31bf7bb1-bd01-491c-9760-d9d60edfccad
caps.latest.revision: 9
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
ms.openlocfilehash: 92da56fd5b84537c2fa01a252dfee202c729cc96
ms.lasthandoff: 02/24/2017

---
# <a name="affinitypartitioner-class"></a>affinity_partitioner 类
`affinity_partitioner` 类与 `static_partitioner` 类相似，但它选择将子范围映射到工作线程，从而改善缓存关联。 在同一数据集中重新执行循环且数据适应缓存时，它可以显著提高性能。 请注意，必须与在特定数据集中执行的并行循环的后续迭代一起使用同一 `affinity_partitioner` 对象，才能受益于数据位置。  
  
## <a name="syntax"></a>语法  
  
```
class affinity_partitioner;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[affinity_partitioner 构造函数](#ctor)|构造 `affinity_partitioner` 对象。|  
|[~ affinity_partitioner 析构函数](#dtor)|销毁`affinity_partitioner`对象。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `affinity_partitioner`  
  
## <a name="requirements"></a>要求  
 **标头︰** ppl.h  
  
 **命名空间：** 并发  
  
##  <a name="a-namedtora-affinitypartitioner"></a><a name="dtor"></a>~ affinity_partitioner 

 销毁`affinity_partitioner`对象。  
  
```
~affinity_partitioner();
```  
  
##  <a name="a-namectora-affinitypartitioner"></a><a name="ctor"></a>affinity_partitioner 

 构造 `affinity_partitioner` 对象。  
  
```
affinity_partitioner();
```  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace](concurrency-namespace.md)


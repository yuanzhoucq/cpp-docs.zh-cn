---
title: "static_partitioner 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ppl/concurrency::static_partitioner
dev_langs:
- C++
helpviewer_keywords:
- static_partitioner class
ms.assetid: 2b3dbdf0-6eb9-49f6-8639-03df1d974143
caps.latest.revision: 8
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
ms.openlocfilehash: f36b1e1dcc68d94bdebd8b7b10f4fec735ce9fb5
ms.lasthandoff: 02/24/2017

---
# <a name="staticpartitioner-class"></a>static_partitioner 类
`static_partitioner` 类表示由 `parallel_for` 循环访问的范围的静态分区。 只要基础计划程序有工作线程可用，分区程序就会将范围分成尽可能多的区块。  
  
## <a name="syntax"></a>语法  
  
```
class static_partitioner;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[static_partitioner 构造函数](#ctor)|构造 `static_partitioner` 对象。|  
|[~ static_partitioner 析构函数](#dtor)|销毁 `static_partitioner` 对象。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `static_partitioner`  
  
## <a name="requirements"></a>要求  
 **标头︰** ppl.h  
  
 **命名空间：** 并发  
  
##  <a name="a-namedtora-staticpartitioner"></a><a name="dtor"></a>~ static_partitioner 

 销毁 `static_partitioner` 对象。  
  
```
~static_partitioner();
```  
  
##  <a name="a-namectora-staticpartitioner"></a><a name="ctor"></a>static_partitioner 

 构造 `static_partitioner` 对象。  
  
```
static_partitioner();
```  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace](concurrency-namespace.md)


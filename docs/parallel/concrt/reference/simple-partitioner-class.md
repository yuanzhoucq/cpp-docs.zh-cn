---
title: "simple_partitioner 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ppl/concurrency::simple_partitioner
dev_langs:
- C++
helpviewer_keywords:
- simple_partitioner class
ms.assetid: d7e997af-54d1-43f5-abe0-def72df6edb3
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
ms.openlocfilehash: dc90df5ba9fbbf5566a26a014a6a2db2ae4a0459
ms.lasthandoff: 02/24/2017

---
# <a name="simplepartitioner-class"></a>simple_partitioner 类
`simple_partitioner` 类表示由 `parallel_for` 循环访问的范围的静态分区。 分区程序将该范围分成区块，以便每个区块都至少具有区块大小指定的迭代数量。  
  
## <a name="syntax"></a>语法  
  
```
class simple_partitioner;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[simple_partitioner 构造函数](#ctor)|构造 `simple_partitioner` 对象。|  
|[~ simple_partitioner 析构函数](#dtor)|销毁 `simple_partitioner` 对象。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `simple_partitioner`  
  
## <a name="requirements"></a>要求  
 **标头︰** ppl.h  
  
 **命名空间：** 并发  
  
##  <a name="a-namedtora-simplepartitioner"></a><a name="dtor"></a>~ simple_partitioner 

 销毁 `simple_partitioner` 对象。  
  
```
~simple_partitioner();
```  
  
##  <a name="a-namectora-simplepartitioner"></a><a name="ctor"></a>simple_partitioner 

 构造 `simple_partitioner` 对象。  
  
```
explicit simple_partitioner(_Size_type _Chunk_size);
```  
  
### <a name="parameters"></a>参数  
 `_Chunk_size`  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace](concurrency-namespace.md)


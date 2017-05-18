---
title: "static_partitioner 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- static_partitioner
- PPL/concurrency::static_partitioner
- PPL/concurrency::static_partitioner::static_partitioner
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: 84cdbb30068f8dd9d2a1130e53d06d9b718b0c02
ms.contentlocale: zh-cn
ms.lasthandoff: 03/17/2017

---
# <a name="staticpartitioner-class"></a>static_partitioner 类
`static_partitioner` 类表示由 `parallel_for` 循环访问的范围的静态分区。 只要基础计划程序有工作线程可用，分区程序就会将范围分成尽可能多的区块。  
  
## <a name="syntax"></a>语法  
  
```
class static_partitioner;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[static_partitioner](#ctor)|构造 `static_partitioner` 对象。|  
|[~ static_partitioner 析构函数](#dtor)|销毁 `static_partitioner` 对象。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `static_partitioner`  
  
## <a name="requirements"></a>要求  
 **标头︰** ppl.h  
  
 **命名空间：** 并发  
  
##  <a name="dtor"></a>~ static_partitioner 

 销毁 `static_partitioner` 对象。  
  
```
~static_partitioner();
```  
  
##  <a name="ctor"></a>static_partitioner 

 构造 `static_partitioner` 对象。  
  
```
static_partitioner();
```  
  
## <a name="see-also"></a>另请参阅  
 [并发命名空间](concurrency-namespace.md)


---
title: "tile_barrier 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- amp/Concurrency::tile_barrier
dev_langs:
- C++
helpviewer_keywords:
- tile_barrier class
ms.assetid: b4ccdccb-0032-4e11-b7bd-dc9d43445dee
caps.latest.revision: 17
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
ms.openlocfilehash: 7ace6bb366881f9e5a9678b3a005f3079542c9cd
ms.lasthandoff: 02/24/2017

---
# <a name="tilebarrier-class"></a>tile_barrier 类
同步使用正在运行的线程组 (tile) 中的线程的执行`wait`方法。 只有运行时可以实例化此类。  
  
### <a name="syntax"></a>语法 
  
```  
class tile_barrier;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[tile_barrier 构造函数](#ctor)|初始化 `tile_barrier` 类的新实例。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[wait 方法](#wait)|指示要停止执行，直至磁贴中的所有线程都完成等待的线程组 (tile) 中的所有线程。|  
|[wait_with_all_memory_fence 方法](#wait_with_all_memory_fence)|直到已完成的所有内存访问平铺中的所有线程和磁贴中的所有线程的阻止执行已达到此调用。|  
|[wait_with_global_memory_fence 方法](#wait_with_global_memory_fence)|块中的图块，直到已完成的所有全局内存访问以及磁贴中的所有线程均已都到达此调用的所有线程执行。|  
|[wait_with_tile_static_memory_fence 方法](#wait_with_tile_static_memory_fence)|将阻止执行平铺中的所有线程，直到所有`tile_static`已完成的内存访问以及磁贴中的所有线程均已都到达此调用。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `tile_barrier`  
  
## <a name="requirements"></a>要求  
 **标头：** amp.h  
  
 **命名空间：** 并发  

## <a name="a-nametilebarrierctora--tilebarrier-constructor"></a><a name="tile_barrier__ctor"></a>tile_barrier 构造函数  
 通过将一个现有的复制初始化类的新实例。  
  
### <a name="syntax"></a>语法 
  
```  
tile_barrier(  
    const tile_barrier& _Other ) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>参数  
 `_Other`  
 `tile_barrier`要从中复制对象。  

## <a name="a-namewaita--wait"></a><a name="wait"></a>等待 
指示线程组 (Tile) 中的所有线程停止执行，直到 Tile 中的所有线程完成等待。  
  
### <a name="syntax"></a>语法 
  
```  
void wait() const restrict(amp);  
```    

## <a name="a-namewaitwithallmemoryfencea--waitwithallmemoryfence"></a><a name="wait_with_all_memory_fence"></a>wait_with_all_memory_fence   
平铺直至平铺中的所有线程都已都达到此调用中的所有线程的阻止执行。 这可确保所有的内存访问中的线程磁贴，其他线程可见，并且已按程序顺序执行。  
  
### <a name="syntax"></a>语法 
  
```  
void wait_with_all_memory_fence() const restrict(amp);  
```  
  

## <a name="a-namewaitwithglobalmemoryfencea--waitwithglobalmemoryfence"></a><a name="wait_with_global_memory_fence"></a>wait_with_global_memory_fence   
平铺直至平铺中的所有线程都已都达到此调用中的所有线程的阻止执行。 这可确保所有全局内存访问中的线程磁贴，其他线程可见，并且已按程序顺序执行。  
  
### <a name="syntax"></a>语法 
  
```  
void wait_with_global_memory_fence() const  restrict(amp);  
```

## <a name="a-namewaitwithtilestaticmemoryfencea--waitwithtilestaticmemoryfence"></a><a name="wait_with_tile_static_memory_fence"></a>wait_with_tile_static_memory_fence   
平铺直至平铺中的所有线程都已都达到此调用中的所有线程的阻止执行。 这样可以确保`tile_static`内存的访问会向其他线程在线程图块，以及已按程序顺序执行。  
  
### <a name="syntax"></a>语法 
  
```  
void wait_with_tile_static_memory_fence() const restrict(amp);  
```  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace (c + + AMP)](concurrency-namespace-cpp-amp.md)


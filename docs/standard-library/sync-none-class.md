---
title: "sync_none 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- allocators/stdext::sync_none
- allocators/stdext::sync_none::allocate
- allocators/stdext::sync_none::deallocate
- allocators/stdext::sync_none::equals
dev_langs:
- C++
helpviewer_keywords:
- stdext::sync_none
- stdext::sync_none [C++], allocate
- stdext::sync_none [C++], deallocate
- stdext::sync_none [C++], equals
ms.assetid: f7473cee-14f3-4fe1-88bc-68cd085e59e1
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: 6cd96ec71098bed30fdbbb0fa84cfd7e61e33a7b
ms.contentlocale: zh-cn
ms.lasthandoff: 10/03/2017

---
# <a name="syncnone-class"></a>sync_none 类
描述不提供同步的[同步筛选器](../standard-library/allocators-header.md)。  
  
## <a name="syntax"></a>语法  
  
```
template <class Cache>  
class sync_none
```  
  
#### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|`Cache`|与同步筛选器相关联的缓存类型。 它可以是 [cache_chunklist](../standard-library/cache-chunklist-class.md)、[cache_freelist](../standard-library/cache-freelist-class.md) 或 [cache_suballoc](../standard-library/cache-suballoc-class.md)。|  
  
### <a name="member-functions"></a>成员函数  
  
|||  
|-|-|  
|[allocate](#allocate)|分配内存块。|  
|[deallocate](#deallocate)|从指定位置开始从存储中释放指定数量的的对象。|  
|[equals](#equals)|比较两个缓存是否相等。|  
  
## <a name="requirements"></a>要求  
 **标头：**\<allocators>  
  
 **命名空间：** stdext  
  
##  <a name="allocate"></a>  sync_none::allocate  
 分配内存块。  
  
```
void *allocate(std::size_t count);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|`count`|数组中要分配的元素数目。|  
  
### <a name="remarks"></a>备注  
 此成员函数返回 `cache.allocate(count)`，其中 `cache` 是缓存对象。  
  
##  <a name="deallocate"></a>  sync_none::deallocate  
 从指定位置开始从存储中释放指定数量的的对象。  
  
```
void deallocate(void* ptr, std::size_t count);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|`ptr`|指向要从存储中释放的第一个对象的指针。|  
|`count`|要从存储中释放的对象数量。|  
  
### <a name="remarks"></a>备注  
 此成员函数调用 `cache.deallocate(ptr, count)`，其中 `cache` 表示缓存对象。  
  
##  <a name="equals"></a>  sync_none::equals  
 比较两个缓存是否相等。  
  
```
bool equals(const sync<Cache>& Other) const;
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|`Cache`|同步筛选器的缓存对象。|  
|`Other`|要用于比较是否相等的缓存对象。|  
  
### <a name="return-value"></a>返回值  
 此成员函数总是返回 `true`。  
  
### <a name="remarks"></a>备注  
  
## <a name="see-also"></a>另请参阅  
 [\<allocators>](../standard-library/allocators-header.md)





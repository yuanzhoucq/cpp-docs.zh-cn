---
title: "sync_shared 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- allocators/stdext::sync_shared
- allocators/stdext::sync_shared::allocate
- allocators/stdext::sync_shared::deallocate
- allocators/stdext::sync_shared::equals
dev_langs: C++
helpviewer_keywords:
- stdext::sync_shared
- stdext::sync_shared [C++], allocate
- stdext::sync_shared [C++], deallocate
- stdext::sync_shared [C++], equals
ms.assetid: cab3af9e-3d1a-4f2c-8580-0f89e5687d8e
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ff7c75428fbe63a2ec9183c3d909d22e9f38703e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="syncshared-class"></a>sync_shared 类
介绍[同步筛选器](../standard-library/allocators-header.md)，它使用互斥体来控制对所有分配器共享的缓存对象的访问。  
  
## <a name="syntax"></a>语法  
  
```
template <class Cache>  
class sync_shared
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
  
## <a name="requirements"></a>惠?  
 **标头：**\<allocators>  
  
 **命名空间：** stdext  
  
##  <a name="allocate"></a>  sync_shared::allocate  
 分配内存块。  
  
```
void *allocate(std::size_t count);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|`count`|数组中要分配的元素数目。|  
  
### <a name="return-value"></a>返回值  
 指向已分配对象的指针。  
  
### <a name="remarks"></a>备注  
 成员函数会锁定互斥体，调用 `cache.allocate(count)`、解除对互斥体的锁定并返回之前调用 `cache.allocate(count)` 的结果。 `cache` 表示当前缓存对象。  
  
##  <a name="deallocate"></a>  sync_shared::deallocate  
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
 此成员函数会锁定互斥体，调用 `cache.deallocate(ptr, count)`其中 `cache` 表示缓存对象），然后取消对该互斥体的锁定。  
  
##  <a name="equals"></a>  sync_shared::equals  
 比较两个缓存是否相等。  
  
```
bool equals(const sync_shared<Cache>& Other) const;
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|`Cache`|与同步筛选器相关联的缓存类型。|  
|`Other`|要比较是否相等的缓存。|  
  
### <a name="return-value"></a>返回值  
 如果 `cache.equals(Other.cache)` 的结果为 `true`（其中 `cache` 表示缓存对象），则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
  
## <a name="see-also"></a>请参阅  
 [\<allocators>](../standard-library/allocators-header.md)




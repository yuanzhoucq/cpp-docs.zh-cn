---
title: "rts_alloc 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- stdext::rts_alloc
- allocators/stdext::rts_alloc
- rts_alloc
- allocators/stdext::rts_alloc::allocate
- allocators/stdext::rts_alloc::deallocate
- allocators/stdext::rts_alloc::equals
dev_langs:
- C++
helpviewer_keywords:
- rts_alloc class
ms.assetid: ab41bffa-83d1-4a1c-87b9-5707d516931f
caps.latest.revision: 19
author: corob-msft
ms.author: corob
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
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: fe127f896fa902f4a8cdb44454cf6e4c5f449e79
ms.contentlocale: zh-cn
ms.lasthandoff: 04/29/2017

---
# <a name="rtsalloc-class"></a>rts_alloc 类
rts_alloc 模板类描述一种[筛选器](../standard-library/allocators-header.md)，它具有缓存实例数组，并确定运行时（而非编译时）用于分配和解除分配的实例。  
  
## <a name="syntax"></a>语法  
  
```
template <class Cache>  
class rts_alloc
```  
  
#### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|`Cache`|数组中包含的缓存实例的类型。 这可能是 [cache_chunklist 类](../standard-library/cache-chunklist-class.md)、 [cache_freelist](../standard-library/cache-freelist-class.md) 或 [cache_suballoc](../standard-library/cache-suballoc-class.md)。|  
  
## <a name="remarks"></a>备注  
 此模板类持有多个块分配器实例，并确定运行时（而非编译时）用于分配或解除分配的实例。 它与不能编译重新绑定的编译器一起使用。  
  
### <a name="member-functions"></a>成员函数  
  
|||  
|-|-|  
|[allocate](#allocate)|分配内存块。|  
|[deallocate](#deallocate)|从指定位置开始从存储中释放指定数量的的对象。|  
|[equals](#equals)|比较两个缓存是否相等。|  
  
## <a name="requirements"></a>要求  
 **标头：**\<allocators>  
  
 **命名空间：** stdext  
  
##  <a name="allocate"></a>rts_alloc::allocate  
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
 成员函数返回 `caches[_IDX].allocate(count)`，其中索引 `_IDX` 由所请求的块大小 `count` 决定，但如果 `count` 太大，将返回 `operator new(count)`。 用于表示缓存对象的 `cache`。  
  
##  <a name="deallocate"></a>  rts_alloc::deallocate  
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
 成员函数将调用 `caches[_IDX].deallocate(ptr, count)`，其中索引 `_IDX` 由所请求的块大小 `count` 决定，但如果 `count` 太大，它将返回 `operator delete(ptr)`。  
  
##  <a name="equals"></a>  rts_alloc::equals  
 比较两个缓存是否相等。  
  
```
bool equals(const sync<_Cache>& _Other) const;
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|`_Cache`|与筛选器关联的缓存对象。|  
|`_Other`|要用于比较是否相等的缓存对象。|  
  
### <a name="remarks"></a>备注  
 如果结果为 `caches[0].equals(other.caches[0])`，则为 `true`；否则为 `false`。 `caches` 表示缓存对象的数组。  
  
## <a name="see-also"></a>另请参阅  
 [ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl)   
 [\<allocators>](../standard-library/allocators-header.md)





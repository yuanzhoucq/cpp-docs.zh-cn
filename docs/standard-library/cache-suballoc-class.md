---
title: "cache_suballoc 类 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- allocators/stdext::cache_suballoc
- stdext::cache_suballoc
- cache_suballoc
- allocators/stdext::cache_suballoc::allocate
- allocators/stdext::cache_suballoc::deallocate
dev_langs:
- C++
helpviewer_keywords:
- cache_suballoc class
ms.assetid: 9ea9c5e9-1dcc-45d0-b3a7-a56a93d88898
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
ms.openlocfilehash: fa98856bc7e55ca78effb64c806a95cab60a68a5
ms.contentlocale: zh-cn
ms.lasthandoff: 04/29/2017

---
# <a name="cachesuballoc-class"></a>cache_suballoc 类
定义分配和释放单个大小内存块的[块分配器](../standard-library/allocators-header.md)。  
  
## <a name="syntax"></a>语法  
  
```
template <std::size_t Sz, size_t Nelts = 20>  
class cache_suballoc
```  
  
#### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|`Sz`|数组中要分配的元素数目。|  
  
## <a name="remarks"></a>备注  
 cache_suballoc 模板类使用 `freelist<sizeof(Type), max_unbounded>` 将释放的内存块存储在长度不受限制的可用列表中，并在可用列表为空时在 `operator new` 分配的较大区块中细分内存块。  
  
 每个区块保留 `Sz * Nelts` 个字节的可用内存以及 `operator new` 和 `operator delete` 所需的数据。 不会释放已分配的区块。  
  
### <a name="constructors"></a>构造函数  
  
|||  
|-|-|  
|[cache_suballoc](#cache_suballoc)|构造 `cache_suballoc` 类型的对象。|  
  
### <a name="member-functions"></a>成员函数  
  
|||  
|-|-|  
|[allocate](#allocate)|分配内存块。|  
|[deallocate](#deallocate)|从指定位置开始从存储中释放指定数量的的对象。|  
  
## <a name="requirements"></a>要求  
 **标头：**\<allocators>  
  
 **命名空间：** stdext  
  
##  <a name="allocate"></a>  cache_suballoc::allocate  
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
  
##  <a name="cache_suballoc"></a>  cache_suballoc::cache_suballoc  
 构造 `cache_suballoc` 类型的对象。  
  
```
cache_suballoc();
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="deallocate"></a>  cache_suballoc::deallocate  
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
  
## <a name="see-also"></a>另请参阅  
 [\<allocators>](../standard-library/allocators-header.md)





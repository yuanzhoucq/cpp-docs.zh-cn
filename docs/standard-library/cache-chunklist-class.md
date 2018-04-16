---
title: "cache_chunklist 类 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- allocators/stdext::cache_chunklist
- allocators/stdext::cache_chunklist::allocate
- allocators/stdext::cache_chunklist::deallocate
dev_langs:
- C++
helpviewer_keywords:
- stdext::cache_chunklist
- stdext::cache_chunklist [C++], allocate
- stdext::cache_chunklist [C++], deallocate
ms.assetid: af19eccc-4ae7-4a34-bbb2-81e397424cb9
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: acab7f835ac6bcbad61b4f9fe7157cbda953b2f9
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="cachechunklist-class"></a>cache_chunklist 类
定义分配和释放单个大小内存块的[块分配器](../standard-library/allocators-header.md)。  
  
## <a name="syntax"></a>语法  
  
```
template <std::size_t Sz, std::size_t Nelts = 20>  
class cache_chunklist
```  
  
#### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|`Sz`|数组中要分配的元素数目。|  
  
## <a name="remarks"></a>备注  
 此模板类使用 `operator new` 分配原始内存的区块，并对块进行细分以在必要时为内存块分配存储空间；其将释放的内存块存储在每个区块的独立释放列表中，并在未使用区块的任何内存块时使用 `operator delete` 释放区块。  
  
 每个内存块保留 `Sz` 个字节的可用内存和指向其所属于的区块的指针。 每个区块保留 `Nelts` 内存块、三个指针、一个 int 以及 `operator new` 和 `operator delete` 所需的数据。  
  
### <a name="constructors"></a>构造函数  
  
|||  
|-|-|  
|[cache_chunklist](#cache_chunklist)|构造 `cache_chunklist` 类型的对象。|  
  
### <a name="member-functions"></a>成员函数  
  
|||  
|-|-|  
|[allocate](#allocate)|分配内存块。|  
|[deallocate](#deallocate)|从指定位置开始从存储中释放指定数量的的对象。|  
  
## <a name="requirements"></a>惠?  
 **标头：**\<allocators>  
  
 **命名空间：** stdext  
  
##  <a name="allocate"></a>  cache_chunklist::allocate  
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
  
##  <a name="cache_chunklist"></a>  cache_chunklist::cache_chunklist  
 构造 `cache_chunklist` 类型的对象。  
  
```
cache_chunklist();
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="deallocate"></a>  cache_chunklist::deallocate  
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
  
## <a name="see-also"></a>请参阅  
 [\<allocators>](../standard-library/allocators-header.md)




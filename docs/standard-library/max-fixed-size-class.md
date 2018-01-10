---
title: "max_fixed_size 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- allocators/stdext::max_fixed_size
- allocators/stdext::max_fixed_size::allocated
- allocators/stdext::max_fixed_size::deallocated
- allocators/stdext::max_fixed_size::full
- allocators/stdext::max_fixed_size::released
- allocators/stdext::max_fixed_size::saved
dev_langs: C++
helpviewer_keywords:
- stdext::max_fixed_size
- stdext::max_fixed_size [C++], allocated
- stdext::max_fixed_size [C++], deallocated
- stdext::max_fixed_size [C++], full
- stdext::max_fixed_size [C++], released
- stdext::max_fixed_size [C++], saved
ms.assetid: 8c8f4588-37e9-4579-8168-ba3553800914
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a853e417ad79ed27f7579ce50186974abfe21c3e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="maxfixedsize-class"></a>max_fixed_size 类
描述 [max 类](../standard-library/allocators-header.md) 对象，该对象将 [freelist](../standard-library/freelist-class.md) 对象的最大长度限制为固定的最大长度。  
  
## <a name="syntax"></a>语法  
  
```
template <std::size_t Max>  
class max_fixed_size
```  
  
#### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|`Max`|max 类，用于决定要存储于 `freelist` 中的最大元素数目。|  
  
### <a name="constructors"></a>构造函数  
  
|||  
|-|-|  
|[max_fixed_size](#max_fixed_size)|构造 `max_fixed_size` 类型的对象。|  
  
### <a name="member-functions"></a>成员函数  
  
|||  
|-|-|  
|[allocated](#allocated)|逐量增加已分配的内存块的计数。|  
|[deallocated](#deallocated)|逐量减小已分配的内存块的计数。|  
|[full](#full)|返回一个值，该值指定是否应将更多的内存块添加到空闲列表。|  
|[released](#released)|逐量减小空闲列表上内存块的计数。|  
|[saved](#saved)|逐量增加空闲列表上内存块的计数。|  
  
## <a name="requirements"></a>惠?  
 **标头：**\<allocators>  
  
 **命名空间：** stdext  
  
##  <a name="allocated"></a>max_fixed_size::allocated  
 逐量增加已分配的内存块的计数。  
  
```
void allocated(std::size_t _Nx = 1);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|`_Nx`|增量值。|  
  
### <a name="remarks"></a>备注  
 此成员函数不执行任何操作。 每次调用成功后，`cache_freelist::allocate` 会将此成员函数调用到运算符 `new`。 自变量 `_Nx` 是运算符 `new` 分配的区块中的内存块数。  
  
##  <a name="deallocated"></a>max_fixed_size::deallocated  
 逐量减小已分配的内存块的计数。  
  
```
void deallocated(std::size_t _Nx = 1);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|`_Nx`|增量值。|  
  
### <a name="remarks"></a>备注  
 此成员函数不执行任何操作。 每次调用后，`cache_freelist::deallocate` 会将此成员函数调用到运算符 `delete`。 自变量 `_Nx` 是运算符 `delete` 取消分配的区块中的内存块数。  
  
##  <a name="full"></a>max_fixed_size::full  
 返回一个值，该值指定是否应将更多的内存块添加到空闲列表。  
  
```
bool full();
```  
  
### <a name="return-value"></a>返回值  
 如果是 `Max <= _Nblocks`，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 此成员函数由 `cache_freelist::deallocate` 调用。 如果调用返回 `true`，则 `deallocate` 会将内存块放入空闲列表；如果它返回 false，则 `deallocate` 将调用运算符 `delete` 以取消分配块。  
  
##  <a name="max_fixed_size"></a>max_fixed_size::max_fixed_size  
 构造 `max_fixed_size` 类型的对象。  
  
```
max_fixed_size();
```  
  
### <a name="remarks"></a>备注  
 该构造函数将存储的值 `_Nblocks` 初始化为零。  
  
##  <a name="released"></a>max_fixed_size::released  
 逐量减小空闲列表上内存块的计数。  
  
```
void released();
```  
  
### <a name="remarks"></a>备注  
 逐量减小存储值 `_Nblocks`。 每当当前 [max 类](../standard-library/allocators-header.md)的 `released` 成员函数从空闲列表中删除内存块时，`cache_freelist::allocate` 将对其进行调用。  
  
##  <a name="saved"></a>max_fixed_size::saved  
 逐量增加空闲列表上内存块的计数。  
  
```
void saved();
```  
  
### <a name="remarks"></a>备注  
 此成员函数逐量增加存储值 `_Nblocks`。 每当此成员函数向空闲列表放入内存块时，`cache_freelist::deallocate` 将对其进行调用。  
  
## <a name="see-also"></a>请参阅  
 [\<allocators>](../standard-library/allocators-header.md)




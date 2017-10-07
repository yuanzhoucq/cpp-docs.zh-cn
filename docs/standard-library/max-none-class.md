---
title: "max_none 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- allocators/stdext::max_none
- allocators/stdext::max_none::allocated
- allocators/stdext::max_none::deallocated
- allocators/stdext::max_none::full
- allocators/stdext::max_none::released
- allocators/stdext::max_none::saved
dev_langs:
- C++
helpviewer_keywords:
- stdext::max_none
- stdext::max_none [C++], allocated
- stdext::max_none [C++], deallocated
- stdext::max_none [C++], full
- stdext::max_none [C++], released
- stdext::max_none [C++], saved
ms.assetid: 12ab5376-412e-479c-86dc-2c3d6a3559b6
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: ffa6da15f19d3215080d7a1e5355134409765da5
ms.contentlocale: zh-cn
ms.lasthandoff: 10/03/2017

---
# <a name="maxnone-class"></a>max_none 类
描述 [max 类](../standard-library/allocators-header.md) 对象，该对象将 [freelist](../standard-library/freelist-class.md) 对象的最大长度限制为零。  
  
## <a name="syntax"></a>语法  
  
```
template <std::size_t Max>  
class max_none
```  
  
#### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|`Max`|max 类，用于决定要存储于 `freelist` 中的最大元素数目。|  
  
### <a name="member-functions"></a>成员函数  
  
|||  
|-|-|  
|[allocated](#allocated)|逐量增加已分配的内存块的计数。|  
|[deallocated](#deallocated)|逐量减小已分配的内存块的计数。|  
|[full](#full)|返回一个值，该值指定是否应将更多的内存块添加到空闲列表。|  
|[released](#released)|逐量减小空闲列表上内存块的计数。|  
|[saved](#saved)|逐量增加空闲列表上内存块的计数。|  
  
## <a name="requirements"></a>要求  
 **标头：**\<allocators>  
  
 **命名空间：** stdext  
  
##  <a name="allocated"></a>max_none::allocated  
 逐量增加已分配的内存块的计数。  
  
```
void allocated(std::size_t _Nx = 1);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|`_Nx`|增量值。|  
  
### <a name="remarks"></a>备注  
 此成员函数不执行任何操作。 每次调用成功后，`cache_freelist::allocate` 会将此成员函数调用到运算符 `new`。 自变量 `_Nx` 是运算符 `new` 分配的区块中的内存块数。  
  
##  <a name="deallocated"></a>max_none::deallocated  
 逐量减小已分配的内存块的计数。  
  
```
void deallocated(std::size_t _Nx = 1);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|`_Nx`|增量值。|  
  
### <a name="remarks"></a>备注  
 此成员函数不执行任何操作。 每次调用后，`cache_freelist::deallocate` 会将此成员函数调用到运算符 `delete`。 自变量 `_Nx` 是运算符 `delete` 取消分配的区块中的内存块数。  
  
##  <a name="full"></a>max_none::full  
 返回一个值，该值指定是否应将更多的内存块添加到空闲列表。  
  
```
bool full();
```  
  
### <a name="return-value"></a>返回值  
 此成员函数总是返回 `true`。  
  
### <a name="remarks"></a>备注  
 此成员函数由 `cache_freelist::deallocate` 调用。 如果调用返回 `true`，则 `deallocate` 会将内存块放入空闲列表；如果它返回 false，则 `deallocate` 将调用运算符 `delete` 以取消分配块。  
  
##  <a name="released"></a>max_none::released  
 逐量减小空闲列表上内存块的计数。  
  
```
void released();
```  
  
### <a name="remarks"></a>备注  
 此成员函数不执行任何操作。 每当当前 max 类的 `released` 成员函数从空闲列表中删除内存块时，`cache_freelist::allocate` 将对其进行调用。  
  
##  <a name="saved"></a>max_none::saved  
 逐量增加空闲列表上内存块的计数。  
  
```
void saved();
```  
  
### <a name="remarks"></a>备注  
 此成员函数不执行任何操作。 每当此成员函数向空闲列表放入内存块时，`cache_freelist::deallocate` 将对其进行调用。  
  
## <a name="see-also"></a>另请参阅  
 [\<allocators>](../standard-library/allocators-header.md)





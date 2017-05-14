---
title: "max_none 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- max_none
- stdext::max_none
- allocators/stdext::max_none
- allocators/stdext::max_none::allocated
- allocators/stdext::max_none::deallocated
- allocators/stdext::max_none::full
- allocators/stdext::max_none::released
- allocators/stdext::max_none::saved
dev_langs:
- C++
helpviewer_keywords:
- max_none class
ms.assetid: 12ab5376-412e-479c-86dc-2c3d6a3559b6
caps.latest.revision: 19
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
ms.openlocfilehash: a8d3380f89f3bd25be0c23e719dfa94df5539ae4
ms.contentlocale: zh-cn
ms.lasthandoff: 04/29/2017

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





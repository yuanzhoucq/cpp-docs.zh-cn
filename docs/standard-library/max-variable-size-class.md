---
title: "max_variable_size 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- stdext::max_variable_size
- allocators/stdext::max_variable_size
- max_variable_size
- allocators/stdext::max_variable_size::allocated
- allocators/stdext::max_variable_size::deallocated
- allocators/stdext::max_variable_size::full
- allocators/stdext::max_variable_size::released
- allocators/stdext::max_variable_size::saved
dev_langs:
- C++
helpviewer_keywords:
- max_variable_size class
ms.assetid: 9f2e9df0-4148-4b37-bc30-f8eca0ef86ae
caps.latest.revision: 18
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
ms.openlocfilehash: dbb2405313f9b58bc6c5634410a5c378e0f0abca
ms.contentlocale: zh-cn
ms.lasthandoff: 04/29/2017

---
# <a name="maxvariablesize-class"></a>max_variable_size 类
描述 [max 类](../standard-library/allocators-header.md) 对象，该对象将 [freelist](../standard-library/freelist-class.md) 对象限制为与已分配的内存块数大致成比例的最大长度。  
  
## <a name="syntax"></a>语法  
  
```
class max_variable_size
```  
  
### <a name="constructors"></a>构造函数  
  
|||  
|-|-|  
|[max_variable_size](#max_variable_size)|构造 `max_variable_size` 类型的对象。|  
  
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
  
##  <a name="allocated"></a>max_variable_size::allocated  
 逐量增加已分配的内存块的计数。  
  
```
void allocated(std::size_t _Nx = 1);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|`_Nx`|增量值。|  
  
### <a name="remarks"></a>备注  
 此成员函数将 `_Nx` 添加到存储值 `_Nallocs`。 每次调用成功后，`cache_freelist::allocate` 会将此成员函数调用到运算符 `new`。 自变量 `_Nx` 是运算符 `new` 分配的区块中的内存块数。  
  
##  <a name="deallocated"></a>max_variable_size::deallocated  
 逐量减小已分配的内存块的计数。  
  
```
void deallocated(std::size_t _Nx = 1);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|`_Nx`|增量值。|  
  
### <a name="remarks"></a>备注  
 该成员函数从存储值 `_Nallocs` 中减去 `_Nx`。 每次调用后，`cache_freelist::deallocate` 会将此成员函数调用到运算符 `delete`。 自变量 `_Nx` 是运算符 `delete` 取消分配的区块中的内存块数。  
  
##  <a name="full"></a>max_variable_size::full  
 返回一个值，该值指定是否应将更多的内存块添加到空闲列表。  
  
```
bool full();
```  
  
### <a name="return-value"></a>返回值  
 如果 `_Nallocs / 16 + 16 <= _Nblocks`，则为 `true`。  
  
### <a name="remarks"></a>备注  
 此成员函数由 `cache_freelist::deallocate` 调用。 如果调用返回 `true`，则 `deallocate` 会将内存块放入空闲列表；如果它返回 false，则 `deallocate` 将调用运算符 `delete` 以取消分配块。  
  
##  <a name="max_variable_size"></a>max_variable_size::max_variable_size  
 构造 `max_variable_size` 类型的对象。  
  
```
max_variable_size();
```  
  
### <a name="remarks"></a>备注  
 该构造函数将存储的值 `_Nblocks` 和 `_Nallocs` 初始化为零。  
  
##  <a name="released"></a>max_variable_size::released  
 逐量减小空闲列表上内存块的计数。  
  
```
void released();
```  
  
### <a name="remarks"></a>备注  
 此成员函数逐量减小存储值 `_Nblocks`。 每当当前 max 类的 `released` 成员函数从空闲列表中删除内存块时，`cache_freelist::allocate` 将对其进行调用。  
  
##  <a name="saved"></a>max_variable_size::saved  
 逐量增加空闲列表上内存块的计数。  
  
```
void saved();
```  
  
### <a name="remarks"></a>备注  
 此成员函数逐量增加存储值 `_Nblocks`。 每当此成员函数向空闲列表放入内存块时，`cache_freelist::deallocate` 将对其进行调用。  
  
## <a name="see-also"></a>另请参阅  
 [\<allocators>](../standard-library/allocators-header.md)





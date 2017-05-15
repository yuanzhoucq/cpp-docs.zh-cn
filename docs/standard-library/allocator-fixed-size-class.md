---
title: "allocator_fixed_size 类 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- allocators/stdext::allocators::allocator_fixed_size
- allocators::allocator_fixed_size
- allocators/stdext::allocator_fixed_size
- allocator_fixed_size
- stdext::allocators::allocator_fixed_size
dev_langs:
- C++
helpviewer_keywords:
- allocator_fixed_size class
ms.assetid: 138f3ef8-b0b3-49c3-9486-58f2213c172f
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
ms.sourcegitcommit: 4ecf60434799708acab4726a95380a2d3b9dbb3a
ms.openlocfilehash: 95fdb03f48080c309b61df6f760d2d29a7e865ff
ms.contentlocale: zh-cn
ms.lasthandoff: 04/19/2017

---
# <a name="allocatorfixedsize-class"></a>allocator_fixed_size 类
描述一个对象，用于管理由 [max_fixed_size](../standard-library/max-fixed-size-class.md) 所管理的长度的使用缓存类型 [cache_suballoc](../standard-library/cache-freelist-class.md) 的类型 `Type` 的对象的存储分配和释放。  
  
## <a name="syntax"></a>语法  
  
```
template <class Type>  
class allocator_fixed_size;
```  
  
#### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|`Type`|由分配器分配元素类型。|  
  
## <a name="remarks"></a>备注  
 [ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl) 宏将此类传递为以下语句中的 `name` 参数：`ALLOCATOR_DECL(CACHE_FREELIST(stdext::allocators::max_fixed_size<10>), SYNC_DEFAULT, allocator_fixed_size);`  
  
## <a name="requirements"></a>要求  
 **标头：**\<allocators>  
  
 **命名空间：** stdext  
  
## <a name="see-also"></a>另请参阅  
 [\<allocators>](../standard-library/allocators-header.md)





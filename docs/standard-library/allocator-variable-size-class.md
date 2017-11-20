---
title: "allocator_variable_size 类 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- allocators/stdext::allocator_variable_size
- allocators/stdext::allocators::allocator_variable_size
- stdext::allocators::allocator_variable_size
dev_langs: C++
helpviewer_keywords:
- stdext::allocator_variable_size
- stdext::allocators [C++], allocator_variable_size
ms.assetid: c3aa4105-ae45-4385-bbbe-9f23060478cb
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: cb8a6526e57c1af706eb4ee071419aa0550cb6ba
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="allocatorvariablesize-class"></a>allocator_variable_size 类
描述一个对象，用于管理使用缓存类型为 [cache_freelist](../standard-library/cache-freelist-class.md) 的对象类型 `Type` 的存储分配和释放，其长度由 [max_variable_size](../standard-library/max-variable-size-class.md) 管理。  
  
## <a name="syntax"></a>语法  
  
```
template <class Type>  
class allocator_variable_size;
```  
  
#### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|`Type`|由分配器分配元素类型。|  
  
## <a name="remarks"></a>备注  
 [ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl) 宏将此类传递为以下语句中的 `name` 参数：`ALLOCATOR_DECL(CACHE_FREELIST(stdext::allocators::max_variable_size), SYNC_DEFAULT, allocator_variable_size);`  
  
## <a name="requirements"></a>要求  
 **标头：**\<allocators>  
  
 **命名空间：** stdext  
  
## <a name="see-also"></a>另请参阅  
 [\<allocators>](../standard-library/allocators-header.md)




---
title: "allocator_newdel 类 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- allocators/stdext::allocators::allocator_newdel
- allocators/stdext::allocator_newdel
- stdext::allocators::allocator_newdel
dev_langs:
- C++
helpviewer_keywords:
- stdext::allocators [C++], allocator_newdel
- stdext::allocator_newdel
ms.assetid: 62666cd2-3afe-49f7-9dd1-9bbbb154da98
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: 9a86e9f1939c455e4dd9a3bb5c0c2fd252438fba
ms.contentlocale: zh-cn
ms.lasthandoff: 10/03/2017

---
# <a name="allocatornewdel-class"></a>allocator_newdel 类
实现分配器使用 `operator delete` 来释放内存块和使用 `operator new` 来分配内存块。  
  
## <a name="syntax"></a>语法  
  
```
template <class Type>  
class allocator_newdel;
```  
  
#### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|`Type`|由分配器分配元素类型。|  
  
## <a name="remarks"></a>备注  
 [ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl) 宏将此类传递为以下语句中的 `name` 参数：`ALLOCATOR_DECL(CACHE_FREELIST stdext::allocators::max_none), SYNC_DEFAULT, allocator_newdel);`  
  
## <a name="requirements"></a>要求  
 **标头：**\<allocators>  
  
 **命名空间：** stdext  
  
## <a name="see-also"></a>另请参阅  
 [\<allocators>](../standard-library/allocators-header.md)





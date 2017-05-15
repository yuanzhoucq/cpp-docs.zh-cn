---
title: "allocator_newdel 类 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- allocators::allocator_newdel
- allocators/stdext::allocators::allocator_newdel
- allocators/stdext::allocator_newdel
- allocator_newdel
- stdext::allocators::allocator_newdel
dev_langs:
- C++
helpviewer_keywords:
- allocator_newdel class
ms.assetid: 62666cd2-3afe-49f7-9dd1-9bbbb154da98
caps.latest.revision: 18
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
ms.openlocfilehash: 45a80316ddd36cccbe5e5aab6757163d45bc2f07
ms.contentlocale: zh-cn
ms.lasthandoff: 04/19/2017

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





---
title: '&lt;system_error&gt; typedef | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- system_error/std::generic_errno
ms.assetid: 28cf9f7d-9c28-4baa-a297-67c8260b07fb
caps.latest.revision: 11
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: 9b39cb2140e366b983638de212571c9665ea8cbb
ms.contentlocale: zh-cn
ms.lasthandoff: 10/03/2017

---
# <a name="ltsystemerrorgt-typedefs"></a>&lt;system_error&gt; typedef
||  
|-|  
|[generic_errno](#generic_errno)|  
  
##  <a name="generic_errno"></a>  generic_errno  
 一种表示枚举的类型，用于为所有由 `<errno.h>` 中的 Posix 定义的错误代码宏提供符号名称。  
  
```
typedef errc generic_error;
```  
  
### <a name="remarks"></a>备注  
 该类型是 [errc](../standard-library/system-error-enums.md#errc) 的同义词。  
  
## <a name="see-also"></a>另请参阅  
 [<system_error>](../standard-library/system-error.md)





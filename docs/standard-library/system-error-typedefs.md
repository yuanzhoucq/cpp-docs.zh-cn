---
title: '&lt;system_error&gt; typedef | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- system_error/std::generic_errno
ms.assetid: 28cf9f7d-9c28-4baa-a297-67c8260b07fb
caps.latest.revision: 
manager: ghogen
ms.openlocfilehash: f6cda65997e15694d90a03f15fceaa3a6ee5b49c
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
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
  
## <a name="see-also"></a>请参阅  
 [<system_error>](../standard-library/system-error.md)




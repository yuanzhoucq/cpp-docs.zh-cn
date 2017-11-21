---
title: '&lt;new&gt; typedefs | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: new/std::new_handler
ms.assetid: aef01de1-06b5-4b6c-aebc-2c9f423d7e47
caps.latest.revision: "7"
manager: ghogen
ms.openlocfilehash: e23ea06002dc840997a0e7202f581cd81ef407c5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="ltnewgt-typedefs"></a>&lt;new&gt; typedefs
||  
|-|  
|[new_handler](#new_handler)|  
  
##  <a name="new_handler"></a>new_handler  
 该类型指向适合用作新处理程序的函数。  
  
```
typedef void (*new_handler)();
```  
  
### <a name="remarks"></a>备注  
 当它们不能满足额外存储的请求时，**operatornew** 或 `operator new[]` 将调用这种类型的处理程序函数。  
  
### <a name="example"></a>示例  
  有关将 `new_handler` 用作返回值的示例，请参阅 [set_new_handler](../standard-library/new-functions.md#set_new_handler)。  
  
## <a name="see-also"></a>另请参阅  
 [\<new>](../standard-library/new.md)




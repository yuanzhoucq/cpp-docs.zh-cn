---
title: "_WAIT_CHILD、_WAIT_GRANDCHILD | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _WAIT_GRANDCHILD
- WAIT_CHILD
- WAIT_GRANDCHILD
- _WAIT_CHILD
dev_langs: C++
helpviewer_keywords:
- WAIT_CHILD constant
- WAIT_GRANDCHILD constant
- _WAIT_CHILD constant
- _WAIT_GRANDCHILD constant
ms.assetid: 7acd96fa-d118-4339-bb00-e5afaf286945
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1e5e3aa48f0184730a7860ea055d9b233b4ac708
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="waitchild-waitgrandchild"></a>_WAIT_CHILD、_WAIT_GRANDCHILD
## <a name="syntax"></a>语法  
  
```  
  
#include <process.h>  
  
```  
  
## <a name="remarks"></a>备注  
 `_cwait` 函数可以由任何进程用来等待任何其他进程（如果进程 ID 是已知的）。 操作参数可以是以下值之一：  
  
|常量|含义|  
|--------------|-------------|  
|`_WAIT_CHILD`|调用进程一直等到指定的新进程终止。|  
|`_WAIT_GRANDCHILD`|调用进程一直等到指定的新进程以及由该新进程创建的所有进程终止。|  
  
## <a name="see-also"></a>另请参阅  
 [_cwait](../c-runtime-library/reference/cwait.md)   
 [全局常量](../c-runtime-library/global-constants.md)
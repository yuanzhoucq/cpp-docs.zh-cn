---
title: "HUGE_VAL、_HUGE |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _HUGE
apilocation:
- msvcrt.dll
apitype: DLLExport
f1_keywords:
- _HUGE
- HUGE_VAL
dev_langs:
- C++
helpviewer_keywords:
- _HUGE constant
- HUGE_VAL constant
- double value
ms.assetid: 3f044b45-02cd-46b2-b1de-87fd0441dd6a
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 4c70ea331902ac16e99fcfa214af512f780829d8
ms.lasthandoff: 04/01/2017

---
# <a name="hugeval-huge"></a>HUGE_VAL、_HUGE
## <a name="syntax"></a>语法  
  
```  
  
#include <math.h>  
  
```  
  
## <a name="remarks"></a>备注  
 `HUGE_VAL` 是可表示的最大双精度值。 在出现错误时，该值将由许多运行时数学函数返回。 对于某些函数，将返回 -`HUGE_VAL`。 `HUGE_VAL` 定义为 `_HUGE`，而运行时数学函数返回 `HUGE_VAL`。 为确保一致性，还应在代码中使用 `HUGE_VAL`。  
  
## <a name="see-also"></a>另请参阅  
 [全局常量](../c-runtime-library/global-constants.md)

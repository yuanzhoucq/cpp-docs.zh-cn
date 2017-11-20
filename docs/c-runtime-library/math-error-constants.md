---
title: "数学错误常量 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _PLOSS
- _UNDERFLOW
- _TLOSS
- _SING
- _DOMAIN
- _OVERFLOW
dev_langs: C++
helpviewer_keywords:
- _TLOSS constant
- _SING constant
- PLOSS constant
- UNDERFLOW constant
- _UNDERFLOW constant
- _OVERFLOW constant
- DOMAIN constant
- OVERFLOW constant
- TLOSS constant
- SING constant
- _DOMAIN constant
- _PLOSS constant
- math error constants
ms.assetid: 4be933a6-674e-45a5-8ac9-090023542f5b
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 003851227d56469436f7c75396803d80052dca15
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="math-error-constants"></a>数学错误常量
## <a name="syntax"></a>语法  
  
```  
  
#include <math.h>  
  
```  
  
## <a name="remarks"></a>备注  
 运行库的数学例程可生成数学错误常量。  
  
 如下所述，这些错误对应于 MATH.H 中定义的异常类型，并在发生数学错误后由 `_matherr` 函数返回。  
  
|常量|含义|  
|--------------|-------------|  
|`_DOMAIN`|函数的自变量位于函数域的外部。|  
|`_OVERFLOW`|结果太大而无法在函数的返回类型中表示。|  
|`_PLOSS`|发生了有效位部分丢失的情况。|  
|`_SING`|自变量奇异性：函数的自变量具有非法值。 （例如，将值 0 传递到需要非零值的函数。）|  
|`_TLOSS`|发生了有效位完全丢失的情况。|  
|`_UNDERFLOW`|结果太小而无法表示。|  
  
## <a name="see-also"></a>另请参阅  
 [_matherr](../c-runtime-library/reference/matherr.md)   
 [全局常量](../c-runtime-library/global-constants.md)
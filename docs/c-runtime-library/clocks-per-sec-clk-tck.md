---
title: "CLOCKS_PER_SEC、CLK_TCK | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CLOCKS_PER_SEC
- CLK_TCK
dev_langs:
- C++
helpviewer_keywords:
- CLOCKS_PER_SEC
- CLK_TCK constant
ms.assetid: bc285106-383d-44cb-91bf-276ad7de57bf
caps.latest.revision: 6
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
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: 0478b23248912df3d8c8ce41518ccd478293b9ec
ms.contentlocale: zh-cn
ms.lasthandoff: 05/18/2017

---
# <a name="clockspersec-clktck"></a>CLOCKS_PER_SEC、CLK_TCK
## <a name="syntax"></a>语法  
  
```  
  
#include <time.h>  
```  
  
## <a name="remarks"></a>备注  
 时间（以秒为单位）是由 `clock` 函数返回的值除以 `CLOCKS_PER_SEC` 所得的值。 `CLK_TCK` 是等效的，但被视为已过时。  
  
## <a name="see-also"></a>另请参阅  
 [clock](../c-runtime-library/reference/clock.md)   
 [全局常量](../c-runtime-library/global-constants.md)

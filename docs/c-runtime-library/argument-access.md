---
title: "自变量访问 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.arguments
dev_langs:
- C++
helpviewer_keywords:
- argument access macros [C++]
- variable-length argument lists
ms.assetid: 7046ae34-a0ec-44f0-815d-3209492a3e19
caps.latest.revision: 8
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
translationtype: Human Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 66f9ff6dff86bbdff2ec86970a4176f3581316fa
ms.lasthandoff: 03/30/2017

---
# <a name="argument-access"></a>自变量访问
当参数数量可变时，`va_arg`、`va_end` 和 `va_start` 宏提供对函数参数的访问。 为了兼容 ANSI C，STDARG.H 中定义了这些宏。为了兼容 UNIX System V，VARARGS.H 中定义了这些宏。  
  
### <a name="argument-access-macros"></a>参数-访问宏   
  
|宏|使用|  
|-----------|-------------------------------|  
|[va_arg](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)|从列表中检索自变量|  
|[va_end](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)|重置指针|  
|[va_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)|将指针设置到自变量列表的开始位置|  
  
## <a name="see-also"></a>另请参阅  
 [按类别分的运行时例程](../c-runtime-library/run-time-routines-by-category.md)

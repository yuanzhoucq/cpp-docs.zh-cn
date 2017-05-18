---
title: "运行时错误检查 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.runtime
dev_langs:
- C++
helpviewer_keywords:
- run-time error checking
- run-time errors, checking
ms.assetid: c965dd01-57ad-4a3c-b1d6-5aa04f920501
caps.latest.revision: 7
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
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: eb9db9ea42d50faa6e7a693c95795036e650a760
ms.contentlocale: zh-cn
ms.lasthandoff: 03/30/2017

---
# <a name="run-time-error-checking"></a>运行时错误检查
C 运行库包含支持运行时错误检查 (RTC) 的函数。 利用运行时错误检查，您可以生成程序来报告特定类型的运行时错误。 您可指定如何报告错误以及报告哪些类型的错误。 有关详细信息，请参阅[运行时错误检查](http://msdn.microsoft.com/Library/dc7b2f1e-5ff6-42e0-89b3-dc9dead83ee1)。  
  
 使用下列函数自定义程序执行运行时错误检查的方式。  
  
### <a name="run-time-error-checking-functions"></a>运行时错误检查函数  
  
|函数|使用|  
|--------------|---------|  
|[_RTC_GetErrDesc](../c-runtime-library/reference/rtc-geterrdesc.md)|返回运行时错误检查类型的简要描述。|  
|[_RTC_NumErrors](../c-runtime-library/reference/rtc-numerrors.md)|返回可由运行时错误检查检测的错误的总数。|  
|[_RTC_SetErrorFunc](../c-runtime-library/reference/rtc-seterrorfunc.md)|将函数指定为报告运行时错误检查的处理程序。|  
|[_RTC_SetErrorType](../c-runtime-library/reference/rtc-seterrortype.md)|将一个由运行时错误检查检测到的错误与一个类型关联。|  
  
## <a name="see-also"></a>另请参阅  
 [按类别分的运行时例程](../c-runtime-library/run-time-routines-by-category.md)   
 [/RTC（运行时错误检查）](../build/reference/rtc-run-time-error-checks.md)   
 [runtime_checks](../preprocessor/runtime-checks.md)   
 [RTC 示例](http://msdn.microsoft.com/en-us/b3415b09-f6fd-43dc-8c02-9a910bc2574e)   
 [调试例程](../c-runtime-library/debug-routines.md)

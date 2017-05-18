---
title: "异常处理例程 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.exceptions
dev_langs:
- C++
helpviewer_keywords:
- exception handling, routines
ms.assetid: f60548c6-850a-4e1e-a79b-a2a6a541ab62
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
ms.translationtype: Human Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 3dd5d8dd77f2b62a6b0ea52e7d056b3d779cd2f4
ms.contentlocale: zh-cn
ms.lasthandoff: 03/30/2017

---
# <a name="exception-handling-routines"></a>异常处理例程
在程序执行期间使用 C++ 异常处理函数从意外事件恢复。  
  
### <a name="exception-handling-functions"></a>异常处理函数  
  
|函数|使用|  
|--------------|---------|  
|[_set_se_translator](../c-runtime-library/reference/set-se-translator.md)|将 Win32 异常（C 结构的异常）处理为 C++ 类型的异常|  
|[set_terminate](../c-runtime-library/reference/set-terminate-crt.md)|安装 `terminate` 将调用的自身的终止例程|  
|[set_unexpected](../c-runtime-library/reference/set-unexpected-crt.md)|安装 `unexpected` 将调用的自身的终止函数|  
|[terminate](../c-runtime-library/reference/terminate-crt.md)|引发异常后在特定情况下自动调用。 `terminate` 函数可调用 `abort` 或使用 `set_terminate` 指定的函数|  
|[unexpected](../c-runtime-library/reference/unexpected-crt.md)|调用 `terminate` 或使用 `set_unexpected` 指定的函数。 不会在当前 Microsoft C++ 异常处理实现中使用 `unexpected`|  
  
## <a name="see-also"></a>另请参阅  
 [按类别分的运行时例程](../c-runtime-library/run-time-routines-by-category.md)

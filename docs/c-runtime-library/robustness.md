---
title: "可靠性 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.runtime
dev_langs:
- C++
helpviewer_keywords:
- robustness [CRT]
ms.assetid: 7f1a87f8-eff9-4b76-ae9b-d133d3de6adf
caps.latest.revision: 13
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
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 12424d6d233c1c109cb246b6c5b520f2ef12539e
ms.lasthandoff: 02/24/2017

---
# <a name="robustness"></a>稳定性
使用以下 C 运行时库函数以提高程序的可靠性。  
  
### <a name="run-time-robustness-functions"></a>运行时可靠性函数  
  
|函数|使用|.NET Framework 等效项|  
|--------------|---------|-------------------------------|  
|[_set_new_handler](../c-runtime-library/reference/set-new-handler.md)|如果 `new` 运算符无法分配内存，则将控制权传输到错误处理机制。|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_set_se_translator](../c-runtime-library/reference/set-se-translator.md)|将 Win32 异常（C 结构的异常）处理为 C++ 类型的异常。|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[set_terminate](../c-runtime-library/reference/set-terminate-crt.md)|安装要由 [terminate](../c-runtime-library/reference/terminate-crt.md) 调用的自身的终止函数。|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[set_unexpected](../c-runtime-library/reference/set-unexpected-crt.md)|安装要由 [unexpected](../c-runtime-library/reference/unexpected-crt.md) 调用的自身的终止函数。|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
  
## <a name="see-also"></a>另请参阅  
 [按类别分的运行时例程](../c-runtime-library/run-time-routines-by-category.md)   
 [SetUnhandledExceptionFilter](http://msdn.microsoft.com/library/windows/desktop/ms680634.aspx)

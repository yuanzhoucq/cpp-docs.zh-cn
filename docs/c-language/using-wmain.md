---
title: "使用 wmain |Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- wmain function
ms.assetid: d0300812-adc4-40c6-bba3-b2da25468c80
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
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
ms.openlocfilehash: 884d487d5cb2b28dac653f04b409255c44ca1818
ms.contentlocale: zh-cn
ms.lasthandoff: 05/18/2017

---
# <a name="using-wmain"></a>使用 wmain
**Microsoft 专用**  
  
 在 Unicode 编程模型中，可以定义 **main** 函数的宽字符版本。 如果要编写符合 Unicode 编程模型的可移植代码，请使用 wmain 而不是 main。  
  
## <a name="syntax"></a>语法  
  
```  
wmain( int argc, wchar_t *argv[ ], wchar_t *envp[ ] )  
```  
  
## <a name="remarks"></a>备注  
 使用与 main 的相似格式声明 wmain 的形参。 然后可以将宽字符自变量和宽字符环境指针（可选）传递给该程序。 wmain 的 `argv` 和 `envp` 参数为 `wchar_t*` 类型。 例如:   
  
 如果程序使用 main 函数，则多字节字符环境由运行时库在程序启动时创建。 环境的宽字符副本仅在需要时创建（如调用 `_wgetenv` 或 `_wputenv` 函数时）。 在首次调用 `_wputenv` 或首次调用 `_wgetenv` 时（如果 MBCS 环境已存在），会创建一个对应的宽字符字符串环境，然后通过 `_wenviron` 全局变量指向该环境，此变量是 `_environ` 全局变量的宽字符版本。 此时，同时存在该环境的两个副本（MBCS 和 Unicode），在程序的整个生存期这两个副本由操作系统维护。  
  
 同样，如果程序使用 wmain 函数，则在程序启动时创建宽字符环境并用 `_wenviron` 全局变量指向该环境。 MBCS (ASCII) 环境是在首次调用 `_putenv` 或 `getenv` 时创建的，并由 `_environ` 全局变量指向。  
  
 有关 MBCS 环境的详细信息，请参阅《运行时库参考》中的[国际化](../c-runtime-library/internationalization.md)。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>另请参阅  
 [main 函数和程序执行](../c-language/main-function-and-program-execution.md)

---
title: "参数说明 | Microsoft Docs"
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
- envp argument
- main function, syntax
- arguments [C++], for main function
- argv argument
- argc argument
ms.assetid: 91c2cbe3-9aca-4277-afa1-6137eb8fb704
caps.latest.revision: 10
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
ms.openlocfilehash: 588d052380286498181b1062f616618408e5fe99
ms.contentlocale: zh-cn
ms.lasthandoff: 05/18/2017

---
# <a name="argument-description"></a>自变量说明
main 和 wmain 函数中的 `argc` 形参是一个整数，用来指定从命令行传递到程序的实参的数量。 由于程序名被视为实参，因此 `argc` 的值至少有一个。  
  
## <a name="remarks"></a>备注  
 `argv` 形参是一个指针数组，这些指针指向表示程序实参的以 null 结尾的字符串。 该数组的每个元素指向传递给 main（或 wmain）的参数的字符串表示形式。 （有关数组的信息，请参阅[数组声明](../c-language/array-declarations.md)。）`argv` 参数可以声明为指向类型 `char` (`char *argv[]`) 的指针数组，或者声明为一个指针（指向指向类型 `char` (`char **argv`) 的多个指针）。 对于 wmain，`argv` 参数可以声明为指向类型 `wchar_t` (`wchar_t *argv[]`) 的指针数组，或者声明为一个指针（指向类型 `wchar_t` (`wchar_t **argv`) 的多个指针）。  
  
 按照约定，`argv`[0] 是用于调用程序的命令。  但是，可以使用 [CreateProcess](http://msdn.microsoft.com/library/windows/desktop/ms682425) 来生成进程，并且如果同时使用了第一个和第二个参数（`lpApplicationName` 和 `lpCommandLine`），`argv`[0] 可能不是可执行名称；请使用 [GetModuleFileName](http://msdn.microsoft.com/library/windows/desktop/ms683197) 来检索可执行名称。  
  
 最后一个指针 (`argv[argc]`) 是 NULL。 （有关获取环境变量信息的替代方法，请参阅《运行时库参考》中的 [getenv](../c-runtime-library/reference/getenv-wgetenv.md)。）  
  
 **Microsoft 专用**  
  
 `envp` 参数是以 null 结尾的字符串的数组，这些字符串表示在用户的环境变量中设置的值。 `envp` 参数可以声明为 `char` (`char *envp[]`) 的指针数组，或者声明为一个指针（指向指向 `char` (`char **envp`) 的多个指针）。 在 wmain 函数中，`envp` 参数可以声明为指向 `wchar_t` (`wchar_t *envp[]`) 的指针数组，或者声明为一个指针（指向 `wchar_t` (`wchar_t **envp`) 的多个指针）。 数组的末尾由 NULL \* 指针来指示。 请注意，传递给 main 或 wmain 的环境块是当前环境的“冻结”副本。 如果随后通过调用 _putenv 或 `_wputenv` 更改环境，则当前环境（由 `getenv`/`_wgetenv` 以及 `_environ` 或 `_wenviron` 变量返回）将发生更改，但 `envp` 指向的块将不会更改。 `envp` 参数在 C 中是与 ANSI 兼容的，但在 C++ 中却不是如此。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>另请参阅  
 [main 函数和程序执行](../c-language/main-function-and-program-execution.md)

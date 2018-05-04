---
title: 使用 wmain 代替 main |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- wmain
dev_langs:
- C++
helpviewer_keywords:
- main function, vs. wmain
- wmain function
ms.assetid: 7abb1257-b85c-413a-b913-d45b1582a71d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1f8f916fd6716678218b1b9b3d5d8b2e21a37c29
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="using-wmain-instead-of-main"></a>使用 wmain 代替 main
## <a name="microsoft-specific"></a>Microsoft 专用  
 在 Unicode 编程模型中，可以定义 **main** 函数的宽字符版本。 使用**wmain**而不是**主要**如果你想要编写符合 Unicode 规范的可移植代码。  
  
 使用与 main 的相似格式声明 wmain 的形参。 然后可以将宽字符自变量和宽字符环境指针（可选）传递给该程序。 wmain 的 `argv` 和 `envp` 参数为 `wchar_t*` 类型。  
  
 如果程序使用**主要**函数，则多字节字符环境由操作系统在程序启动时创建。 创建环境的宽字符副本仅在需要时 (例如，通过调用[_wgetenv](../c-runtime-library/reference/getenv-wgetenv.md)或[_wputenv](../c-runtime-library/reference/putenv-wputenv.md)函数)。 在首次调用 `_wputenv` 或首次调用 `_wgetenv` 时（如果 MBCS 环境已存在），会创建一个对应的宽字符字符串环境，然后通过 `_wenviron` 全局变量指向该环境，此变量是 `_environ` 全局变量的宽字符版本。 此时，同时存在该环境的两个副本（MBCS 和 Unicode），在程序的整个生存期这两个副本由操作系统维护。  
  
 同样，如果程序使用**wmain**函数，在首次调用创建的 MBCS (ASCII) 环境`_putenv`或`getenv`，并通过指向`_environ`全局变量。  
  
 有关 MBCS 环境的详细信息，请参阅[单字节和多字节字符集](../c-runtime-library/single-byte-and-multibyte-character-sets.md)中*运行时库参考。*  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [main：程序启动](../cpp/main-program-startup.md)
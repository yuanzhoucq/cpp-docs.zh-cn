---
title: 使用 wmain 代替 main
ms.date: 11/04/2016
f1_keywords:
- wmain
helpviewer_keywords:
- main function, vs. wmain
- wmain function
ms.assetid: 7abb1257-b85c-413a-b913-d45b1582a71d
ms.openlocfilehash: 8cdc986d1582d2b26f137e3147ce78bc83e9daca
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50677755"
---
# <a name="using-wmain-instead-of-main"></a>使用 wmain 代替 main

## <a name="microsoft-specific"></a>Microsoft 专用

在 Unicode 编程模型中，可以定义的宽字符版本`main`函数。 使用**wmain**而不是`main`如果你想要编写符合 Unicode 规范的可移植代码。

您将形参声明为**wmain**使用的相似格式`main`。 然后可以将宽字符自变量和宽字符环境指针（可选）传递给该程序。 *Argv*并*envp*参数**wmain**属于类型`wchar_t*`。

如果程序使用`main`函数，则多字节字符环境由操作系统在程序启动时创建。 创建环境的宽字符副本仅在需要时 (例如，通过调用[_wgetenv](../c-runtime-library/reference/getenv-wgetenv.md)或[_wputenv](../c-runtime-library/reference/putenv-wputenv.md)函数)。 在首次调用 `_wputenv` 或首次调用 `_wgetenv` 时（如果 MBCS 环境已存在），会创建一个对应的宽字符字符串环境，然后通过 `_wenviron` 全局变量指向该环境，此变量是 `_environ` 全局变量的宽字符版本。 此时，同时存在该环境的两个副本（MBCS 和 Unicode），在程序的整个生存期这两个副本由操作系统维护。

同样，如果程序使用**wmain**上首次调用函数，创建 MBCS (ASCII) 环境时`_putenv`或`getenv`，并通过指向`_environ`全局变量。

有关 MBCS 环境的详细信息，请参阅[单字节和多字节字符集](../c-runtime-library/single-byte-and-multibyte-character-sets.md)中*运行时库参考。*

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[main：程序启动](../cpp/main-program-startup.md)
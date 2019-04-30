---
title: 进程
ms.date: 11/04/2016
f1_keywords:
- process_cpp
helpviewer_keywords:
- __declspec keyword [C++], process
- process __declspec keyword
ms.assetid: 60eecc2f-4eef-4567-b9db-aaed34733023
ms.openlocfilehash: 049360dddff2b9ca2ea460b96e027e86899f1ecb
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344998"
---
# <a name="process"></a>进程

指定托管应用程序进程在该过程中应具有特定全局变量、静态成员变量或在任何应用程序域之间共享的静态局部变量的单一副本。 这主要用于编译时使用 **/clr: pure**，这是在 Visual Studio 2017 中弃用，在 Visual Studio 2017 中不受支持。 使用编译时 **/clr**，全局和静态变量是每个进程默认情况下并不需要使用 **__declspec （process)**。

只有全局变量、 静态成员变量或本机类型的静态局部变量可以使用标记 **__declspec （process)**。

**进程**编译时才有效[/clr](../build/reference/clr-common-language-runtime-compilation.md)。

如果您希望每个应用程序域具有其自己的全局变量的副本，使用[appdomain](../cpp/appdomain.md)。

请参阅[应用程序域和 Visual C++](../dotnet/application-domains-and-visual-cpp.md)有关详细信息。

## <a name="see-also"></a>请参阅

[__declspec](../cpp/declspec.md)<br/>
[关键字](../cpp/keywords-cpp.md)

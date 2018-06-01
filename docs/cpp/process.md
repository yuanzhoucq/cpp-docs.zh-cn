---
title: 进程 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- process_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], process
- process __declspec keyword
ms.assetid: 60eecc2f-4eef-4567-b9db-aaed34733023
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b36ec42447aa076d0623707951f82b7b9c95d563
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/01/2018
ms.locfileid: "34704901"
---
# <a name="process"></a>进程

指定托管应用程序进程在该过程中应具有特定全局变量、静态成员变量或在任何应用程序域之间共享的静态局部变量的单一副本。 这主要用于编译时使用 **/clr: pure**，是在 Visual Studio 2017 中已过时，在 Visual Studio 2017 中不支持。 使用编译时 **/clr**，全局和静态变量是每个进程的默认情况下并不需要使用`__declspec(process)`。

只有本机类型的全局变量、静态成员变量或静态局部变量可以使用 `__declspec(process)` 标记。

`process` 使用编译时才有效[/clr](../build/reference/clr-common-language-runtime-compilation.md)。

如果你希望每个应用程序域具有其自己的全局变量副本，使用[appdomain](../cpp/appdomain.md)。

请参阅[应用程序域和 Visual C++](../dotnet/application-domains-and-visual-cpp.md)有关详细信息。

## <a name="see-also"></a>请参阅

- [__declspec](../cpp/declspec.md)
- [关键字](../cpp/keywords-cpp.md)

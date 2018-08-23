---
title: 进程 |Microsoft Docs
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
ms.openlocfilehash: fdad177231c02d2e6f6fad171ae1811ecb9ccc6c
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/01/2018
ms.locfileid: "39407177"
---
# <a name="process"></a>进程

指定托管应用程序进程在该过程中应具有特定全局变量、静态成员变量或在任何应用程序域之间共享的静态局部变量的单一副本。 这主要用于编译时使用 **/clr: pure**，这是在 Visual Studio 2017 中弃用，在 Visual Studio 2017 中不受支持。 使用编译时 **/clr**，全局和静态变量是每个进程默认情况下并不需要使用 **__declspec （process)**。

只有全局变量、 静态成员变量或本机类型的静态局部变量可以使用标记 **__declspec （process)**。

**进程**编译时才有效[/clr](../build/reference/clr-common-language-runtime-compilation.md)。

如果您希望每个应用程序域具有其自己的全局变量的副本，使用[appdomain](../cpp/appdomain.md)。

请参阅[应用程序域和 Visual C++](../dotnet/application-domains-and-visual-cpp.md)有关详细信息。

## <a name="see-also"></a>请参阅
 [__declspec](../cpp/declspec.md)  
 [关键字](../cpp/keywords-cpp.md)

---
title: 应用程序域和 Visual c + + |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- interop [C++], application domains
- application domains [C++], C++
- /clr compiler option [C++], application domains
- interoperability [C++], application domains
- mixed assemblies [C++], application domains
ms.assetid: 75a08efc-9b02-40ba-99b7-dcbd71010bbf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: b935b9a5d1561fa1c8b961ee48b92f59b98e2bd2
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/01/2018
ms.locfileid: "34704329"
---
# <a name="application-domains-and-visual-c"></a>应用程序域和 Visual c + +

如果你有`__clrcall`虚拟函数，每个应用程序域 (appdomain) 将是 vtable。 如果在一个 appdomain 中创建的对象，只能调用在该 appdomain 中的虚拟函数。 在混合模式下 (**/clr**) 如果你的类型未包含任何将具有每个进程 vtable`__clrcall`虚函数。 **/Clr: pure**和 **/clr: safe**编译器选项是在 Visual Studio 2015 中已过时，在 Visual Studio 2017 中不支持。

有关详细信息，请参见:

- [appdomain](../cpp/appdomain.md)

- [__clrcall](../cpp/clrcall.md)

- [进程](../cpp/process.md)

## <a name="see-also"></a>请参阅

- [混合（本机和托管）程序集](../dotnet/mixed-native-and-managed-assemblies.md)
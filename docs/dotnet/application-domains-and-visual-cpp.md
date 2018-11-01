---
title: 应用程序域和 Visual C++
ms.date: 11/04/2016
helpviewer_keywords:
- interop [C++], application domains
- application domains [C++], C++
- /clr compiler option [C++], application domains
- interoperability [C++], application domains
- mixed assemblies [C++], application domains
ms.assetid: 75a08efc-9b02-40ba-99b7-dcbd71010bbf
ms.openlocfilehash: 2296654e6935bc40f301226b184cf34f77cb126d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50539264"
---
# <a name="application-domains-and-visual-c"></a>应用程序域和 Visual c + +

如果您有`__clrcall`虚函数，vtable 将为每个应用程序域 (appdomain)。 如果在一个 appdomain 中创建一个对象，只能调用从该 appdomain 中的虚拟函数。 在混合模式下 (**/clr**) 如果您的类型不具有将具有每个进程 vtable`__clrcall`虚函数。 **/Clr: pure**并 **/clr: safe**编译器选项在 Visual Studio 2015 中弃用，在 Visual Studio 2017 中不受支持。

有关详细信息，请参见:

- [appdomain](../cpp/appdomain.md)

- [__clrcall](../cpp/clrcall.md)

- [进程](../cpp/process.md)

## <a name="see-also"></a>请参阅

- [混合（本机和托管）程序集](../dotnet/mixed-native-and-managed-assemblies.md)
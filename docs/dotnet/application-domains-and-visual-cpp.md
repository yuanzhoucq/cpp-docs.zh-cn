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
ms.openlocfilehash: 16c02bb58681ecb241d3552f57e0b05f2d6711b4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208793"
---
# <a name="application-domains-and-visual-c"></a>应用程序域和 Visual C++

如果有 `__clrcall` 虚函数，则 vtable 将为每个应用程序域（appdomain）。 如果在一个 appdomain 中创建对象，则只能从该 appdomain 内调用虚拟函数。 在混合模式（ **/clr**）中，如果类型没有 `__clrcall` 虚函数，则会有每个进程的 vtables。 **/Clr： pure**和 **/clr： safe**编译器选项在 visual studio 2015 中已弃用，在 visual studio 2017 中不受支持。

有关详细信息，请参阅：

- [appdomain](../cpp/appdomain.md)

- [__clrcall](../cpp/clrcall.md)

- [进程](../cpp/process.md)

## <a name="see-also"></a>另请参阅

- [混合（本机和托管）程序集](../dotnet/mixed-native-and-managed-assemblies.md)

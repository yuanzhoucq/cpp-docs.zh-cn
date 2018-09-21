---
title: 混合程序集的库支持 |Microsoft Docs
ms.custom: ''
ms.date: 09/18/2018
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- msvcm90[d].dll
- mixed assemblies [C++], library support
- msvcmrt[d].lib
- libraries [C++], mixed assemblies
ms.assetid: 1229595c-9e9d-414d-b018-b4e4c727576d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 868cae6701e17c79c9856b3a16c63c1e25b67bda
ms.sourcegitcommit: 338e1ddc2f3869d92ba4b73599d35374cf1d5b69
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/20/2018
ms.locfileid: "46494512"
---
# <a name="library-support-for-mixed-assemblies"></a>混合程序集的库支持

Visual c + + 支持 c + + 标准库，C 运行时库 (CRT) 的使用 ATL 和 MFC 与编译的应用程序[/clr （公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md)。 这样，使用这些库使用.NET Framework 的功能的现有应用程序。

> [!IMPORTANT]
> **/Clr: pure**并 **/clr: safe**编译器选项在 Visual Studio 2015 中弃用，在 Visual Studio 2017 中不受支持。

此支持包括 DLL 和导入以下库：

- 如果使用编译的 Msvcmrt [d].lib **/clr**。 混合程序集链接到导入该库。

这一支持提供了多个相关优势：

- CRT 和 c + + 标准库可供混合代码。 CRT 和 c + + 标准库提供不是可验证;从根本上讲，你的调用仍传送到相同的 CRT 和 c + + 标准库使用从本机代码。

- 正确统一的异常处理在混合映像中。

- 混合映像中的 c + + 变量的静态初始化。

- 支持在托管代码中的每个 AppDomain 和每个进程变量。

- 解析应用于在 Visual Studio 2003 及更早版本编译的混合 Dll 加载程序锁问题。

此外，这一支持也有以下限制：

- 仅将 CRT DLL 模型支持编译的代码与 **/clr**。 不存在静态 CRT 库支持 **/clr**生成。


## <a name="see-also"></a>请参阅

- [混合（本机和托管）程序集](../dotnet/mixed-native-and-managed-assemblies.md)

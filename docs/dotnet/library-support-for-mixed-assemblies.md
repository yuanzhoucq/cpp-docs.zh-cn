---
title: 混合程序集的库支持 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: d4b584e0bacb1cb93cad33efdff807bb5fa9c8e2
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704106"
---
# <a name="library-support-for-mixed-assemblies"></a>混合程序集的库支持

Visual c + + 支持 c + + 标准库，C 运行库 (CRT)，使用 ATL 和 MFC 应用程序使用编译[/clr （公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md)。 这样，使用这些库使用.NET Framework 的功能的现有应用程序。

> [!IMPORTANT]
> **/Clr: pure**和 **/clr: safe**编译器选项是在 Visual Studio 2015 中已过时，在 Visual Studio 2017 中不支持。

这种支持包括以下 DLL 和导入库：

- 如果使用编译的 Msvcmrt [d].lib **/clr**。 混合程序集链接到此导入的库。

这一支持提供几个相关优点：

- CRT 和 c + + 标准库可供混合的代码。 CRT 和 c + + 标准库提供不是可验证;从根本上讲，你的调用仍路由到相同的 CRT 和 c + + 标准库随着你从本机代码使用。

- 更正混合映像中的统一的异常处理。

- 混合映像中的 c + + 变量的静态初始化。

- 支持在托管代码中的每个 AppDomain 和每个进程变量。

- 解析应用到编译在 Visual Studio 2003 及更早版本的混合 Dll 加载程序锁定问题。

此外，此项支持有以下限制：

- 仅 CRT DLL 模型支持使用代码编译 **/clr**。 不存在静态 CRT 库支持 **/clr**生成。

你应更新公共语言运行时 (CLR) 到最新版本，因为不保证能够使用早期版本。 用这些更改生成的代码不会在 CLR 版本 1.x。

## <a name="see-also"></a>请参阅

- [混合（本机和托管）程序集](../dotnet/mixed-native-and-managed-assemblies.md)

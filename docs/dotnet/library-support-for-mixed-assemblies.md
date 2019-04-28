---
title: 混合程序集的库支持
ms.date: 09/18/2018
helpviewer_keywords:
- msvcm90[d].dll
- mixed assemblies [C++], library support
- msvcmrt[d].lib
- libraries [C++], mixed assemblies
ms.assetid: 1229595c-9e9d-414d-b018-b4e4c727576d
ms.openlocfilehash: 42116c09d5b31cf669eb6d5d1e75eae60b2610a7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62312003"
---
# <a name="library-support-for-mixed-assemblies"></a>混合程序集的库支持

VisualC++支持使用C++标准库，C 运行时库 (CRT)、 ATL 和 MFC 与编译的应用程序[/clr （公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md)。 这样，使用这些库使用.NET Framework 的功能的现有应用程序。

> [!IMPORTANT]
> **/Clr: pure**并 **/clr: safe**编译器选项在 Visual Studio 2015 中弃用，在 Visual Studio 2017 中不受支持。

此支持包括 DLL 和导入以下库：

- 如果使用编译的 Msvcmrt [d].lib **/clr**。 混合程序集链接到导入该库。

这一支持提供了多个相关优势：

- CRT 和C++标准库可供混合代码。 CRT 和C++标准库提供的不是可验证;从根本上讲，你的调用仍传送到相同的 CRT 和C++为您的标准库使用从本机代码。

- 正确统一的异常处理在混合映像中。

- 静态初始化的C++混合映像中的变量。

- 支持在托管代码中的每个 AppDomain 和每个进程变量。

- 解析应用于在 Visual Studio 2003 及更早版本编译的混合 Dll 加载程序锁问题。

此外，这一支持也有以下限制：

- 仅将 CRT DLL 模型支持编译的代码与 **/clr**。 不存在静态 CRT 库支持 **/clr**生成。

## <a name="see-also"></a>请参阅

- [混合（本机和托管）程序集](../dotnet/mixed-native-and-managed-assemblies.md)

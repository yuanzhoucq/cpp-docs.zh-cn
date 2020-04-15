---
title: 如何：创建部分受信任的应用程序（C++/CLI）
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- partially trusted applications [C++]
- mixed assemblies [C++], partially trusted applications
- msvcm90[d].dll
- interoperability [C++], partially trusted applications
- interop [C++], partially trusted applications
- /clr compiler option [C++], partially trusted applications
ms.assetid: 4760cd0c-4227-4f23-a7fb-d25b51bf246e
ms.openlocfilehash: 9df3a751f4073472b9495425599aaf43878db99a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364407"
---
# <a name="how-to-create-a-partially-trusted-application-by-removing-dependency-on-the-crt-library-dll"></a>如何：通过移除 CRT 库 DLL 上的依赖项来创建部分受信任的应用程序

本主题讨论如何通过删除对 msvcm90.dll 的依赖项，使用 Visual C++创建部分受信任的通用语言运行时应用程序。

使用 **/clr**构建的可视C++应用程序将依赖于 msvcm90.dll，msvcm90.dll 是 C-运行时库的一部分。 当您希望应用程序在部分信任环境中使用时，CLR 将在 DLL 上强制实施某些代码访问安全规则。 因此，有必要删除此依赖项，因为 msvcm90.dll 包含本机代码，并且无法对它强制实施代码访问安全策略。

如果应用程序不使用 C-Runtime 库的任何功能，并且希望从代码中删除对此库的依赖项，则必须使用 **/NODEFAULTLIB：msvcmrt.lib**链接器选项并与 ptrustm.lib 或 ptrustmd.lib 链接。 这些库包含用于应用程序初始化和非初始化的对象文件、初始化代码使用的异常类以及托管异常处理代码。 在这些库中链接将删除对 msvcm90.dll 的任何依赖。

> [!NOTE]
> 对于使用 ptrust 库的应用程序，程序集取消初始化的顺序可能不同。 对于普通应用程序，程序集通常按加载程序集的相反顺序卸载，但这不能保证。 对于部分信任应用程序，程序集的卸载顺序通常与加载程序集的顺序相同。 这也不能保证这一点。

### <a name="to-create-a-partially-trusted-mixed-clr-application"></a>创建部分受信任的混合 （/clr） 应用程序

1. 要删除对 msvcm90.dll 的依赖项，必须指定链接器不要使用 **/NODEFAULTLIB：msvcmrt.lib**链接器选项来包括此库。 有关如何使用可视化工作室开发环境或以编程方式执行此操作的信息，请参阅[/NODEFAULTLIB（忽略库）。](../build/reference/nodefaultlib-ignore-libraries.md)

1. 将其中一个 ptrustm 库添加到链接器输入依赖项。 如果要在发布模式下构建应用程序，请使用 ptrustm.lib。 对于调试模式，请使用 ptrustmd.lib。 有关如何使用 Visual Studio 开发环境或以编程方式执行此操作的信息，请参阅[。Lib 文件作为链接器输入](../build/reference/dot-lib-files-as-linker-input.md)。

## <a name="see-also"></a>另请参阅

[混合（本机和托管）程序集](../dotnet/mixed-native-and-managed-assemblies.md)<br/>
[混合程序集的初始化](../dotnet/initialization-of-mixed-assemblies.md)<br/>
[混合程序集的库支持](../dotnet/library-support-for-mixed-assemblies.md)<br/>
[/link（将选项传递到链接器）](../build/reference/link-pass-options-to-linker.md)

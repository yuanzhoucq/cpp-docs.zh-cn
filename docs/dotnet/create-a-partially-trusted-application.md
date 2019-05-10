---
title: 如何：创建部分受信任的应用程序 (C++/CLI)
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
ms.openlocfilehash: afdfb8ca11753d7def9d7da6f431082b1a90c345
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62209117"
---
# <a name="how-to-create-a-partially-trusted-application-by-removing-dependency-on-the-crt-library-dll"></a>如何：通过移除 CRT 库 DLL 上的依赖项来创建部分受信任的应用程序

本主题介绍了如何创建使用视觉对象的部分受信任的公共语言运行时应用程序C++通过删除对 msvcm90.dll 依赖关系。

视觉对象C++通过生成应用程序 **/clr**将 msvcm90.dll，是 C 运行时库的一部分存在依赖关系。 当你想要在部分信任环境中使用应用程序时，CLR 将强制执行某些代码访问安全性规则对您的 DLL。 因此，将需要删除此依赖关系，因为 msvcm90.dll 包含本机代码，并且不能对其实施代码访问安全性策略。

如果你的应用程序不使用 C 运行时库的任何功能，并且你想要从代码中删除对此库的依赖关系，您将需要使用 **/NODEFAULTLIB:msvcmrt.lib**链接器选项和链接ptrustm.lib 或 ptrustmd.lib。 这些库包含初始化和取消初始化应用程序的对象文件、 异常类使用的初始化代码和托管异常处理代码。 中的这些库的链接将删除对 msvcm90.dll 任何依赖关系。

> [!NOTE]
>  对于使用 ptrust 库的应用程序，程序集取消初始化的顺序可能会有所不同。 对于正常的应用程序，程序集通常情况下卸载的相反顺序加载，但这无法保证。 对于部分信任应用程序，程序集通常情况下卸载的顺序进行加载。 此操作，此外，不保证。

### <a name="to-create-a-partially-trusted-mixed-clr-application"></a>若要创建部分受信任混合 (/ clr) 应用程序

1. 若要删除对 msvcm90.dll 的依赖关系，必须指定到链接器不要将该库包括通过使用 **/NODEFAULTLIB:msvcmrt.lib**链接器选项。 了解如何使用 Visual Studio 开发环境执行此操作，或以编程方式，请参阅[/NODEFAULTLIB （忽略库）](../build/reference/nodefaultlib-ignore-libraries.md)。

1. 将一个 ptrustm 库添加到链接器输入依赖项。 如果要生成你的应用程序在发布模式下，使用 ptrustm.lib。 对于调试模式下，使用 ptrustmd.lib。 了解如何使用 Visual Studio 开发环境执行此操作，或以编程方式，请参阅[。用作链接器输入 lib 文件](../build/reference/dot-lib-files-as-linker-input.md)。

## <a name="see-also"></a>请参阅

[混合（本机和托管）程序集](../dotnet/mixed-native-and-managed-assemblies.md)<br/>
[混合程序集的初始化](../dotnet/initialization-of-mixed-assemblies.md)<br/>
[混合程序集的库支持](../dotnet/library-support-for-mixed-assemblies.md)<br/>
[/link（将选项传递到链接器）](../build/reference/link-pass-options-to-linker.md)

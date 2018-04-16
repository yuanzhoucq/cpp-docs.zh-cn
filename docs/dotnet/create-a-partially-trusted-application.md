---
title: "如何： 创建部分受信任的应用程序 (C + + /cli CLI) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs:
- C++
helpviewer_keywords:
- partially trusted applications [C++]
- mixed assemblies [C++], partially trusted applications
- msvcm90[d].dll
- interoperability [C++], partially trusted applications
- interop [C++], partially trusted applications
- /clr compiler option [C++], partially trusted applications
ms.assetid: 4760cd0c-4227-4f23-a7fb-d25b51bf246e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: dfef7eacfa9da8c55155f6e7ce43dfdb79e67e91
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-create-a-partially-trusted-application-by-removing-dependency-on-the-crt-library-dll"></a>如何：通过移除 CRT 库 DLL 上的依赖项来创建部分受信任的应用程序
本主题讨论如何创建通过移除对 msvcm90.dll 依赖性使用 Visual c + + 的部分受信任公共语言运行时应用程序。  
  
 一个与生成的 Visual c + + 应用程序**/clr**将具有依赖关系 msvcm90.dll，这是 C 运行时库的一部分。 如果你想要在部分信任环境中使用的应用程序时，CLR 将强制执行某些代码访问安全性规则对您的 DLL。 因此，将需要删除此依赖关系，因为 msvcm90.dll 包含本机代码，并且不能对其实施代码访问安全性策略。  
  
 如果你的应用程序不使用任何 C 运行库的功能，你想要在代码中删除对此库的依赖关系，你将需要使用**/NODEFAULTLIB:msvcmrt.lib**链接器选项和链接ptrustm.lib 或 ptrustmd.lib 中。 这些库包含初始化和取消初始化应用程序的对象文件、 异常类使用的初始化代码和托管异常处理代码。 这些库中的一个链接将删除对 msvcm90.dll 任何依赖关系。  
  
> [!NOTE]
>  程序集未初始化的顺序可能与使用 ptrust 库的应用程序不同。 对于普通的应用程序，通常情况程序集卸载顺序相反的顺序，它们已加载的但这不保证。 对于部分信任应用程序，程序集通常情况下卸载它们已加载的相同顺序。 此操作，此外，不保证。  
  
### <a name="to-create-a-partially-trusted-mixed-clr-application"></a>若要创建部分受信任混合 (/ clr) 应用程序  
  
1.  若要删除对 msvcm90.dll 的依赖关系，必须指定到链接器无法通过使用包括此库**/NODEFAULTLIB:msvcmrt.lib**链接器选项。 有关如何使用 Visual Studio 开发环境执行此操作，或以编程方式，请参阅[/NODEFAULTLIB （忽略库）](../build/reference/nodefaultlib-ignore-libraries.md)。  
  
2.  将其中一个 ptrustm 库添加到链接器输入依赖关系。 如果你在构建你的应用程序在发布模式下，请使用 ptrustm.lib。 对于调试模式下，使用 ptrustmd.lib。 有关如何使用 Visual Studio 开发环境执行此操作，或以编程方式，请参阅[。用作链接器输入 lib 文件](../build/reference/dot-lib-files-as-linker-input.md)。  
  
## <a name="see-also"></a>请参阅  
 [混合 （本机和托管） 程序集](../dotnet/mixed-native-and-managed-assemblies.md)   
 [混合程序集的初始化](../dotnet/initialization-of-mixed-assemblies.md)   
 [混合程序集的库支持](../dotnet/library-support-for-mixed-assemblies.md)   
 [/link （将选项传递到链接器）](../build/reference/link-pass-options-to-linker.md)   

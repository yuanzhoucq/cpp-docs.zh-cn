---
title: Dll 的类型 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC DLLs [C++], types
- DLLs [C++], types
- DLLs [C++], MFC
ms.assetid: f6a30db9-6138-4b2c-90cc-a17855e499a6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1ca646c39bbe99ba4ed4059f350d9478b669d408
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45710172"
---
# <a name="kinds-of-dlls"></a>DLL 类型

本主题提供信息以帮助您确定要生成 DLL 的类型。

##  <a name="_core_the_different_kinds_of_dlls_available_with_visual_c.2b2b"></a> 不同类型的 Dll 可用

使用 Visual c + +，可以构建在 C 或 c + + 中不使用 Microsoft 基础类 (MFC) 库的 Win32 Dll。 可以使用 Win32 应用程序向导创建非 MFC DLL 项目。

MFC 库本身不可用，在任一静态链接库或若干 Dll，使用 MFC DLL 向导中。 如果 DLL 使用的 MFC，Visual c + + 支持三种不同的 DLL 开发方案：

- 生成一个常规 MFC DLL 的静态链接 MFC

- 生成一个常规 MFC DLL 的动态链接 MFC

- 构建的 MFC 扩展 DLL，始终动态链接 MFC

### <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [非 MFC DLL：概述](../build/non-mfc-dlls-overview.md)

- [静态链接到 MFC 的规则 MFC Dll](../build/regular-dlls-statically-linked-to-mfc.md)

- [动态链接到 MFC 的规则 MFC Dll](../build/regular-dlls-dynamically-linked-to-mfc.md)

- [MFC 扩展 DLL：概述](../build/extension-dlls-overview.md)

- [要使用的 DLL 哪种类型](#_core_which_kind_of_dll_to_use)

##  <a name="_core_which_kind_of_dll_to_use"></a> 决定哪种类型使用的 DLL

如果您的 DLL 不使用 MFC，使用 Visual c + + 生成非 MFC Win32 DLL。 （静态或动态） 链接到 MFC 的 DLL 将占用大量磁盘空间和内存。 除非 DLL 确实使用 MFC，不应链接到 MFC。

如果您的 DLL 将使用 MFC，并且将由 MFC 或非 MFC 应用程序，必须生成静态链接到 MFC 的规则 MFC DLL 或动态链接到 MFC 的规则 MFC DLL。 在大多数情况下，你可能想要使用动态链接到 MFC，因为该 DLL 的文件大小要小得多，且会在内存中使用共享的版本的 MFC 节省大量的规则 MFC DLL。 如果以静态方式链接到 MFC，您的 DLL 的文件大小将变大并可能占用额外内存，因为它会加载其自己的 MFC 库代码的私有副本。

生成动态链接到 MFC 的 DLL 是比生成静态链接到 MFC，因为它不是链接 MFC 本身所需的 DLL 快。 这是在其中链接器必须压缩调试信息的调试版本中尤其如此。 通过链接已包含调试信息的 DLL，没有较少的调试信息在 DLL 内压缩。

动态链接到 MFC 的一个缺点是必须用 DLL 分发共享的 Dll Mfcx0.dll 和 Msvcrxx.dll （或类似文件）。 MFC Dll 可随便重新发布，但你仍必须将 Dll 安装在安装程序中。 此外，您必须交付 Msvcrxx.dll，其中包含您的程序和 MFC Dll 本身使用的 C 运行时库。

如果 DLL 仅将由 MFC 可执行文件，则必须选择生成规则 MFC DLL 或 MFC 扩展 DLL。 如果您的 DLL 实现从现有的 MFC 类派生的可重用类，或者需要将应用程序和 DLL 之间传递 MFC 派生的对象，则必须生成 MFC 扩展 DLL。

如果 DLL 动态链接到 MFC，可能与您的 DLL 重新分发 MFC Dll。 此体系结构是对共享类库以节省磁盘空间和最大程度减少内存使用情况的多个可执行文件之间特别有用。

之前的版本 4.0 中，Visual c + + 仅支持两种使用 MFC 的 Dll: Usrdll 和 Afxdll。 静态链接到 MFC 的规则 MFC Dll 具有 usrdll 相同的特性。 MFC 扩展 Dll 具有 Afxdll 相同的特性。

### <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [非 MFC DLL：概述](../build/non-mfc-dlls-overview.md)

- [静态链接到 MFC 的规则 MFC Dll](../build/regular-dlls-statically-linked-to-mfc.md)

- [动态链接到 MFC 的规则 MFC Dll](../build/regular-dlls-dynamically-linked-to-mfc.md)

- [MFC 扩展 DLL：概述](../build/extension-dlls-overview.md)

## <a name="see-also"></a>请参阅

[Visual C++ 中的 DLL](../build/dlls-in-visual-cpp.md)
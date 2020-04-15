---
title: DLL 类型
ms.date: 05/06/2019
helpviewer_keywords:
- MFC DLLs [C++], types
- DLLs [C++], types
- DLLs [C++], MFC
ms.assetid: f6a30db9-6138-4b2c-90cc-a17855e499a6
ms.openlocfilehash: dae44d2dd39597420ce2a2c4e1642e8a7f0784e2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328505"
---
# <a name="kinds-of-dlls"></a>DLL 类型

本主题提供的信息可帮助您确定要构建的 DLL 类型。

## <a name="different-kinds-of-dlls-available"></a><a name="_core_the_different_kinds_of_dlls_available_with_visual_c.2b2b"></a>提供不同类型的 DLL

使用 Visual Studio，您可以在 C 或不使用 Microsoft 基础类 （MFC） 库的 C++中构建 Win32 DLL。 您可以使用 Win32 应用程序向导创建非 MFC DLL 项目。

MFC 库本身在静态链接库中或多个 DLL 中可用，带有 MFC DLL 向导。 如果您的 DLL 使用 MFC，Visual Studio 支持三种不同的 DLL 开发方案：

- 构建一个常规的 MFC DLL，以静态方式链接 MFC

- 构建动态链接 MFC 的常规 MFC DLL

- 构建 MFC 扩展 DLL，始终动态链接 MFC

### <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [非 MFC DLL：概述](non-mfc-dlls-overview.md)

- [静态链接到 MFC 的常规 MFC DLL](regular-dlls-statically-linked-to-mfc.md)

- [动态链接到 MFC 的常规 MFC DLL](regular-dlls-dynamically-linked-to-mfc.md)

- [MFC 扩展 DLL：概述](extension-dlls-overview.md)

- [使用哪种 DLL](#_core_which_kind_of_dll_to_use)

## <a name="deciding-which-kind-of-dll-to-use"></a><a name="_core_which_kind_of_dll_to_use"></a>决定使用哪种 DLL

如果您的 DLL 不使用 MFC，请使用 Visual Studio 构建非 MFC Win32 DLL。 将 DLL 链接到 MFC（静态或动态）会占用大量磁盘空间和内存。 除非 DLL 实际使用 MFC，否则不应链接到 MFC。

如果您的 DLL 将使用 MFC，并且将由 MFC 或非 MFC 应用程序使用，则必须构建动态链接到 MFC 的常规 MFC DLL 或静态链接到 MFC 的常规 MFC DLL。 在大多数情况下，您可能需要使用动态链接到 MFC 的常规 MFC DLL，因为 DLL 的文件大小将小得多，并且使用 MFC 的共享版本可以节省内存。 如果静态链接到 MFC，则 DLL 的文件大小将更大，并可能占用额外的内存，因为它加载了 MFC 库代码的私有副本。

构建动态链接到 MFC 的 DLL 比构建一个静态链接到 MFC 的 DLL 更快，因为没有必要链接 MFC 本身。 在调试生成中尤其如此，其中链接器必须压缩调试信息。 通过链接到已包含调试信息的 DLL，DLL 中要压缩的调试信息就更少了。

动态链接到 MFC 的一个缺点是，您必须将共享的 DlL Mfcx0.dll 和 Msvcrxx.dll（或类似文件）与 DLL 一起分发。 MFC DLL 可自由再分发，但您仍必须在安装程序中安装 DLL。 此外，您必须提供 Msvcrxx.dll，其中包含程序和 MFC DLL 本身使用的 C 运行时库。

如果 DLL 仅由 MFC 可执行文件使用，则可以在构建常规 MFC DLL 或 MFC 扩展 DLL 之间进行选择。 如果 DLL 实现了从现有 MFC 类派生的可重用类，或者需要在应用程序和 DLL 之间传递 MFC 派生的对象，则必须构建 MFC 扩展 DLL。

如果您的 DLL 动态链接到 MFC，则 MFC DLL 可能会与您的 DLL 重新分发。 此体系结构对于在多个可执行文件之间共享类库以节省磁盘空间并最大限度地减少内存使用量特别有用。

### <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [非 MFC DLL：概述](non-mfc-dlls-overview.md)

- [静态链接到 MFC 的常规 MFC DLL](regular-dlls-statically-linked-to-mfc.md)

- [动态链接到 MFC 的常规 MFC DLL](regular-dlls-dynamically-linked-to-mfc.md)

- [MFC 扩展 DLL：概述](extension-dlls-overview.md)

## <a name="see-also"></a>另请参阅

[在 Visual Studio 中创建 C/C++ DLL](dlls-in-visual-cpp.md)

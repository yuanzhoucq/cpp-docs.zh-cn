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
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328505"
---
# <a name="kinds-of-dlls"></a>DLL 类型

本主题提供的信息可帮助你确定要生成的 DLL 的类型。

## <a name="different-kinds-of-dlls-available"></a><a name="_core_the_different_kinds_of_dlls_available_with_visual_c.2b2b"></a>不同类型的可用 DLL

借助 Visual Studio，可以在不使用 Microsoft 基础类 (MFC) 库的 C 或 C++ 中生成 Win32 DLL。 你可以使用 Win32 应用程序向导创建非 MFC DLL 项目。

MFC 库本身可以通过 MFC DLL 向导用于静态链接库或多个 DLL。 如果你的 DLL 使用 MFC，Visual Studio 支持三种不同的 DLL 开发方案：

- 生成静态链接 MFC 的规则 MFC DLL

- 生成动态链接 MFC 的规则 MFC DLL

- 生成始终动态链接 MFC 的 MFC 扩展 DLL

### <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [非 MFC DLL：概述](non-mfc-dlls-overview.md)

- [静态链接到 MFC 的规则 MFC DLL](regular-dlls-statically-linked-to-mfc.md)

- [动态链接到 MFC 的规则 MFC DLL](regular-dlls-dynamically-linked-to-mfc.md)

- [MFC 扩展 DLL：概述](extension-dlls-overview.md)

- [要使用的 DLL 的类型](#_core_which_kind_of_dll_to_use)

## <a name="deciding-which-kind-of-dll-to-use"></a><a name="_core_which_kind_of_dll_to_use"></a>决定要使用的 DLL 的类型

如果你的 DLL 不使用 MFC，请使用 Visual Studio 生成非 MFC Win32 DLL。 将你的 DLL 链接到 MFC（静态或动态）会占用大量磁盘空间和内存。 除非你的 DLL 实际使用 MFC，否则不应链接到 MFC。

如果你的 DLL 将使用 MFC，并将由 MFC 或非 MFC 应用程序使用，则必须生成动态链接到 MFC 的规则 MFC DLL 或静态链接到 MFC 的规则 MFC DLL。 在大多数情况下，你可能希望使用动态链接到 MFC 的规则 MFC DLL，因为该 DLL 的文件大小会小得多，并且使用 MFC 的共享版本可以节省大量内存。 如果静态链接到 MFC，则 DLL 的文件大小将会更大，并且可能会占用额外的内存，因为它会加载自己的 MFC 库代码专用副本。

生成动态链接到 MFC 的 DLL 比生成静态链接到 MFC 的 DLL 速度要快，因为不需要链接 MFC 本身。 在链接器必须压缩调试信息的调试版本中更是如此。 通过与已经包含调试信息的 DLL 链接，你的 DLL 中要压缩的调试信息会变少。

动态链接到 MFC 的一个缺点是，必须与你的 DLL 一起发行共享的 DLL Mfcx0.dll 和 Msvcrxx.dll（或类似文件）。 可以随意再发行 MFC DLL，但仍然必须在安装程序中安装 DLL。 此外，还必须提供 Msvcrxx.dll，其中包含程序和 MFC DLL 本身使用的 C 运行时库。

如果你的 DLL 仅由 MFC 可执行文件使用，则可以在生成规则 MFC DLL 和 MFC 扩展 DLL 之间进行选择。 如果你的 DLL 实现从现有 MFC 类派生的可重用类，或者需要在应用程序和 DLL 之间传递 MFC 派生的对象，则必须生成 MFC 扩展 DLL。

如果你的 DLL 动态链接到 MFC，则 MFC DLL 可能会随 DLL 再发行。 此体系结构特别适合在多个可执行文件之间共享类库，以节省磁盘空间并最大限度地减少内存使用量。

### <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [非 MFC DLL：概述](non-mfc-dlls-overview.md)

- [静态链接到 MFC 的规则 MFC DLL](regular-dlls-statically-linked-to-mfc.md)

- [动态链接到 MFC 的规则 MFC DLL](regular-dlls-dynamically-linked-to-mfc.md)

- [MFC 扩展 DLL：概述](extension-dlls-overview.md)

## <a name="see-also"></a>请参阅

[在 Visual Studio 中创建 C/C++ DLL](dlls-in-visual-cpp.md)

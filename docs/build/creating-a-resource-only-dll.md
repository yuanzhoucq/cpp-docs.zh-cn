---
title: 创建纯资源 DLL
description: 如何在 Visual Studio 中创建纯资源 DLL。
ms.date: 01/27/2020
helpviewer_keywords:
- resource-only DLLs [C++], creating
- DLLs [C++], creating
ms.assetid: e6b1d4da-7275-467f-a58c-a0a8a5835199
no-loc:
- noentry
ms.openlocfilehash: ef79de77e35cbef6acd4af1cec82a4edc1b7d105
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821338"
---
# <a name="creating-a-resource-only-dll"></a>创建纯资源 DLL

纯资源 DLL 是指只包含资源（例如图标、位图、字符串和对话框）的 DLL。 使用纯资源 DLL 可以很好地在多个程序之间共享同一组资源。 也可以很好地向应用程序提供已本地化为多种语言的资源。 有关详细信息，请参阅 [MFC 应用程序中已本地化的资源：附属 DLL](localized-resources-in-mfc-applications-satellite-dlls.md)。

## <a name="create-a-resource-only-dll"></a>创建纯资源 DLL

若要创建纯资源 DLL，请创建一个新的 Windows DLL（非 MFC）项目，并将资源添加到该项目中：

::: moniker range="vs-2015"

1. 在“新建项目”  对话框中选择“Win32 项目”  。 输入项目和解决方案名称，然后选择“确定”  。

1. 在“Win32 应用程序向导”  中，选择“应用程序设置”  。 为“应用程序类型”选择“DLL”   。 在“附加选项”  下，选择“空项目”  。 选择“完成”  以创建项目。

1. 创建一个新的资源脚本，其中包含 DLL 的资源（例如字符串或菜单）。 保存 `.rc` 文件。

1. 在“项目”  菜单上，选择“添加现有项”  ，然后将新的 `.rc` 文件插入项目中。

1. 指定 [/NOENTRY](reference/noentry-no-entry-point.md) 链接器选项。 `/NOENTRY` 可防止链接器将对 `_main` 的引用链接到 DLL 中；创建纯资源 DLL 时需要使用此选项。

1. 生成 DLL。

::: moniker-end
::: moniker range=">=vs-2017"

1. 在“新建项目”  对话框中选择“Windows 桌面向导”  ，然后选择“下一步”  。 在“配置新项目”  页面上，输入项目和解决方案名称，然后选择“创建”  。

1. 在“Windows 桌面项目”  对话框中，为“应用程序类型”选择“动态链接库”   。 在“附加选项”  下，选择“空项目”  。 选择“确定”  以创建项目。

1. 创建一个新的资源脚本，其中包含 DLL 的资源（例如字符串或菜单）。 保存 `.rc` 文件。

1. 在“项目”  菜单上，选择“添加现有项”  ，然后将新的 `.rc` 文件插入项目中。

1. 指定 [/NOENTRY](reference/noentry-no-entry-point.md) 链接器选项。 `/NOENTRY` 可防止链接器将对 `_main` 的引用链接到 DLL 中；创建纯资源 DLL 时需要使用此选项。

1. 生成 DLL。

::: moniker-end

## <a name="use-a-resource-only-dll"></a>使用纯资源 DLL

使用纯资源 DLL 的应用程序应调用 [LoadLibraryEx](loadlibrary-and-afxloadlibrary.md) 或相关函数，以便显式链接到该 DLL。 若要访问资源，请调用泛型函数 `FindResource` 和 `LoadResource`，它们对任何类型的资源都有效。 或者，调用以下特定于资源的函数之一：

- `FormatMessage`

- `LoadAccelerators`

- `LoadBitmap`

- `LoadCursor`

- `LoadIcon`

- `LoadMenu`

- `LoadString`

应用程序在用完资源后，应调用 `FreeLibrary`。

## <a name="see-also"></a>请参阅

[使用资源文件](../windows/working-with-resource-files.md)\
[在 Visual Studio 中创建 C/C++ DLL](dlls-in-visual-cpp.md)

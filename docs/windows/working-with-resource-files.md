---
title: 使用资源文件 (C++)
ms.date: 02/14/2019
helpviewer_keywords:
- resources [C++], about resources
- resources [C++], about resource files
- resource files [C++], about resource files
ms.assetid: 2699a539-b369-4b78-80f0-df03eb7b6780
ms.openlocfilehash: d9f6c6b9798bc708bb5334eafc0585471f25c059
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513590"
---
# <a name="working-with-resource-files"></a>使用资源文件

> [!WARNING]
> 本节适用于采用 C++ 编写的 Windows 桌面应用程序。
>
> C++有关在中编写的通用 Windows 平台应用中的资源的信息, 请参阅[定义应用资源](/windows/uwp/app-resources/)或将C++资源添加到/cli (托管) 项目, 请参阅[桌面应用](/dotnet/framework/resources/index)中的资源 .NET Framework 开发人员向导.

资源可以由各种各样的元素组成, 如下所示:

- 向用户提供信息 (如位图、图标或光标) 的接口元素。
- 包含数据和应用程序需求的自定义资源。
- 安装 Api 使用的版本资源。
- 菜单和对话框资源。

可以向项目添加新资源并使用适当的资源编辑器修改这些资源。 大多数 Visual C++ 向导自动为项目生成 .rc 文件。

> [!NOTE]
> **资源编辑器**和**资源视图**在 Express 版本中不可用。

若要手动将资源文件添加到托管项目, 请参阅[创建桌面应用的资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 本文包括如何访问资源、显示静态资源和将资源字符串分配给属性。

若要全球化和本地化托管应用中的资源, 请参阅[.NET Framework 应用程序进行全球化和本地化](/dotnet/standard/globalization-localization/index)。

## <a name="in-this-section"></a>本节内容

[资源文件](../windows/resource-files-visual-studio.md)<br/>
描述资源文件以及在 Windows 桌面应用程序中使用它们的方式。 还提供指向描述如何使用资源文件的文章的链接。

[资源标识符（符号）](../windows/symbols-resource-identifiers.md)<br/>
描述符号并提供有关在项目中使用 **“资源符号”** 对话框管理符号的信息。

[资源编辑器](../windows/resource-editors.md)<br/>
介绍 Visual Studio 中提供的资源编辑器, 以及可通过每个编辑器修改的资源类型。 还提供了有关使用每个编辑器的详细信息的链接。

## <a name="related-sections"></a>相关章节

[Visual Studio 中的 C++](../overview/visual-cpp-in-visual-studio.md)<br/>
提供 Visual C++ 文档的链接。

[与我们交流](/visualstudio/ide/talk-to-us)<br/>
提供指向特定信息的链接，这些信息说明如何使用文档集、如何与产品支持部门联系以及如何使用辅助功能。

## <a name="see-also"></a>请参阅

[Windows 桌面应用程序](../windows/windows-desktop-applications-cpp.md)<br/>
[菜单和其他资源](/windows/win32/menurc/resources)
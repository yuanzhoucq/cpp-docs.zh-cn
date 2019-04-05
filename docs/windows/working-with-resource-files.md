---
title: 使用资源文件 （c + +）
ms.date: 02/14/2019
helpviewer_keywords:
- resources [C++], about resources
- resources [C++], about resource files
- resource files [C++], about resource files
ms.assetid: 2699a539-b369-4b78-80f0-df03eb7b6780
ms.openlocfilehash: a08c7ecb153b790f06da386ac93d1f05f5981e61
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59037722"
---
# <a name="working-with-resource-files"></a>使用资源文件

> [!WARNING]
> 本节适用于采用 C++ 编写的 Windows 桌面应用程序。
>
> 有关 c + + 编写的通用 Windows 平台应用中的资源的信息，请参阅[定义应用的资源](/windows/uwp/app-resources/)，或将资源添加到 C + + /cli （托管） 的 CLI 项目，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中.NET Framework 开发人员指南。

资源可以组成任务的各种元素，如：

- 向位图、 图标或光标等用户提供信息的界面元素。
- 包含数据和应用程序的自定义资源需求。
- 由安装 Api 使用的版本资源。
- 菜单和对话框资源。

可以向项目添加新资源并使用适当的资源编辑器修改这些资源。 大多数 Visual C++ 向导自动为项目生成 .rc 文件。

> [!NOTE]
> **资源编辑器**并**资源视图**在 Express 版本中不可用。

若要手动将资源文件添加到托管项目，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 本文包含如何访问资源、 显示静态资源以及将资源字符串分配给属性。

若要进行全球化和本地化托管应用中的资源，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="in-this-section"></a>本节内容

[资源文件](../windows/resource-files-visual-studio.md)<br/>
描述资源文件以及如何在 Windows 桌面应用程序中使用。 此外提供了指向介绍如何使用资源文件的文章。

[资源标识符 （符号）](../windows/symbols-resource-identifiers.md)<br/>
描述符号并提供有关在项目中使用 **“资源符号”** 对话框管理符号的信息。

[资源编辑器](../windows/resource-editors.md)<br/>
介绍在 Visual Studio 和类型的资源可以用各个编辑器修改提供的资源编辑器。 有关使用各编辑器还提供指向详细信息。

## <a name="related-sections"></a>相关章节

[Visual C++](../overview/visual-cpp-in-visual-studio.md)<br/>
提供 Visual C++ 文档的链接。

[Talk to Us](/visualstudio/ide/talk-to-us)<br/>
提供指向特定信息的链接，这些信息说明如何使用文档集、如何与产品支持部门联系以及如何使用辅助功能。

## <a name="see-also"></a>请参阅

[Windows 桌面应用程序](../windows/windows-desktop-applications-cpp.md)<br/>
[菜单和其他资源](https://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)
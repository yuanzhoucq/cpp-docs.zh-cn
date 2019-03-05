---
title: TN020:ID 命名和编号约定
ms.date: 11/04/2016
f1_keywords:
- vc.id
helpviewer_keywords:
- TN020
- resource identifiers, naming and numbering
- resource identifiers
ms.assetid: aecbd2cf-68b3-47f6-ae21-b1f507917245
ms.openlocfilehash: f1cd44ed448cc4c0fc60d490a613f0ad91071376
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57267389"
---
# <a name="tn020-id-naming-and-numbering-conventions"></a>TN020:ID 命名和编号约定

本说明介绍 ID 命名和编号约定，MFC 2.0 使用的资源、 命令、 字符串、 控件和子窗口。

MFC ID 命名和编号约定旨在满足以下要求：

- 提供跨 MFC 库和 MFC 应用程序支持的 Visual c + + 资源编辑器使用一致的 ID 命名标准。 这便于程序员能够解释的类型和其 id。 从资源来源

- 强调某些类型的 Id 之间的强 1 对 1 关系。

- 符合已广泛使用标准命名 Windows 中的 Id。

- 分区的 ID 编号的空间。 可由程序员、 MFC、 Windows 和 Visual c + + 编辑资源分配的 ID 号。 适当的分区将有助于避免重复的 ID 号。

## <a name="the-id-prefix-naming-convention"></a>ID 前缀命名约定

应用程序中可能会出现多个类型的 Id。 MFC ID 命名约定定义不同资源类型的不同的前缀。

MFC 使用的前缀"IDR_"来指示适用于多个资源类型的资源 ID。 例如，对于给定的框架窗口中，MFC 使用的相同"IDR_"前缀来指示菜单、 快捷键、 字符串和图标资源。 下表显示了各种前缀和其使用情况：

|前缀|使用|
|------------|---------|
|IDR_|为多个资源类型 （主要是使用菜单、 快捷键、 功能区的）。|
|IDD_|对话框模板资源 (例如，IDD_DIALOG1)。|
|IDC_|对于游标资源。|
|IDI_|对于图标资源。|
|IDB_|对于位图资源。|
|IDS_|对于字符串资源。|

在对话框资源中，MFC 遵循以下约定：

|前缀或标签|使用|
|---------------------|---------|
|IDOK IDCANCEL|有关标准下压按钮 Id。|
|IDC_|其他对话框控件。|

为游标还使用"IDC_"前缀。 此命名冲突通常不是问题由于典型的应用程序将具有几个游标和许多对话框控件。

在菜单资源中，MFC 遵循以下约定：

|前缀|使用|
|------------|---------|
|IDM_|对于不使用 MFC 命令体系结构的菜单项。|
|ID_|使用 MFC 命令体系结构的菜单命令。|

命令遵循 MFC 命令体系结构必须 ON_COMMAND 命令处理程序，并且可以具有 ON_UPDATE_COMMAND_UI 处理程序。 如果这些命令处理程序遵循 MFC 命令体系结构，它们将正常运行它们是否已绑定到菜单命令、 工具栏按钮或对话框任务栏按钮。 相同的"ID_"前缀还用于在程序的消息栏上显示的菜单提示字符串。 在应用程序中的菜单项的大多数都应遵循 MFC 命令约定。 所有标准命令 Id (例如，ID_FILE_NEW) 都遵循此约定。

MFC 还使用"IDP_"作为一种特殊形式的字符串 （而不是"IDS_")。 使用"IDP_"前缀的字符串是提示，也就是说，消息框中使用的字符串。 "IDP_"字符串可以包含"%1"和"%2"作为占位符的字符串由该程序。 "IDP_"字符串通常采用与它们相关联的帮助主题，并且"IDS_"字符串。 "IDP_"字符串始终被本地化，并可能不会本地化"IDS_"字符串。

MFC 库还使用"IDW_"前缀，作为一种特殊形式的控件 Id （而不是"IDC_")。 这些 Id 分配给子窗口，如视图和拆分条由 framework 类。 MFC 实现 Id 前缀为"AFX_"。

## <a name="the-id-numbering-convention"></a>ID 编号约定

下表列出的有效范围为特定类型的 Id。 一些限制采用技术实现限制，其他采用旨在防止应用 Id 与 Windows 预定义的 Id 或 MFC 冲突的默认实现的约定。

我们强烈建议你定义在建议的范围内的所有 Id。 这些范围的下限为 1，因为不使用 0。 我们建议你使用的常见约定并使用 100 或 101 作为第一个 id。

|前缀|资源类型|有效范围|
|------------|-------------------|-----------------|
|IDR_|多个|1 到 0x6FFF|
|IDD_|对话框模板|1 到 0x6FFF|
|IDC_,IDI_,IDB_|光标、 图标、 位图|1 到 0x6FFF|
|IDS_ IDP_|常规字符串|1 到 0x7FFF|
|ID_|命令|0x8000 到 0xDFFF|
|IDC_|控件|8 到 0xDFFF|

这些范围限制的原因：

- 按照约定，不使用的 ID 值为 0。

- Windows 实现的限制，则返回 true 的资源 Id 小于或等于 0x7FFF。

- MFC 的内部框架保留这些范围：

  - 通过 0x7FFF 0x7000 （请参阅 afxres.h）

  - 通过 0xEFFF 0xE000 （请参阅 afxres.h）

  - 16000 通过 18000 （请参阅 afxribbonres.h）

  这些范围可能会更改在将来的 MFC 实现。

- Windows 系统的多个命令使用 0xF000 到 0xFFFF 的范围。

- 1 到 7 的控件 Id 被保留的标准控件如 IDOK 和 IDCANCEL。

- 0x8000 到 0xFFFF 的字符串的范围被保留的菜单会提示你输入命令。

## <a name="see-also"></a>请参阅

[按编号列出的技术说明](../mfc/technical-notes-by-number.md)<br/>
[按类别列出的技术说明](../mfc/technical-notes-by-category.md)

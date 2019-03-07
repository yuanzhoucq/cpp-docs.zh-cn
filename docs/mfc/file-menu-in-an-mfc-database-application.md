---
title: MFC 数据库应用程序中的文件菜单
ms.date: 11/04/2016
helpviewer_keywords:
- File menu
- database applications [MFC], File menu commands
ms.assetid: 92dafb75-c1b3-4860-80a0-87a83bfc36f2
ms.openlocfilehash: 6c9a195a81423417809b65b5edce32027071ad2e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57279115"
---
# <a name="file-menu-in-an-mfc-database-application"></a>MFC 数据库应用程序中的文件菜单

如何应解释打开、 关闭、 保存，和另存为创建 MFC 数据库应用程序并不使用序列化时，如果文件菜单命令尽管有此问题没有风格指导原则，此处是一些建议：

- 完全消除“文件”菜单的“打开”命令。

- 将“打开”命令解释为“打开数据库”，并向用户显示应用程序识别的数据源的列表。

- 也可将“打开”命令解释为“打开配置文件”。 保留“打开”命令以打开序列化的文件，但使用该文件存储包含“用户配置文件”信息（如用户首选项）的序列化文档，包括用户的登录 ID（可以选择排除密码）和用户最近使用的数据源。

MFC 应用程序向导支持使用不与任何文档相关的“文件”菜单命令创建应用程序。 选择**数据库不支持文件的视图**选项卡上**数据库支持**页。

若要以特定方法解释“文件”菜单命令，您必须重写一个或多个命令处理程序，这些处理程序大多出现在 `CWinApp` 派生的类中。 例如，如果完全重写 `OnFileOpen`（可实现 `ID_FILE_OPEN` 命令）来表示“打开数据库”：

- 不要调用 `OnFileOpen` 的基类版本，因为您将完全替换框架对此命令的默认实现。

- 而是使用处理程序来显示一个列出了数据源的对话框。 可以通过调用显示这类对话框`CDatabase::OpenEx`或`CDatabase::Open`与参数**NULL**。 这将打开一个 ODBC 对话框，其中显示用户计算机上所有可用的数据源。

- 由于数据库应用程序通常不会保存整个文档，因此您可能需要删除“保存”或“另存为”实现，除非您使用序列化的文档存储配置文件信息。 否则，你可能会将“保存”命令作为“提交事务”实现。 请参阅[技术说明 22](../mfc/tn022-standard-commands-implementation.md)有关重写这些命令的详细信息。

## <a name="see-also"></a>请参阅

[序列化：序列化与数据库输入/输出](../mfc/serialization-serialization-vs-database-input-output.md)

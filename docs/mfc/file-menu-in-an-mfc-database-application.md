---
title: MFC 数据库应用程序中的文件菜单
ms.date: 11/04/2016
helpviewer_keywords:
- File menu
- database applications [MFC], File menu commands
ms.assetid: 92dafb75-c1b3-4860-80a0-87a83bfc36f2
ms.openlocfilehash: fbbb4382749278708e8e758f79a618d5cad0549e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615702"
---
# <a name="file-menu-in-an-mfc-database-application"></a>MFC 数据库应用程序中的文件菜单

如果创建的是 MFC 数据库应用程序，并且不使用序列化，则应如何在 "文件" 菜单上解释 "打开"、"关闭"、"保存" 和 "另存为" 命令，因为没有针对此问题的样式准则，以下是一些建议：

- 完全消除“文件”菜单的“打开”命令。

- 将“打开”命令解释为“打开数据库”，并向用户显示应用程序识别的数据源的列表。

- 也可将“打开”命令解释为“打开配置文件”。 保留“打开”命令以打开序列化的文件，但使用该文件存储包含“用户配置文件”信息（如用户首选项）的序列化文档，包括用户的登录 ID（可以选择排除密码）和用户最近使用的数据源。

MFC 应用程序向导支持使用不与任何文档相关的“文件”菜单命令创建应用程序。 在**数据库支持**页上，选择 "**没有文件支持的数据库视图**" 选项。

若要以特定方法解释“文件”菜单命令，您必须重写一个或多个命令处理程序，这些处理程序大多出现在 `CWinApp` 派生的类中。 例如，如果完全重写 `OnFileOpen`（可实现 `ID_FILE_OPEN` 命令）来表示“打开数据库”：

- 不要调用 `OnFileOpen` 的基类版本，因为您将完全替换框架对此命令的默认实现。

- 而是使用处理程序来显示一个列出了数据源的对话框。 可以通过调用 `CDatabase::OpenEx` 或 `CDatabase::Open` 参数**NULL**来显示此类对话框。 这将打开一个 ODBC 对话框，其中显示用户计算机上所有可用的数据源。

- 由于数据库应用程序通常不会保存整个文档，因此您可能需要删除“保存”或“另存为”实现，除非您使用序列化的文档存储配置文件信息。 否则，你可能会将“保存”命令作为“提交事务”实现。 有关替代这些命令的详细信息，请参阅[技术说明 22](tn022-standard-commands-implementation.md) 。

## <a name="see-also"></a>另请参阅

[序列化：序列化与数据库输入/输出的对比](serialization-serialization-vs-database-input-output.md)

---
title: TN048：为 MFC 数据库应用程序编写 ODBC 安装和管理程序
ms.date: 11/04/2016
helpviewer_keywords:
- installing ODBC
- ODBC, installing
- setup, ODBC setup programs
- TN048
- ODBC, and MFC
- MFC, database applications
ms.assetid: d456cdd4-0513-4a51-80c0-9132b66115ce
ms.openlocfilehash: d25520c4ffc805701dfe6b51192f8078e2fa300f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365486"
---
# <a name="tn048-writing-odbc-setup-and-administration-programs-for-mfc-database-applications"></a>TN048：为 MFC 数据库应用程序编写 ODBC 安装和管理程序

> [!NOTE]
> 以下技术说明在首次包括在联机文档中后未更新。 因此，某些过程和主题可能已过时或不正确。 要获得最新信息，建议你在联机文档索引中搜索热点话题。

使用 MFC 数据库类的应用程序将需要安装 ODBC 组件的安装程序。 他们可能需要一个 ODBC 管理程序，它将检索有关可用驱动程序的信息，指定默认驱动程序和配置数据源。 本说明介绍了使用 ODBC 安装程序 API 编写这些程序。

## <a name="writing-an-odbc-setup-program"></a><a name="_mfcnotes_writing_an_odbc_setup_program"></a>编写 ODBC 安装程序

MFC 数据库应用程序需要 ODBC 驱动程序管理器 （ODBC）。DLL） 和 ODBC 驱动程序能够访问数据源。 许多 ODBC 驱动程序还需要额外的网络和通信 DLL。 大多数 ODBC 驱动程序附带一个安装程序，将安装所需的 ODBC 组件。 使用 MFC 数据库类的应用程序开发人员可以：

- 使用特定于驱动程序的安装程序来安装 ODBC 组件。 这将不需要开发人员的进一步工作 - 您可以重新分发驱动程序的安装程序。

- 或者，您可以编写自己的安装程序，这将安装驱动程序管理器和驱动程序。

ODBC 安装程序 API 可用于编写特定于应用程序的安装程序。 安装程序 API 中的函数由 ODBC 安装程序 DLL 和 ODBCINST 实现。16 位 Windows 和 ODBCCP32 上的 DLL。DLL 上 Win32。 应用程序可以调用`SQLInstallODBC`安装程序 DLL，它将安装 ODBC 驱动程序管理器、ODBC 驱动程序和任何必需的转换器。 然后，它会在 ODBCINST 中记录已安装的驱动程序和译员。INI 文件（或注册表，在 NT 上）。 `SQLInstallODBC`需要到 ODBC 的完整路径。INF 文件，其中包含要安装的驱动程序列表，并描述构成每个驱动程序的文件。 它还包含有关驱动程序管理器和译员的类似信息。 Odbc。INF 文件通常由驱动程序开发人员提供。

程序还可以安装单个 ODBC 组件。 要安装驱动程序管理器，程序首先在安装程序`SQLInstallDriverManager`DLL 中调用以获取驱动程序管理器的目标目录。 这通常是 Windows DLL 所在的目录。 然后，程序使用 ODBC [ODBC 驱动程序管理器] 部分中的信息。INF 文件将驱动程序管理器和相关文件从安装磁盘复制到此目录。 要安装单个驱动程序，程序首先调用`SQLInstallDriver`安装程序 DLL 中，将驱动程序规范添加到 ODBCINST。INI 文件（或注册表，在 NT 上）。 `SQLInstallDriver`返回驱动程序的目标目录 - 通常是 Windows DLL 所在的目录。 然后，程序使用 ODBC 驱动程序部分中的信息。INF 文件将驱动程序 DLL 和相关文件从安装磁盘复制到此目录。

有关 ODBC 的更多信息。INF，药点。INI 和使用安装程序 API，请参阅 ODBC SDK*程序员参考，* 第 19 章，安装 ODBC 软件。

## <a name="writing-an-odbc-administrator"></a><a name="_mfcnotes_writing_an_odbc_administrator"></a>编写 ODBC 管理员

MFC 数据库应用程序可以通过以下两种方式之一设置和配置 ODBC 数据源：

- 使用 ODBC 管理员（作为程序或控制面板项目提供）。

- 创建您自己的程序来配置数据源。

配置数据源的程序对安装程序 DLL 进行函数调用。 安装程序 DLL 调用安装程序 DLL 来配置数据源。 每个驱动程序有一个设置 DLL;它可能是驱动程序 DLL 本身，或单独的 DLL。 安装程序 DLL 会提示用户获取驱动程序需要连接到数据源和默认转换器（如果受支持）的信息。 然后，它调用安装程序 DLL 和 Windows API 以在 ODBC 中记录此信息。INI 文件（或注册表）。

要显示用户可以用该对话框添加、修改和删除数据源，安装程序 DLL 中的程序调用`SQLManageDataSources`。 当从控制面板调用安装程序 DLL 时，将调用此功能。 要添加、修改或删除数据源，`SQLManageDataSources`请`ConfigDSN`调用与该数据源关联的驱动程序的安装程序 DLL。 要直接添加、修改或删除数据源，安装程序 DLL 中`SQLConfigDataSource`的程序调用。 程序传递数据源的名称和指定要执行的操作的选项。 `SQLConfigDataSource`在`ConfigDSN`设置 DLL 中调用，并从 传递参数`SQLConfigDataSource`。

有关详细信息，请参阅 ODBC SDK*程序员的参考、* 第 23 章、设置 DLL 函数参考和第 24 章安装程序 DLL 函数参考。

## <a name="see-also"></a>另请参阅

[技术说明（按编号）](../mfc/technical-notes-by-number.md)<br/>
[按类别分类的技术说明](../mfc/technical-notes-by-category.md)

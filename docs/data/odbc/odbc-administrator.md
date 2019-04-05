---
title: ODBC 管理器
ms.date: 11/04/2016
helpviewer_keywords:
- installing ODBC
- ODBC data sources [C++], ODBC Administrator
- ODBC drivers [C++], installing
- ODBC [C++], ODBC Administrator
- Administrator in ODBC
- administration ODBC Administrator
- ODBC Administrator [C++]
- drivers [C++], ODBC
ms.assetid: b8652790-3437-4e7d-bc83-6ea6981f008b
ms.openlocfilehash: ac893981ff8c697dc090f1e6ad5ac61886a69f99
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59035859"
---
# <a name="odbc-administrator"></a>ODBC 管理器

ODBC 管理器注册和配置[数据源](../../data/odbc/data-source-odbc.md)可供你在本地或网络中。 向导使用提供的 ODBC 管理器中的信息连接到数据源的用户在应用程序中创建的代码。

若要设置 ODBC 数据源与 MFC ODBC 类或 MFC 数据访问对象 (DAO) 类配合使用，必须先注册并配置数据源。 使用 ODBC 管理器添加和删除数据源。 具体取决于 ODBC 驱动程序，还可以创建新的数据源。

ODBC 管理器安装在安装过程中。 如果选择了**自定义**安装，但未选择任何中的 ODBC 驱动程序**数据库选项**对话框中，您需要运行安装程序以安装所需的文件。

安装过程中，选择你想要安装的 ODBC 驱动程序。 更高版本可以安装其他驱动程序随 Visual c + + 使用 Visual c + + 安装程序。

如果你想要使用 Visual c + + 安装的 ODBC 驱动程序不提供，必须运行安装程序附带驱动程序。

#### <a name="to-install-odbc-drivers-that-ship-with-visual-c"></a>若要使用 Visual c + + 安装附带的 ODBC 驱动程序

1. 从您的 Visual c + + 分发 CD 运行安装程序。

   打开安装程序中的对话框时，会显示。

1. 单击**下一步**上每个对话框中，直到达到**安装选项**对话框。 选择**自定义**，然后单击**下一步**。

1. 清除所有复选框**Microsoft Visual c + + 安装程序**除对话框**数据库选项**复选框，然后依次**详细信息**显示**数据库选项**对话框。

1. 清除**Microsoft 数据访问对象**复选框，选中**Microsoft ODBC 驱动程序**复选框，然后依次**详细信息**。

   **Microsoft ODBC 驱动程序**对话框随即出现。

1. 选择你想要安装，然后单击的驱动程序**确定**两次。

1. 单击**下一步**上其余对话框以开始安装。 安装完成后，安装程序将通知你。

当安装驱动程序时，可以配置使用 ODBC 管理器的数据源。 在控制面板中，您会发现的 ODBC 图标。

## <a name="see-also"></a>请参阅

[开放式数据库连接 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[数据源 (ODBC)](../../data/odbc/data-source-odbc.md)
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
ms.openlocfilehash: 9e88492919eac80a4f3db2f94202d49011aa69de
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213149"
---
# <a name="odbc-administrator"></a>ODBC 管理器

ODBC 管理器可在本地或跨网络注册和配置可用的[数据源](../../data/odbc/data-source-odbc.md)。 这些向导使用 ODBC 管理器提供的信息在将用户连接到数据源的应用程序中创建代码。

若要设置 ODBC 数据源以用于 MFC ODBC 类或 MFC 数据访问对象（DAO）类，必须先注册并配置数据源。 使用 ODBC 管理器添加和删除数据源。 根据 ODBC 驱动程序，您还可以创建新的数据源。

ODBC 管理器是在安装过程中安装的。 如果选择了 "**自定义**安装"，但未在 "**数据库选项**" 对话框中选择任何 ODBC 驱动程序，则需要重新运行安装程序以安装所需的文件。

在安装过程中，选择要安装的 ODBC 驱动程序。 稍后可使用视觉对象C++ C++安装程序安装随视觉对象一起提供的其他驱动程序。

如果要安装不随视觉对象C++一起提供的 ODBC 驱动程序，则必须运行驱动程序随附的安装程序。

#### <a name="to-install-odbc-drivers-that-ship-with-visual-c"></a>安装随视觉对象一起提供的 ODBC 驱动程序C++

1. 从你的可视C++分发 CD 运行安装程序。

   此时将显示安装程序中的 "打开" 对话框。

1. 在每个对话框上单击 "**下一步**"，直到出现 "**安装选项**" 对话框。 选择 "**自定义**"，然后单击 "**下一步**"。

1. 清除 " **Microsoft 视觉C++设置**" 对话框中除 "**数据库选项**" 复选框之外的所有复选框，然后单击 "**详细信息**" 以显示 "**数据库选项**" 对话框。

1. 清除 " **Microsoft 数据访问对象**" 复选框，选中 " **Microsoft ODBC 驱动程序**" 复选框，然后单击 "**详细信息**"。

   此时将显示 " **MICROSOFT ODBC 驱动程序**" 对话框。

1. 选择要安装的驱动程序，然后单击 **"确定"** 两次。

1. 在其余对话框中单击 "**下一步**" 以开始安装。 安装完成后，安装程序会通知你。

安装驱动程序后，可以使用 ODBC 管理器配置数据源。 你将在 "控制面板" 中找到 "ODBC" 图标。

## <a name="see-also"></a>另请参阅

[开放式数据库连接 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[数据源 (ODBC)](../../data/odbc/data-source-odbc.md)

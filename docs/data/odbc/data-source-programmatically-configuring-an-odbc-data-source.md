---
title: 数据源：以编程方式配置 ODBC 数据源
ms.date: 11/04/2016
f1_keywords:
- SQLConfigDataSource
helpviewer_keywords:
- ODBC data sources, configuring
- SQLConfigDataSource method example
- ODBC connections, configuring
- configuring ODBC data sources
ms.assetid: b8cabe9b-9e12-4d73-ae36-7cb12dee3213
ms.openlocfilehash: ba0224d166795b34d636ace610265e115209e49c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358861"
---
# <a name="data-source-programmatically-configuring-an-odbc-data-source"></a>数据源：以编程方式配置 ODBC 数据源

本主题介绍如何以编程方式配置开放数据库连接 （ODBC） 数据源名称。 这样，您可以灵活地访问数据，而无需强制用户显式使用 ODBC 管理员或其他程序来指定数据源的名称。

通常，如果关联的数据库管理系统 （DBMS） 支持此操作，则用户运行 ODBC 管理员以创建数据源。

通过 ODBC 管理员创建 Microsoft 访问 ODBC 数据源时，您有两种选择：您可以选择现有的 .mdb 文件，也可以创建新的 .mdb 文件。 没有从 MFC ODBC 应用程序创建 .mdb 文件的编程方法。 因此，如果应用程序要求将数据放入 Microsoft Access 数据源 （.mdb 文件），则很可能希望有一个空的 .mdb 文件，您可以随时使用或复制该文件。

但是，许多 DBMS 允许创建编程数据源。 某些数据源维护数据库的目录规范。 也就是说，目录是数据源，数据源中的每个表都存储在单独的文件中（在 dBASE 中，每个表都是 .dbf 文件）。 其他 ODBC 数据库（如 Microsoft Access 和 SQL Server）的驱动程序要求在建立数据源之前满足某些特定条件。 例如，使用 SQL Server ODBC 驱动程序时，需要建立 SQL Server 计算机。

## <a name="sqlconfigdatasource-example"></a><a name="_core_sqlconfigdatasource_example"></a>SQLConfigData源示例

以下示例使用`::SQLConfigDataSource`ODBC API 函数创建新的 Excel 数据源，称为新 Excel 数据源：

```
SQLConfigDataSource(NULL,ODBC_ADD_DSN, "Excel Files (*.xls)",
                   "DSN=New Excel Data Source\0"
                   "Description=New Excel Data Source\0"
                   "FileType=Excel\0"
                   "DataDirectory=C:\\EXCELDIR\0"
                   "MaxScanRows=20\0");
```

请注意，数据源实际上是一个目录 （C：_EXCELDIR）;此目录必须存在。 Excel 驱动程序使用目录作为其数据源，并将文件用作单个表（每个 .xls 文件一个表）。

有关创建表的详细信息，请参阅[数据源：在 ODBC 数据源中以编程方式创建表](../../data/odbc/data-source-programmatically-creating-a-table-in-an-odbc-data-source.md)。

以下信息讨论了需要传递给 ODBC API 函数的`::SQLConfigDataSource`参数。 要使用`::SQLConfigDataSource`，必须包括 Odbcinst.h 标头文件并使用 Odbcinst.lib 导入库。 此外，Odbccp32.dll 必须在运行时的路径中（或 Odbcinst.dll 为 16 位）。

您可以使用 ODBC 管理员或类似实用程序创建 ODBC 数据源名称。 但是，有时最好直接从应用程序创建数据源名称以获取访问权限，而无需用户运行单独的实用程序。

ODBC 管理员（通常安装在控制面板中）通过将条目放入 Windows 注册表（或对于 16 位）中的 Odbc.ini 文件中来创建新的数据源。 ODBC 驱动程序管理器查询此文件以获取有关数据源所需的信息。 请务必了解需要将哪些信息放置在注册表中，因为您需要向 它提供调用`::SQLConfigDataSource`。

尽管此信息可以直接写入注册表而不使用`::SQLConfigDataSource`，但这样做的任何应用程序都依赖于驱动程序管理器用于维护其数据的当前技术。 如果更高版本的 ODBC 驱动程序管理器以不同的方式实现有关数据源的记录保存，则使用此技术的任何应用程序都将中断。 通常建议在提供 API 函数时使用 API 函数。 例如，如果使用`::SQLConfigDataSource`函数，代码从 16 位可移植到 32 位，因为函数正确写入 Odbc.ini 文件或注册表。

## <a name="sqlconfigdatasource-parameters"></a><a name="_core_sqlconfigdatasource_parameters"></a>SQLConfigData源参数

下面介绍了`::SQLConfigDataSource`函数的参数。 大部分信息来自 VisualC++ 版本 1.5 及更高版本中提供的 ODBC API*程序员参考*。

### <a name="function-prototype"></a><a name="_core_function_prototype"></a>功能原型

```
BOOL SQLConfigDataSource(HWND hwndParent,UINT fRequest, LPCSTR lpszDriver, LPCSTR lpszAttributes);
```

### <a name="remarks"></a>备注

#### <a name="parameters-and-usage"></a><a name="_core_parameters_and_usage"></a>参数和用法

*hwnd 家长*<br/>
指定为 ODBC 驱动程序管理器或特定 ODBC 驱动程序创建的任何对话框的所有者的窗口，以便从用户处获取有关新数据源的其他信息。 如果*lpszAttributes*参数未提供足够的信息，则会出现一个对话框。 *hwnd 父参数*可能为 NULL。

*lpszDriver*<br/>
驱动程序说明。 这是向用户显示的名称，而不是物理驱动程序名称 （DLL）。

*lpsz属性*<br/>
窗体中的属性列表"keyname_value"。 这些字符串由空终止符分隔，在列表末尾有两个连续的空终止符。 这些属性主要是默认的特定于驱动程序的条目，这些条目进入新数据源的注册表。 此函数的 ODBC API 引用中未提及的一个重要键是"DSN"（"数据源名称"），它指定新数据源的名称。 其余条目特定于新数据源的驱动程序。 通常不需要提供所有条目，因为驱动程序可以提示用户为新值的对话框。 （将 *"父级设置为 NULL"* 会导致这种情况。您可能希望显式提供默认值，以便不会提示用户。

#### <a name="to-determine-the-description-of-a-driver-for-the-lpszdriver-parameter-using-odbc-administrator"></a>使用 ODBC 管理员确定 lpszDriver 参数的驱动程序描述

1. 运行 ODBC 管理员。

1. 单击 **添加**。

这为您提供了已安装驱动程序的列表及其说明。 使用此说明作为*lpszDriver*参数。 请注意，您可以使用整个说明，例如"Excel 文件 （*.xls）"），包括文件名扩展名和括号（如果它们存在于说明中）。

作为替代方法，您可以检查注册表（或，对于 16 位，文件 Odbcinst.ini），其中包含注册表键"ODBC 驱动程序"（或 Odbcinst.ini 中的部分 [ODBC 驱动程序]下的所有驱动程序条目和说明的列表）。

查找*lpszAttributes*参数的键名和值的一种方法是检查已配置的数据源（可能是由 ODBC 管理员配置的数据源）的 Odbc.ini 文件。

#### <a name="to-find-keynames-and-values-for-the-lpszattributes-parameter"></a>查找 lpszAttributes 参数的键名和值

1. 运行 Windows 注册表编辑器（或者，对于 16 位，打开 Odbc.ini 文件）。

1. 使用以下之一查找 ODBC 数据源信息：

   - 对于 32 位，找到**HKEY_CURRENT_USER\软件_ODBC_ODBC 的关键。左侧窗格中的 INI_ODBC 数据源**。

      右侧窗格列出了窗体的条目："pub：REG_SZ：*\<数据源名称>"，* 其中*\<数据源名称>* 已配置了要使用的驱动程序所需的设置。 选择所需的数据源，例如 SQL Server。 字符串"pub："之后的项按顺序排列，是要在*lpszAttributes*参数中使用的键名和值。

   - 对于 16 位，在 Odbc.ini 文件中找到该部分，该文件由 [*\<数据源名称>*] 标记。

      此行的行是"keyname_value"窗体。 这些正是要在*lpszAttributes*参数中使用的条目。

您可能还需要检查要使用的特定驱动程序的文档。 您可以在驱动程序的在线帮助中找到有用的信息，您可以通过运行 ODBC 管理员来访问这些信息。 这些帮助文件通常放置在 Windows NT、Windows 3.1 或 Windows 95 的 WINDOWS_SYSTEM 目录中。

#### <a name="to-obtain-online-help-for-your-odbc-driver"></a>获取 ODBC 驱动程序的在线帮助

1. 运行 ODBC 管理员。

1. 单击 **添加**。

1. 选择驱动程序名称。

1. 单击“确定”。 

当 ODBC 管理员显示为该特定驱动程序创建新数据源的信息时，单击"**帮助**"。 这将打开该特定驱动程序的帮助文件，该文件通常包含有关驱动程序使用的重要信息。

## <a name="see-also"></a>另请参阅

[数据源 (ODBC)](../../data/odbc/data-source-odbc.md)

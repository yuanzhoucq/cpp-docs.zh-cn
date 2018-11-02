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
ms.openlocfilehash: 3d02a19d6c61e79fffd31b67ef1b8f7ea9007fcb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50677365"
---
# <a name="data-source-programmatically-configuring-an-odbc-data-source"></a>数据源：以编程方式配置 ODBC 数据源

本主题说明如何以编程方式配置开放式数据库连接 (ODBC) 数据源名称。 这使您灵活访问数据而不会迫使用户显式使用 ODBC 管理器或其他程序来指定数据源的名称。

通常情况下，用户运行 ODBC 管理器来创建数据源，如果关联的数据库管理系统 (DBMS) 支持此操作。

在创建 Microsoft Access ODBC 数据源用 ODBC 管理器时，系统会提供两种选择： 可以选择现有的.mdb 文件，也可以创建一个新的.mdb 文件。 没有从 MFC ODBC 应用程序创建.mdb 文件的编程方法。 因此，如果应用程序需要将数据放到 Microsoft Access 数据源 （.mdb 文件），您很可能想要有一个空的.mdb 文件，可以使用或复制时需要它。

但是，许多 Dbms 允许以编程方式的数据源创建。 某些数据源维护数据库的目录规范。 也就是说，目录是数据源和数据源中的每个表都存储在单独的文件 （对于 dBASE，每个表都是一个.dbf 文件）。 对于其他 ODBC 数据库，如 Microsoft Access 和 SQL Server 驱动程序需要可以建立数据源之前满足某些特定条件。 例如，当使用 SQL Server ODBC 驱动程序，需要建立 SQL Server 计算机。

##  <a name="_core_sqlconfigdatasource_example"></a> SQLConfigDataSource 实例

下面的示例使用`::SQLConfigDataSource`调用 ODBC API 函数来创建新的 Excel 数据源的新的 Excel 数据源：

```
SQLConfigDataSource(NULL,ODBC_ADD_DSN, "Excel Files (*.xls)",
                   "DSN=New Excel Data Source\0"
                   "Description=New Excel Data Source\0"
                   "FileType=Excel\0"
                   "DataDirectory=C:\\EXCELDIR\0"
                   "MaxScanRows=20\0");
```

请注意，数据源实际上是一个目录 (C:\EXCELDIR);此目录必须存在。 Excel 驱动程序使用目录作为其数据源和文件作为单独的表 （一个表就是一个.xls 文件）。

有关创建表的详细信息，请参阅[数据源： 以编程方式创建 ODBC 数据源中的表](../../data/odbc/data-source-programmatically-creating-a-table-in-an-odbc-data-source.md)。

下面的内容讨论需要传递给参数`::SQLConfigDataSource`ODBC API 函数。 若要使用`::SQLConfigDataSource`，必须包括 Odbcinst.h 头文件，并使用 Odbcinst.lib 导入库。 另外，Odbccp32.dll 必须在路径中在运行的时 （或对于 16 位系统）。

可以创建 ODBC 数据源名称使用 ODBC 管理器或类似的实用工具。 但是，有时最好直接从应用程序以获取访问权限，而无需用户运行单独的实用程序创建数据源名称。

ODBC 管理器 （通常在控制面板中安装） 通过将条目放在 Windows 注册表中 （或者对于 16 位中的 Odbc.ini 文件） 创建新的数据源。 ODBC 驱动程序管理器将查询此文件以获取有关数据源所需的信息。 务必要知道哪些信息需要放在注册表中，因为你需要提供给该对的调用`::SQLConfigDataSource`。

尽管此信息无法直接写入注册表而无需使用`::SQLConfigDataSource`，这样做的任何应用程序依赖于当前驱动程序管理器使用来维护其数据的技术。 如果以不同方式维护有关数据源的 ODBC 驱动程序管理器实现记录到更高版本的修订版本，则任何使用此技术应用程序将断开。 通常，最好在提供使用 API 函数。 例如，你的代码是从 16 位到 32 位可移植的如果您使用`::SQLConfigDataSource`函数，因为该函数可以正确地写入 Odbc.ini 文件或注册表。

##  <a name="_core_sqlconfigdatasource_parameters"></a> SQLConfigDataSource 参数

以下说明了这些参数的`::SQLConfigDataSource`函数。 从 ODBC API 的大部分信息获取*程序员参考*提供使用 Visual c + + 1.5 和更高版本。

###  <a name="_core_function_prototype"></a> 函数原型

```
BOOL SQLConfigDataSource(HWND hwndParent,UINT fRequest, LPCSTR lpszDriver, LPCSTR lpszAttributes);
```

### <a name="remarks"></a>备注

####  <a name="_core_parameters_and_usage"></a> 参数和使用情况

*hwndParent*<br/>
指定为所有者的任何 ODBC 驱动程序管理器或特定 ODBC 驱动程序创建要从新的数据源的相关用户获得其他信息的对话框窗口。 如果*lpszAttributes*参数没有提供足够的信息，会出现一个对话框。 *HwndParent*参数可能为 NULL。

*lpszDriver*<br/>
驱动程序的描述。 这是显示给用户而不是物理驱动器的名称 (DLL) 的名称。

*lpszAttributes*<br/>
在窗体中的属性列表"键名 = 值"。 由两个连续的 null 结束符列表的末尾与 null 终止符分隔这些字符串。 这些属性是主要是特定于驱动程序中的默认项进入新的数据源的注册表。 此函数的 ODBC API 参考中未提到的一个重要的项是"DSN"（"数据源名称"），它指定新的数据源的名称。 其他项是特定于新数据源的驱动程序。 通常不需要提供的所有条目，因为驱动程序可以提示用户用新值的对话框。 (设置*hwndParent*到 NULL 可导致此问题。)你可能想要显式提供默认值，以便不提示用户。

#### <a name="to-determine-the-description-of-a-driver-for-the-lpszdriver-parameter-using-odbc-administrator"></a>若要确定 lpszDriver 参数使用 ODBC 管理器的驱动程序的说明

1. 运行 ODBC 管理器。

1. 单击 **添加**。

这样，您安装的驱动程序和及其说明的列表。 将此说明作为*lpszDriver*参数。 请注意使用整个说明，如"Excel 文件 (*.xls)"，如果它们存在于说明包括文件扩展名和括号。

或者，你可以检查注册表 （或者对于 16 位，Odbcinst.ini 文件），其中包含所有驱动程序项和注册表项"ODBC 驱动程序"下的说明 （或在 Odbcinst.ini 的 [ODBC Drivers] 部分） 的列表。

查找的键名和值的一种方法*lpszAttributes*参数是一个已配置的数据源 （可能是一个已配置由 ODBC 管理器） 的 Odbc.ini 文件。

#### <a name="to-find-keynames-and-values-for-the-lpszattributes-parameter"></a>若要查找 lpszAttributes 参数的键名及值

1. 运行 Windows 注册表编辑器 （或者，对于 16 位，打开 Odbc.ini 文件）。

1. 查找 ODBC 数据源信息使用以下项之一：

   - 适用于 32 位，找不到该项**HKEY_CURRENT_USER\Software\ODBC\ODBC。INI\ODBC 数据源**的左窗格中。

      右窗格中列出了项的窗体:"pub: REG_SZ:*<data source name>*"，其中*<data source name>* 是已与你想的驱动程序所需的设置配置的数据源若要使用。 选择所需的数据源，如 SQL Server。 字符串后面的项"pub:"是，在顺序中，键名和值要在中使用你*lpszAttributes*参数。

   - 对于 16 位，由标记 Odbc.ini 文件中找到的部分 [*\<数据源名称 >*]。

      该行之后的行是窗体的"键名 = 值"。 这些是完全使用中的条目你*lpszAttributes*参数。

您可能想要检查要使用的特定驱动程序的文档。 可以驱动程序可以通过运行 ODBC 管理器访问联机帮助中找到有用的信息。 这些帮助文件通常位于 WINDOWS\SYSTEM 目录中的 Windows NT、 Windows 3.1 或 Windows 95。

#### <a name="to-obtain-online-help-for-your-odbc-driver"></a>若要获取 ODBC 驱动程序的联机帮助

1. 运行 ODBC 管理器。

1. 单击 **添加**。

1. 选择驱动程序名称。

1. 单击 **“确定”**。

当 ODBC 管理器显示用于创建该特定驱动程序的新数据源的信息时，请单击**帮助**。 这将打开该特定驱动程序，其中通常包含有关该驱动程序使用的重要信息的帮助文件。

## <a name="see-also"></a>请参阅

[数据源 (ODBC)](../../data/odbc/data-source-odbc.md)

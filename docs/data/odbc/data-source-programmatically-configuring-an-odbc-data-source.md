---
title: "数据源： 以编程方式配置 ODBC 数据源 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SQLConfigDataSource
dev_langs: C++
helpviewer_keywords:
- ODBC data sources, configuring
- SQLConfigDataSource method example
- ODBC connections, configuring
- configuring ODBC data sources
ms.assetid: b8cabe9b-9e12-4d73-ae36-7cb12dee3213
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ac5756452a8b1c2d5dbf2f27ac7d3e1a8b069ca2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="data-source-programmatically-configuring-an-odbc-data-source"></a>数据源：以编程方式配置 ODBC 数据源
本主题说明如何以编程方式配置开放式数据库连接 (ODBC) 数据源名称。 这可以灵活地访问数据而不强制用户显式使用 ODBC 管理器或其他程序以指定数据源的名称。  
  
 通常情况下，用户运行 ODBC 管理器可以创建数据源，如果关联的数据库管理系统 (DBMS) 支持此操作。  
  
 在创建时 Microsoft 访问 ODBC 数据源通过 ODBC 管理器中，您有两个选项： 您可以选择现有的.mdb 文件，或者可以创建新的.mdb 文件。 没有从 MFC ODBC 应用程序创建的.mdb 文件的编程方法。 因此，如果你的应用程序要求您将数据放置到 Microsoft Access 数据源 （.mdb 文件），你最有可能想要具有空的.mdb 文件，你可以使用或在需要时复制。  
  
 但是，许多 Dbms 允许以编程方式的数据源创建。 某些数据源保持数据库的目录规范。 也就是说，目录是数据源，数据源中的每个表都存储在单独的文件 （对于 dBASE，每个表都是一个.dbf 文件）。 对于其他 ODBC 数据库，如 Microsoft Access 和 SQL Server 驱动程序都需要在建立数据源之前满足某些特定条件。 例如，在使用 SQL Server ODBC 驱动程序时，你需要建立了 SQL Server 计算机。  
  
##  <a name="_core_sqlconfigdatasource_example"></a>SQLConfigDataSource 示例  
 下面的示例使用**:: SQLConfigDataSource**调用 ODBC API 函数来创建新的 Excel 数据源的新的 Excel 数据源：  
  
```  
SQLConfigDataSource(NULL,ODBC_ADD_DSN, "Excel Files (*.xls)",   
                   "DSN=New Excel Data Source\0"   
                   "Description=New Excel Data Source\0"   
                   "FileType=Excel\0"   
                   "DataDirectory=C:\\EXCELDIR\0"   
                   "MaxScanRows=20\0");  
```  
  
 请注意，数据源是实际的目录 (C:\EXCELDIR);此目录必须存在。 作为单独的表 （一个表中每个.xls 文件） 还原时，Excel 驱动程序使用作为其数据源和文件的目录。  
  
 有关创建表的详细信息，请参阅[数据源： 以编程方式创建 ODBC 数据源中的表](../../data/odbc/data-source-programmatically-creating-a-table-in-an-odbc-data-source.md)。  
  
 以下信息讨论如何将传递给所需要的参数**:: SQLConfigDataSource** ODBC API 函数。 若要使用**:: SQLConfigDataSource**，你必须包括 Odbcinst.h 标头文件，并使用 Odbcinst.lib 导入库。 此外，在路径中必须在 Odbccp32.dll，在运行的时 （或 Odbcinst.dll 16 位）。  
  
 你可以创建 ODBC 数据源名称使用 ODBC 管理器或类似的实用工具。 但是，有时最好直接从你的应用程序，以获取访问权限，而无需用户运行单独的实用程序创建数据源名称。  
  
 ODBC 管理器 （通常在控制面板中安装） 通过将项放在 Windows 注册表中 （或者，为 Odbc.ini 文件中的 16 位） 创建一个新的数据源。 ODBC 驱动程序管理器查询此文件以获取有关数据源所需的信息。 务必要知道哪些信息需要放置在注册表中，因为你需要提供对的调用**:: SQLConfigDataSource**。  
  
 尽管此信息无法将直接写入到注册表而无需使用**:: SQLConfigDataSource**，这样做的任何应用程序依赖于驱动程序管理器使用来维护其数据的当前技术。 如果以不同的方式维护有关数据源的 ODBC 驱动程序管理器实现记录到更高版本的修订版本，任何应用程序使用此方法将断开。 通常，最好是在其中一个提供时使用 API 函数。 例如，你的代码是在 16 位为 32 位可移植性的如果你使用**:: SQLConfigDataSource**函数，因为该函数正确将写入 Odbc.ini 文件或注册表。  
  
##  <a name="_core_sqlconfigdatasource_parameters"></a>SQLConfigDataSource 参数  
 以下说明了这些参数的**:: SQLConfigDataSource**函数。 很多信息则来自 ODBC API*程序员参考*提供使用 Visual c + + 版本 1.5 和更高版本。  
  
###  <a name="_core_function_prototype"></a>函数原型  
  
```  
BOOL SQLConfigDataSource(HWND hwndParent,UINT fRequest, LPCSTR lpszDriver, LPCSTR lpszAttributes);  
```  
  
### <a name="remarks"></a>备注  
  
####  <a name="_core_parameters_and_usage"></a>参数和使用情况  
 *hwndParent*  
 指定为任何 ODBC 驱动程序管理器或特定 ODBC 驱动程序创建以获得有关新的数据源的用户的其他信息的对话框的所有者窗口。 如果`lpszAttributes`参数不会提供足够的信息，将出现一个对话框。 *HwndParent*参数可能是**NULL**。  
  
 `lpszDriver`  
 驱动程序说明中。 这是显示给用户，而不是物理驱动器的名称 (DLL) 的名称。  
  
 `lpszAttributes`  
 窗体中的属性列表"keyname = value"。 这些字符串用在列表末尾的两个连续 null 终止符与 null 终止符分隔。 这些特性是主要是特定于驱动程序中的默认项进入新的数据源的注册表。 此函数的 ODBC API 参考中未提及的一个重要的项是"DSN"（"数据源名称"），它指定新的数据源的名称。 项的其余部分是特定于新数据源的驱动程序。 通常不需要提供的所有条目，因为该驱动程序可以提示用户提供的新值的对话框。 (设置*hwndParent*到**NULL**以导致此问题。)你可能想要显式提供默认值，以便不会提示用户。  
  
###### <a name="to-determine-the-description-of-a-driver-for-the-lpszdriver-parameter-using-odbc-administrator"></a>若要确定用于使用 ODBC 管理器的 lpszDriver 参数的驱动程序的说明  
  
1.  运行 ODBC 管理器。  
  
2.  单击 **“添加”**。  
  
 这样，可以安装的驱动程序和及其说明的列表。 将此说明作为`lpszDriver`参数。 请注意，你将使用整个说明，如"Excel 文件 (*.xls)"，如果它们存在描述中包括的文件扩展名和括号。  
  
 作为替代方法，你可以检查注册表 （或者，为 16 位，文件 Odbcinst.ini），其中包含的所有驱动程序项和注册表项"ODBC 驱动程序"下的说明 （或 Odbcinst.ini 中的部分 [ODBC 驱动程序]） 的列表。  
  
 查找的键名和值的一种方法`lpszAttributes`参数是 （可能是一个已配置由 ODBC 管理器） 已配置的数据源的 Odbc.ini 文件。  
  
###### <a name="to-find-keynames-and-values-for-the-lpszattributes-parameter"></a>若要查找 lpszAttributes 参数的键名和值  
  
1.  运行 Windows 注册表编辑器 （或对于 16 位，打开 Odbc.ini 文件）。  
  
2.  查找使用下列其中一项的 ODBC 数据源信息：  
  
    -   32 位，找不到该项**HKEY_CURRENT_USER\Software\ODBC\ODBC。INI\ODBC 数据源**的左窗格中。  
  
         右窗格中列出的窗体的项:"pub: REG_SZ:*<data source name>*"，其中 *<data source name>* 是已配置了你想驱动程序所需的设置的数据源若要使用。 选择数据源所需，例如，SQL Server。 以下字符串的项"发布:"中，在顺序、 keyname 和值要在中使用你`lpszAttributes`参数。  
  
    -   16 位，在标记的 Odbc.ini 文件中找到的部分 [*\<数据源名称 >*]。  
  
         该行之后的行是窗体的"keyname = value"。 这些是完全的条目用于你`lpszAttributes`参数。  
  
 你可能还想要检查你要使用的特定驱动程序的文档。 可以驱动程序，你可以通过运行 ODBC 管理器访问联机帮助中找到有用的信息。 这些帮助文件通常位于 WINDOWS\SYSTEM 目录中的 Windows NT、 Windows 3.1 中或 Windows 95。  
  
###### <a name="to-obtain-online-help-for-your-odbc-driver"></a>若要获取联机帮助的 ODBC 驱动程序  
  
1.  运行 ODBC 管理器。  
  
2.  单击 **“添加”**。  
  
3.  选择的驱动程序名称。  
  
4.  单击 **“确定”**。  
  
 ODBC 管理器在显示时用于创建该特定的驱动程序的新数据源的信息，请单击**帮助**。 这将打开该特定的驱动程序，其中通常包含有关使用驱动程序的重要信息的帮助文件。  
  
## <a name="see-also"></a>请参阅  
 [数据源 (ODBC)](../../data/odbc/data-source-odbc.md)
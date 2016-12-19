---
title: "数据源：以编程方式配置 ODBC 数据源 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SQLConfigDataSource"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "配置 ODBC 数据源"
  - "ODBC 连接, 配置"
  - "ODBC 数据源, 配置"
  - "SQLConfigDataSource 方法示例"
ms.assetid: b8cabe9b-9e12-4d73-ae36-7cb12dee3213
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 数据源：以编程方式配置 ODBC 数据源
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主题说明如何用编程方式配置开放式数据库连接 \(ODBC\) 数据源名称。  这增加了访问数据的灵活性，不必强制用户显式地使用 ODBC 管理器或其他程序来指定数据源名称。  
  
 通常，如果关联的数据库管理系统 \(DBMS\) 支持用 ODBC 管理器来创建数据源，则用户运行 ODBC 管理器来创建数据源。  
  
 用 ODBC 管理器创建 Microsoft Access ODBC 数据源时，有两个选择：可以选择现有的 .mdb 文件，或者创建新的 .mdb 文件。  没有从 MFC ODBC 应用程序创建 .mdb 文件的编程方式。  因此，如果您的应用程序要求将数据放到 Microsoft Access 数据源（.mdb 文件）中，最可行的办法是有一个空的 .mdb 文件，需要时可以使用或复制它。  
  
 但是，许多 DBMS 允许以编程的方式创建数据源。  一些数据源维护数据库的目录规范。  也就是说，目录是一个数据源，数据源中的每个表都存储在单独的文件中（对于 dBASE，每个表都是一个 .dbf 文件）。  其他 ODBC 数据库的驱动程序，如 Microsoft Access 和 SQL Server，要求在满足一些特定的条件之后才能建立数据源。  例如，使用 SQL Server ODBC 驱动程序时，需要建立了一台 SQL Server 计算机。  
  
##  <a name="_core_sqlconfigdatasource_example"></a> SQLConfigDataSource 实例  
 下面的示例用 **::SQLConfigDataSource** ODBC API 函数创建一个新的称为“New Excel Data Source”的 Excel 数据源：  
  
```  
SQLConfigDataSource(NULL,ODBC_ADD_DSN, "Excel Files (*.xls)",   
                   "DSN=New Excel Data Source\0"   
                   "Description=New Excel Data Source\0"   
                   "FileType=Excel\0"   
                   "DataDirectory=C:\\EXCELDIR\0"   
                   "MaxScanRows=20\0");  
```  
  
 注意，数据源实际上是一个目录 \(C:\\EXCELDIR\)，这个目录必须存在。  Excel 驱动程序使用目录作为其数据源，使用文件作为单独的表（一个表就是一个 .xls 文件）。  
  
 有关创建表的更多信息，请参见 [数据源：以编程方式在 ODBC 数据源中创建表](../../data/odbc/data-source-programmatically-creating-a-table-in-an-odbc-data-source.md)。  
  
 下面的内容讨论需要传递给 **::SQLConfigDataSource** ODBC API 函数的参数。  若要使用 **::SQLConfigDataSource**，必须包括 Odbcinst.h 头文件并使用 Odbcinst.lib 导入库。  另外，Odbccp32.dll（对于 16 位系统为 Odbcinst.dll）必须在运行时路径中。  
  
 您可以使用 ODBC 管理器或类似的实用程序来创建 ODBC 数据源名称。  但是，有时从应用程序直接创建数据源名称获得访问权，而不需要用户运行单独的实用程序的做法更可取。  
  
 ODBC 管理器（通常安装在“控制面板”中）将一些项放在 Windows 注册表（对于 16 位系统，放在 Odbc.ini 文件）中，从而新建数据源。  ODBC 驱动程序管理器将查询这个文件，以获得有关数据源的所需信息。  了解哪些信息要放在注册表中很重要，因为您需要通过调用 **::SQLConfigDataSource** 来提供这些信息。  
  
 尽管不用 **::SQLConfigDataSource** 也可以将这些信息直接写到注册表，但是任何这样做的应用程序都依赖于驱动程序管理器当前用来维护其数据的技术。  如果 ODBC 驱动程序管理器以后的修订版使用不同的方法来维护有关数据源的记录，使用这项技术的所有应用程序都将会出现问题。  通常建议您在提供了 API 函数的情况下使用 API 函数。  例如，如果使用 **::SQLConfigDataSource** 函数，可以将代码从 16 位系统移植到 32 位系统，因为该函数可以正确地写入 Odbc.ini 文件或注册表。  
  
##  <a name="_core_sqlconfigdatasource_parameters"></a> SQLConfigDataSource 参数  
 下面解释 **::SQLConfigDataSource** 函数的参数。  其中大部分内容摘自随 Visual C\+\+ 1.5 版本和更高版本一同提供的“ODBC API 程序员参考”。  
  
###  <a name="_core_function_prototype"></a> 函数原型  
  
```  
BOOL SQLConfigDataSource(HWND hwndParent,UINT fRequest, LPCSTR lpszDriver, LPCSTR lpszAttributes);  
```  
  
### 备注  
  
####  <a name="_core_parameters_and_usage"></a> 参数及其用法  
 *hwndParent*  
 指定为任何对话框的所有者的窗口。ODBC 驱动程序管理器或者特定 ODBC 驱动程序将创建这些对话框以从用户处获得有关新数据源的附加信息。  如果 `lpszAttributes` 参数没有提供足够的信息，则显示一个对话框。  *hwndParent* 参数可以为 **NULL**。  
  
 `lpszDriver`  
 驱动程序的描述。  这是显示给用户的名称，不是物理驱动器的名称 \(DLL\)。  
  
 `lpszAttributes`  
 格式为“键名＝值”的特性列表。  这些字符串用 Null 结束符分开，列表结尾有 2 个连续的 Null 结束符。  这些特性主要是要为新数据源填入到注册表中的默认驱动程序特定项。  ODBC API 参考中有关该函数没有提到的重要的一项是指定新数据源名称的“DSN”（“数据源名称”）。  其他项都是针对新数据源驱动程序的。  因为驱动程序会用对话框提示用户提供新值，所以通常没有必要提供所有的项。（将 *hwndParent* 设置成 **NULL** 将导致这种情况。）您也可以显式地提供默认值以便不提示用户进行输入。  
  
###### 使用 ODBC 管理器确定 lpszDriver 参数的驱动程序说明  
  
1.  运行 ODBC 管理器。  
  
2.  单击**“添加”**。  
  
 这会提供已安装的驱动程序及其说明的列表。  将此说明作为 `lpszDriver` 参数使用。  请注意，应使用整个说明，包括说明中的文件扩展名和括号（如果有），如“Excel Files \(\*.xls\)”。  
  
 另一种方法是检查注册表（对于 16 位系统，为 Odbcinst.ini 文件），在注册表项“ODBC Drivers”（或在 Odbcinst.ini 的 \[ODBC Drivers\] 节）下有一个所有驱动程序项和说明的列表。  
  
 一种查找 `lpszAttributes` 参数的键名和值的方法是：查看已配置的数据源（多半是由 ODBC 管理器配置的数据源）的 Odbc.ini 文件。  
  
###### 查找 lpszAttributes 参数的键名及值  
  
1.  运行 Windows 注册表编辑器（或者对于 16 位系统，打开 Odbc.ini 文件）。  
  
2.  使用以下方法之一查找 ODBC 数据源的信息：  
  
    -   对于 32 位系统，在左窗格中查找键 **HKEY\_CURRENT\_USER\\Software\\ODBC\\ODBC.INI\\ODBC Data Sources**。  
  
         右边窗格列出了窗体实体：“pub: REG\_SZ:*\<数据源名称\>*”，这里*\<数据源名称\>*是已用您要使用的驱动程序所需设置配置好的数据源。  选择要用的数据源，例如 SQL Server。  字符串“pub:”后的项依次为在 `lpszAttributes` 参数中要使用的键名和值。  
  
    -   对于 16 位系统，在 Odbc.ini 文件中查找带 \[*\<数据源名称\>*\] 标记的节。  
  
         该行之后的各行的格式为“键名\=值”。  这些正是在 `lpszAttributes` 参数中要用的项。  
  
 您也许想查看要使用的特定驱动程序的文档。  可以在驱动程序的联机帮助中找到有用的信息。运行 ODBC 管理器可访问驱动程序的联机帮助。  在 Windows NT、Windows 3.1 或 Windows 95 上，这些帮助文件通常位于 WINDOWS\\SYSTEM 目录下。  
  
###### 获得 ODBC 驱动程序的联机帮助  
  
1.  运行 ODBC 管理器。  
  
2.  单击**“添加”**。  
  
3.  选择驱动程序名称。  
  
4.  单击**“确定”**。  
  
 在 ODBC 管理器显示为该特定驱动程序创建新数据源的信息时，单击“帮助”。  这就打开了该特定驱动程序的帮助文件，该帮助文件一般包含有关使用驱动程序的重要信息。  
  
## 请参阅  
 [数据源 \(ODBC\)](../../data/odbc/data-source-odbc.md)
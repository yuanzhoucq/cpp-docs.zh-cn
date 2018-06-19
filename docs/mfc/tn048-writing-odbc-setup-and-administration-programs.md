---
title: TN048： 为 MFC 数据库应用程序编写 ODBC 安装和管理程序 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.odbc
dev_langs:
- C++
helpviewer_keywords:
- installing ODBC
- ODBC, installing
- setup, ODBC setup programs
- TN048
- ODBC, and MFC
- MFC, database applications
ms.assetid: d456cdd4-0513-4a51-80c0-9132b66115ce
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2c08366f995c1ecb4182fff04a88ac37fe7334bc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33384259"
---
# <a name="tn048-writing-odbc-setup-and-administration-programs-for-mfc-database-applications"></a>TN048：为 MFC 数据库应用程序编写 ODBC 安装和管理程序
> [!NOTE]
>  以下技术说明在首次包括在联机文档中后未更新。 因此，某些过程和主题可能已过时或不正确。 要获得最新信息，建议你在联机文档索引中搜索热点话题。  
  
 使用 MFC 数据库类应用程序将需要安装 ODBC 组件的安装程序。 它们可能还需要将检索有关可用的驱动程序，来指定默认驱动程序以及配置数据源信息的 ODBC 管理程序。 本说明介绍 ODBC 安装程序 api 来编写这些程序使用。  
  
##  <a name="_mfcnotes_writing_an_odbc_setup_program"></a> 编写 ODBC 安装程序  
 MFC 数据库应用程序需要 ODBC 驱动程序管理器 (ODBC。DLL) 和 ODBC 驱动程序要能够获取对数据源。 许多 ODBC 驱动程序还需要其他网络和通信 Dll。 大多数 ODBC 驱动程序附带将安装所需的 ODBC 组件的安装程序。 使用 MFC 数据库类应用程序开发人员可以：  
  
-   依赖于安装 ODBC 组件的特定于驱动程序的安装程序。 这将不再需要开发人员部分工作 — 你只需重新分发的驱动程序的安装程序。  
  
-   此外，你可以编写你自己的安装程序，这将在安装驱动程序管理器和驱动程序。  
  
 ODBC 安装程序 API 用于编写特定于应用程序的安装程序。 在安装程序 API 函数的实现是由 ODBC 安装程序 DLL-ODBCINST。在 16 位 Windows 和 ODBCCP32 上的 DLL。在 Win32 DLL。 应用程序可以调用**SQLInstallODBC**在安装程序 DLL，将安装 ODBC 驱动程序管理器、 ODBC 驱动程序，以及任何所需的转换器。 它然后 ODBCINST 中记录的已安装的驱动程序和翻译。INI 文件 （或 NT 上的注册表，）。 **SQLInstallODBC**需要 ODBC 的完整路径。INF 文件，其中包含要安装的驱动程序列表，并介绍构成每个驱动程序的文件。 它还包含有关驱动程序管理器和翻译的类似信息。 ODBC。通常由驱动程序开发人员提供 INF 文件。  
  
 程序还可以安装单个 ODBC 组件。 若要安装驱动程序管理器，程序首先调用**SQLInstallDriverManager**在安装程序以获取有关驱动程序管理器的目标目录的 DLL。 这通常是 Windows Dll 驻留在其中的目录。 程序然后使用 ODBC 的 [ODBC 驱动程序管理器] 部分中的信息。要将驱动程序管理器和相关的文件从安装光盘复制到此目录的 INF 文件。 若要安装各个驱动程序，程序首先调用**SQLInstallDriver**在安装程序将添加到 ODBCINST 驱动程序规范的 DLL。INI 文件 （或 NT 上的注册表，）。 **SQLInstallDriver**返回驱动程序的目标目录-通常 Windows Dll 驻留在其中的目录。 程序然后使用 ODBC 驱动程序的部分中的信息。要将驱动程序 DLL 和相关的文件从安装光盘复制到此目录的 INF 文件。  
  
 有关 ODBC 的详细信息。INF、 ODBCINST。INI 和使用安装程序 API，请参阅 ODBC SDK*程序员参考*第 19 章、 安装的 ODBC 软件。  
  
##  <a name="_mfcnotes_writing_an_odbc_administrator"></a> 编写 ODBC 管理器  
 MFC 数据库应用程序可以设置，并采用两种方式之一配置 ODBC 数据源，如下所示：  
  
-   使用 ODBC 管理器 （作为程序或作为控制面板项可用）。  
  
-   创建你自己的程序，若要配置数据源。  
  
 配置数据源的程序进行函数调用给安装程序 DLL。 安装程序 DLL 调用安装程序配置数据源的 DLL。 没有为每个驱动程序; 的一个安装程序 DLL它可能是驱动程序 DLL 本身或单独的 DLL。 安装程序 DLL 将提示用户输入该驱动程序必须连接到数据源和默认值转换器，如果受支持的信息。 然后，它调用了安装，DLL 和 Windows Api 在 ODBC 中记录此信息。INI 文件 （或注册表）。  
  
 若要显示一个对话框，可与该用户可以添加、 修改和删除数据源，程序将调用**SQLManageDataSources**在安装程序 DLL。 安装程序从控制面板中调用 DLL 时，调用此函数。 若要添加、 修改或删除数据源， **SQLManageDataSources**调用**ConfigDSN**中与该数据源关联的驱动程序安装程序 DLL。 若要直接添加、 修改或删除数据源、 程序调用**SQLConfigDataSource**在安装程序 DLL。 程序将传递的数据源和一个选项，指定要执行的操作的名称。 **SQLConfigDataSource**调用**ConfigDSN**安装程序 DLL 中并将其传递的自变量从**SQLConfigDataSource**。  
  
 有关详细信息，请参阅 ODBC SDK*程序员参考*章 23、 安装程序 DLL 函数参考及章 24 个，安装程序 DLL 的函数参考。  
  
## <a name="see-also"></a>请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)


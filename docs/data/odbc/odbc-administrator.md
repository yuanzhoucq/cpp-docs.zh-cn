---
title: "ODBC 管理器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4a7d60f11457e509ae67da83aa6bc589af1ce43a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="odbc-administrator"></a>ODBC 管理器
ODBC 管理器注册和配置[数据源](../../data/odbc/data-source-odbc.md)供你在本地或通过网络。 向导使用提供由 ODBC 管理器的信息来创建你的用户连接到数据源的应用程序中的代码。  
  
 若要设置适用于 MFC ODBC 类或 MFC 数据访问对象 (DAO) 类 ODBC 数据源，必须先注册并配置数据源。 使用 ODBC 管理器添加和删除数据源。 具体取决于 ODBC 驱动程序，你还可以创建新的数据源。  
  
 ODBC 管理器安装在安装过程中。 如果你选择了**自定义**安装，但未选择任何中的 ODBC 驱动程序**数据库选项**对话框中，你需要运行安装程序以安装所需的文件。  
  
 安装过程中，选择你想要安装的 ODBC 驱动程序。 你可以更高版本安装的附加驱动程序附带有 Visual c + + 使用 Visual c + + 安装程序。  
  
 如果你想要安装 ODBC 驱动程序不是随 Visual c + +，必须运行安装程序随附的驱动程序。  
  
#### <a name="to-install-odbc-drivers-that-ship-with-visual-c"></a>若要使用 Visual c + + 安装 ODBC 驱动程序附带  
  
1.  从 Visual c + + 分发光盘上运行安装程序。  
  
     打开安装程序中的对话框时显示。  
  
2.  单击**下一步**上每个对话框中，直到你达到**安装选项**对话框。 选择**自定义**，然后单击`Next`。  
  
3.  清除所有复选框**Microsoft Visual c + + 安装程序**对话框中，除**数据库选项**复选框，并依次**详细信息**以显示**数据库选项**对话框。  
  
4.  清除**Microsoft 数据访问对象**复选框，选择**Microsoft ODBC 驱动程序**复选框，并依次**详细信息**。  
  
     **Microsoft ODBC 驱动程序**对话框随即出现。  
  
5.  选择你想要安装，，然后单击的驱动程序**确定**两次。  
  
6.  单击**下一步**上剩余的对话框中，以开始安装。 安装完成后，安装程序将通知您。  
  
 当安装驱动程序时，你可以配置数据源使用 ODBC 管理器。 在控制面板中，将找到 ODBC 图标。  
  
## <a name="see-also"></a>请参阅  
 [开放式数据库连接 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)   
 [数据源 (ODBC)](../../data/odbc/data-source-odbc.md)
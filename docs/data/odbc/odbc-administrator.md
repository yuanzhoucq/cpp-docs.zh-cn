---
title: "ODBC 管理器 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "管理 ODBC 管理器"
  - "ODBC 中的管理器"
  - "驱动程序 [C++], ODBC"
  - "安装 ODBC"
  - "ODBC [C++], ODBC 管理器"
  - "ODBC 管理器 [C++]"
  - "ODBC 数据源 [C++], ODBC 管理器"
  - "ODBC 驱动程序 [C++], 安装"
ms.assetid: b8652790-3437-4e7d-bc83-6ea6981f008b
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ODBC 管理器
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

ODBC 管理器注册和配置可供您在本地或通过网络使用的[数据源](../../data/odbc/data-source-odbc.md)。  该向导使用 ODBC 管理器提供的信息在应用程序中创建代码，将您的用户连接到数据源。  
  
 若要建立在 MFC ODBC 类中或者在 MFC 数据访问对象 \(DAO\) 类中使用 ODBC 数据源，必须首先注册和配置数据源。  使用 ODBC 管理器可以添加和移除数据源。  根据 ODBC 驱动程序，您也可以创建新的数据源。  
  
 安装过程中会安装 ODBC 管理器。  如果您选择了“自定义安装”并且在“数据库选项”对话框中没有选择任何 ODBC 驱动程序，则需要重新运行安装程序以安装必要的文件。  
  
 在安装过程中，选择要安装的 ODBC 驱动程序。  可以在以后用 Visual C\+\+ 安装程序安装随 Visual C\+\+ 附带的其他驱动程序。  
  
 如果要安装 Visual C\+\+ 未提供的 ODBC 驱动程序，必须运行驱动程序附带的安装程序。  
  
#### 安装随 Visual C\+\+ 附带的 ODBC 驱动程序  
  
1.  运行 Visual C\+\+ 分布光盘上的安装程序。  
  
     安装程序中的打开对话框出现。  
  
2.  单击每一对话框中“下一步”，直到显示“安装选项”对话框。  选择“自定义”，再单击 `Next`。  
  
3.  清除“Microsoft Visual C\+\+ 安装”对话框中除“数据库选项”以外的所有复选框，再单击“详细信息”以显示“数据库选项”对话框。  
  
4.  清除“Microsoft 数据访问对象”复选框，选择“Microsoft ODBC 驱动程序”复选框，再单击“详细信息”。  
  
     “Microsoft ODBC 驱动程序”对话框出现。  
  
5.  选择要安装的驱动程序，然后单击“确定”按钮两次。  
  
6.  单击其余对话框上的“下一步”按钮开始安装。  安装结束时，安装程序会通知您。  
  
 安装完驱动程序后，就可以使用 ODBC 管理器配置数据源了。  将会在“控制面板”中找到 ODBC 图标。  
  
## 请参阅  
 [开放式数据库连接 \(ODBC\)](../../data/odbc/open-database-connectivity-odbc.md)   
 [数据源 \(ODBC\)](../../data/odbc/data-source-odbc.md)
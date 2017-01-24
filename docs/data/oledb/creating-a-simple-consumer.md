---
title: "创建简单使用者 | Microsoft Docs"
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
  - "OLE DB 使用者, 创建"
ms.assetid: ae32d657-72ea-4db8-9839-75cb5cff68ae
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 创建简单使用者
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用“ATL 项目向导”和“ATL OLE DB 使用者向导”生成 OLE DB 模板使用者。  
  
#### 创建 OLE DB 使用者的控制台应用程序  
  
1.  在**“文件”**菜单上单击**“新建”**，再单击**“项目”**。  
  
     此时将出现**“新建项目”**对话框。  
  
2.  在“项目类型”窗格中单击 **“Visual C\+\+ 项目”**文件夹，然后在“模板”窗格中单击**“Win32 项目”**图标。  在“名称”框中，输入项目的名称，例如 **MyCons**。  
  
3.  单击**“确定”**。  
  
     “Win32 项目向导”出现。  
  
4.  在**“应用程序设置”**页上，选择“控制台应用程序”，再选择“添加对 ATL 的支持”。  
  
5.  单击“完成”关闭向导并生成该项目。  
  
 下一步，使用“ATL OLE DB 使用者向导”添加 OLE DB 使用者对象。  
  
#### 用“ATL OLE DB 使用者向导”创建使用者  
  
1.  在“类视图”中，右击`MyCons`项目。  
  
2.  在快捷菜单上，单击“添加”，然后单击“添加类”。  
  
     出现“添加类”对话框。  
  
3.  在“类别”窗格中单击**Visual C\+\+**，在“模板”窗格中单击**ATL OLE DB Consumer**图标，然后单击k **打开**。  
  
     出现“ATL OLE DB 使用者向导”。  
  
4.  单击**“数据源”**按钮。  
  
     出现**“数据链接属性”**对话框。  
  
5.  在**“数据链接属性”**对话框中，进行下面的操作：  
  
    -   在“提供程序”选项卡上指定 OLE DB 提供程序。  
  
    -   在**“连接”**选项卡上，指定数据源的服务器名称、登录 ID 和密码以及服务器上的数据库。  
  
    > [!NOTE]
    >  **“数据链接属性”**对话框的“允许保存密码”功能存在安全问题。  在“输入登录服务器的信息”中有两个单选按钮：“使用 Windows NT 集成安全性” 和“使用特定的用户名和密码”。  
  
    > [!NOTE]
    >  如果选择“使用特定的用户名和密码”，则可以选择保存密码（使用“允许保存密码”复选框）；但此选项不安全。  建议您选择“使用 Windows NT 集成安全性”；此选项使用 Windows NT 来验证标识。  
  
    > [!NOTE]
    >  如果无法使用 Windows NT 集成安全性，则应使用中间层应用程序来提示用户输入密码，或者将密码存储在安全的位置（而不是源代码中）。  
  
     在选择了提供程序和其他设置后，单击“测试连接”验证在前面对话框页中所做的选择。  如果**“结果”**框报告`Test connection succeeded`，则单击**OK**创建数据链接。  
  
     出现“选择数据库对象”对话框。  
  
6.  使用树控件 \(Tree Control\) 选择表、视图或存储过程。  为完成此过程，请从 Northwind 数据库中选择 Products 表。  
  
7.  单击**“确定”**。  这将返回到“ATL OLE DB 使用者向导”。  
  
8.  向导根据所选择的表、视图或存储过程的名称完成`Class` 和**“.h 文件”** 的名称。  如果需要可以编辑这些名称。  
  
9. 清除“特性化”复选框，以便向导使用 [OLE DB 模板类](../../data/oledb/ole-db-consumer-templates-reference.md) 而不是默认的 [OLE DB 使用者特性](../../windows/ole-db-consumer-attributes.md) 来创建使用者代码。  
  
10. 在**“类型”**下，选择**“命令”**。  
  
     如果选择“命令”，则向导创建基于 [CCommand](../../data/oledb/ccommand-class.md) 的使用者；如果选择“表”，则向导创建基于 [CTable](../../data/oledb/ctable-class.md) 的使用者。  此表或命令类根据选定对象命名，但您可以编辑此名称。  
  
11. 在“支持”下，保留“更改”、“插入”和“删除”框的清除状态。  
  
     如果需要，选择“更改”、“插入”和“删除”复选框以支持在行集合中更改、插入和删除记录。  有关将数据写入数据存储区的更多信息，请参见 [更新行集](../../data/oledb/updating-rowsets.md)。  
  
12. 单击“完成”创建使用者。  
  
 向导生成命令类和用户记录类，如[使用者向导生成的类](../../data/oledb/consumer-wizard-generated-classes.md)中所示。  命令类将具有您在向导中输入到`Class` 框中的名称（在本例中为 `CProducts`），而用户记录类将具有“*ClassName*Accessor”形式的名称（在本例中为 `CProductsAccessor`）。  
  
> [!NOTE]
>  向导将在 Products.h 中插入下面一行代码：  
  
```  
#error Security Issue: The connection string may contain a password  
```  
  
> [!NOTE]
>  此行代码可以避免对使用者应用程序进行编译，并提醒您检查您的连接字符串中的硬编码密码。  检查了连接字符串之后，便可以移除此行代码。  
  
## 请参阅  
 [使用向导创建 OLE DB 使用者](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)
---
title: "创建简单使用者 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB consumers, creating
ms.assetid: ae32d657-72ea-4db8-9839-75cb5cff68ae
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 553d4f8875812aa9453ec39e0e3223bd3463a31a
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="creating-a-simple-consumer"></a>创建简单使用者
使用 ATL 项目向导和 ATL OLE DB 使用者向导生成 OLE DB 模板使用者。  
  
#### <a name="to-create-a-console-application-for-an-ole-db-consumer"></a>若要为 OLE DB 使用者创建一个控制台应用程序  
  
1.  在 **“文件”** 菜单上，单击 **“新建”**，然后单击 **“项目”**。  
  
     此时将出现 “新建项目” 对话框。  
  
2.  在项目类型窗格中，单击**Visual c + + 项目**文件夹，，然后单击**Win32 项目**在模板窗格中的图标。 在**名称**框中，例如，输入你的项目的名称**MyCons**。  
  
3.  单击 **“确定”**。  
  
     将出现 Win32 项目向导。  
  
4.  上**应用程序设置**页上，选择**控制台应用程序**，然后选择**添加 ATL 支持**。  
  
5.  单击**完成**可关闭向导并且生成项目。  
  
 接下来，使用 ATL OLE DB 使用者向导添加的 OLE DB 使用者对象。  
  
#### <a name="to-create-a-consumer-with-the-atl-ole-db-consumer-wizard"></a>使用 ATL OLE DB 使用者向导创建使用者  
  
1.  在类视图中，右键单击`MyCons`项目。  
  
2.  在快捷菜单上，单击**添加**，然后单击**添加类**。  
  
     **添加类**对话框随即出现。  
  
3.  在类别窗格中，单击**Visual c + +**，单击**ATL OLE DB 使用者**在模板窗格中，然后单击图标**打开**。  
  
     ATL OLE DB 使用者向导显示。  
  
4.  单击**数据源**按钮。  
  
     **数据链接属性**对话框随即出现。  
  
5.  在**数据链接属性**对话框框中，执行以下操作：  
  
    -   上**提供程序**选项卡上，指定的 OLE DB 提供程序。  
  
    -   上**连接**选项卡上，指定服务器上的服务器名称、 登录 ID 和你的数据源和数据库的密码。  
  
    > [!NOTE]
    >  没有与安全性问题**允许保存密码**功能**数据链接属性**对话框。 在**输入信息以登录到服务器**，有两个单选按钮：**使用 Windows NT 集成安全性**和**使用特定用户名和密码**。  
  
    > [!NOTE]
    >  如果你选择**使用特定用户名和密码**，你可以选择保存密码 (使用**允许保存密码**复选框); 但是，此选项不安全。 我们建议你选择**使用 Windows NT 集成安全性**; 此选项使用 Windows NT 验证你的身份。  
  
    > [!NOTE]
    >  如果无法使用 Windows NT 集成安全性，你应使用一个中间层应用程序来提示用户输入密码或者与安全机制，以帮助保护将密码存储在一个位置 (而不是在源代码中)。  
  
     选择你的提供商和其他设置后，单击**测试连接**验证在前面的对话框页上所做的选择。 如果**结果**框中报表`Test connection succeeded`，单击**确定**以创建数据链接。  
  
     **选择数据库对象**对话框随即出现。  
  
6.  使用树控件选择表、 视图或存储的过程。 此过程中，为了从 Northwind 数据库中选择产品表。  
  
7.  单击 **“确定”**。 此操作将返回到 ATL OLE DB 使用者向导。  
  
8.  在向导完成的名称`Class`和**.h 文件**基于名称的表、 视图或存储你选择的过程。 如果你想，你可以编辑这些名称。  
  
9. 清除**属性化**复选框，以便该向导创建使用者代码使用[OLE DB 模板类](../../data/oledb/ole-db-consumer-templates-reference.md)而非默认[OLE DB 使用者特性](../../windows/ole-db-consumer-attributes.md)。  
  
10. 下**类型**，选择**命令**。  
  
     此向导将创建[CCommand](../../data/oledb/ccommand-class.md)-如果你选择基于使用者**命令**或[CTable](../../data/oledb/ctable-class.md)-如果你选择基于使用者**表**。 此表或命令类命名所选对象，但您可以编辑该名称。  
  
11. 下**支持**，保留**更改**，**插入**，和**删除**框被清除。  
  
     选择**更改**，**插入**，和**删除**复选框以支持更改、 插入和删除的行集中的记录，如果需要。 有关将数据写入到数据存储，请参阅[更新行集合](../../data/oledb/updating-rowsets.md)。  
  
12. 单击**完成**创建使用者。  
  
 中所示，向导将生成命令类和用户记录类，[使用者向导生成类](../../data/oledb/consumer-wizard-generated-classes.md)。 命令类将具有你在中输入的名称`Class`框中的向导 (在这种情况下， `CProducts`)，用户记录类将具有窗体的名称和"*ClassName*访问器"(在这种情况下， `CProductsAccessor`)。  
  
> [!NOTE]
>  向导将放入 Products.h 的以下行：  
  
```  
#error Security Issue: The connection string may contain a password  
```  
  
> [!NOTE]
>  此行禁止使用者应用程序进行编译，提醒您检查硬编码密码的连接字符串。 在检查你的连接字符串之后, 你可以删除此代码行。  
  
## <a name="see-also"></a>请参阅  
 [使用向导创建 OLE DB 使用者](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)
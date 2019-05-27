---
title: 创建简单使用者
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB consumers, creating
ms.assetid: ae32d657-72ea-4db8-9839-75cb5cff68ae
ms.openlocfilehash: cc24df1f15d43c384e6bf3853766fad82cf51255
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707717"
---
# <a name="creating-a-simple-consumer"></a>创建简单使用者

::: moniker range="vs-2019"

ATL OLE DB 使用者向导不适用于 Visual Studio 2019 及更高版本。 但仍可以手动添加此功能。 有关详细信息，请参阅[不使用向导创建使用者](creating-a-consumer-without-using-a-wizard.md)。

::: moniker-end

::: moniker range="<=vs-2017"

ATL 项目向导和 ATL OLE DB 使用者向导可用于生成 OLE DB 模板使用者。

## <a name="to-create-a-console-application-for-an-ole-db-consumer"></a>为 OLE DB 使用者创建控制台应用程序的具体步骤

1. 在 **“文件”** 菜单上，单击 **“新建”**，然后单击 **“项目”**。

   此时将出现“新建项目”对话框。

1. 在“项目类型”窗格中，依次单击“已安装” > “Visual C++” > “Windows 桌面”文件夹，再单击“模板”窗格中的“Windows 桌面向导”图标。 在“名称”框中，输入项目名称（例如“MyCons”）。

1. 单击 **“确定”**。

   此时，“Windows 桌面项目”向导显示。

1. 在“应用程序设置”页上，依次选择“控制台应用程序”和“添加 ATL 的常用头文件”。

1. 单击“确定”，以关闭向导并生成项目。

接下来，使用 ATL OLE DB 使用者向导来添加 OLE DB 使用者对象。

## <a name="to-create-a-consumer-with-the-atl-ole-db-consumer-wizard"></a>使用 ATL OLE DB 使用者向导来创建使用者的具体步骤

1. 在“解决方案资源管理器”中，右键单击“`MyCons`”项目。

1. 在快捷菜单中，依次单击“添加”和“新项”。

   “添加新项”对话框随即出现。

1. 在“类别”窗格中，依次单击“已安装”>“Visual C++”>“ATL”，再依次单击“模板”窗格中的“ATL OLEDB 使用者”图标和“添加”。

   此时，ATL OLEDB 使用者向导显示。

1. 单击“数据源”按钮。

   此时，“数据链接属性”对话框显示。

1. 在“数据链接属性”对话框框中，执行以下操作：

   1. 在“提供程序”选项卡上，指定 OLE DB 提供程序。

   1. 在“连接”选项卡上，指定数据源和服务器上的数据库的必需信息（如服务器名称、登录 ID 和密码）。

      > [!NOTE]
      > “数据链接属性”对话框的“允许保存密码”功能存在安全问题。 在“输入登录服务器所需的信息”中，有两个单选按钮：“使用 Windows NT 集成安全性”和“使用特定的用户名和密码”。

      > [!NOTE]
      > 如果选中“使用特定的用户名和密码”，可以视需要保存密码（使用“允许保存密码”复选框），但这样做并不安全。 建议选中“使用 Windows NT 集成安全性”；此选项使用 Windows NT 来验证身份。

      > [!NOTE]
      > 如果无法使用 Windows NT 集成安全性，应使用中间层应用程序来提示用户输入密码，或将密码存储在有安全机制的位置上来保护它（而不是存储在源代码中）。

   1. 选择提供程序和其他设置后，单击“测试连接”，以验证在前几个对话框页上所做的选择。 如果“结果”框报告“`Test connection succeeded`”，单击“确定”来创建数据链接。

   此时，“选择数据库对象”对话框显示。

1. 使用树控件来选择表、视图或存储过程。 在此示例中，从“`Northwind`”数据库中选择“`Products`”表。

1. 单击 **“确定”**。 这样，你会返回到 ATL OLE DB 使用者向导。

1. 向导根据你选择的表、视图或存储过程的名称，填写“`Class`”和“.h 文件”名称。 如果需要，可以编辑这些名称。

1. 取消选中“特性化”复选框，这样向导就能使用 [OLE DB 模板类](../../data/oledb/ole-db-consumer-templates-reference.md)（而不是默认 [OLE DB 使用者特性](../../windows/ole-db-consumer-attributes.md)）来创建使用者代码。

1. 在“类型”下，选择“命令”。

   如果你选择“命令”，向导创建基于 [CCommand](../../data/oledb/ccommand-class.md) 的使用者；如果你选择“表”，向导创建基于 [CTable](../../data/oledb/ctable-class.md) 的使用者。 虽然表或命令类是以选定对象命名，但你可以编辑名称。

1. 在“支持”下，取消选中“更改”、“插入”和“删除”框。

   选中“更改”、“插入”和“删除”复选框，可以支持更改、插入和删除行集中的记录。 若要详细了解如何将数据写入数据存储，请参阅[更新行集](../../data/oledb/updating-rowsets.md)。

1. 单击“完成”，以创建使用者。

此时，向导生成命令类和用户记录类，如[使用者向导生成的类](../../data/oledb/consumer-wizard-generated-classes.md)中所述。 命令类以你在向导的“`Class`”框中输入的名称命名（在此示例中为 `CProducts`），用户记录类采用“ClassNameAccessor”格式的名称（在此示例中为 `CProductsAccessor`）。

> [!NOTE]
> 向导将下面的代码行添加到 `Products.h` 中：

```cpp
#error Security Issue: The connection string may contain a password
```

> [!NOTE]
> 此代码行会阻止使用者应用程序进行编译，并提醒你检查连接字符串中是否有硬编码密码。 检查连接字符串后，可以删除此代码行。

::: moniker-end

## <a name="see-also"></a>请参阅

[使用向导创建 OLE DB 使用者](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)

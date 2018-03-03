---
title: "MFC ODBC 使用者向导 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.codewiz.class.mfc.consumer.overview
dev_langs:
- C++
helpviewer_keywords:
- MFC ODBC Consumer Wizard
- wizards [MFC]
ms.assetid: f64a890b-a252-4887-88a1-782a7cd4ff3d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ad9e4aeb15d2af04987883b6554d569e3cc16b8d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-odbc-consumer-wizard"></a>MFC ODBC 使用者向导
在此处插入摘要的"搜索结果"。  
  
 此向导将设置一个 ODBC 记录集类和数据绑定访问指定的数据源所需。  
  
## <a name="uielement-list"></a>UIElement 列表  
 **数据源**  
 **数据源**按钮的使你可以设置使用指定的 ODBC 驱动程序指定的数据源。 有关数据源文件 (DSN) 的详细信息，请参阅[文件数据源](https://msdn.microsoft.com/library/ms715401.aspx)ODBC SDK 中。 **选择数据源**对话框中有两个选项卡：  
  
-   **文件数据源**选项卡：**查找**框指定在其中选择要用作数据源的文件的目录。 默认值为 \program Files\ODBC\Data 源。 在主列表框中显示现有的文件数据源 （.dsn 文件）。 你可以事先使用的数据源设置**文件 DSN**选项卡上[ODBC 数据源管理器](https://msdn.microsoft.com/library/ms714024.aspx)，或使用此对话框中创建新的。  
  
     若要通过此对话框创建新的文件数据源，请单击`New`指定 DSN 名称;**新建数据源**对话框随即出现。 在**新建数据源**对话框中，选择合适的驱动程序并单击`Next`; 单击**浏览**，并选择要用作数据源 （你需要选择"所有文件"的文件的名称查看非 DSN 文件，如.xls 文件）;单击`Next`，然后单击**完成**。 （如果你选择了非 DSN 文件，你将获取特定于驱动程序的对话框中，如"ODBC Microsoft Excel 安装程序，"会将该文件转换为 DSN）。  
  
    > [!NOTE]
    >  你还可以创建新的文件数据源事先使用 ODBC 数据源管理器。 从**启动**菜单上，选择**设置**，**控制面板**，**管理工具**，**数据源 (ODBC)**，，然后**ODBC 数据源管理器**。  
  
     **DSN 名称**框允许你指定的文件数据源的名称。 你必须确保 DSN 名称，以适当的文件扩展名，如 Excel 文件的.xls 或访问文件的.mdb 结尾。  
  
     Dsn 的详细信息，请参阅[文件数据源](https://msdn.microsoft.com/library/ms715401.aspx)ODBC SDK 中。  
  
-   **计算机数据源**选项卡： 此选项卡列出系统和用户数据源。 用户数据源是特定于此计算机上的用户。 系统数据源可以使用此计算机上或在系统级服务上的所有用户。 请参阅[机器数据源](https://msdn.microsoft.com/library/ms710952.aspx)ODBC SDK 中  
  
 ODBC 数据源的详细信息，请参阅[数据源](https://msdn.microsoft.com/library/ms711688.aspx)ODBC SDK 中。  
  
 单击**确定**完成。 **选择数据库对象**对话框随即出现。 此对话框中，从选择的表或查看，将使用使用者。 请注意，你可以通过单击项时按住控件键选择多个视图和表。  
  
 **类**  
 默认情况下基于你选择的文件或计算机数据源的名称的使用者类的名称。  
  
 **.h 文件**  
 默认情况下基于你选择的文件或计算机数据源的名称的使用者类标头文件的名称。  
  
 **.cpp 文件**  
 默认情况下基于你选择的文件或计算机数据源的名称的使用者类实现文件的名称。  
  
 **Type**  
 指定记录集是动态集 （默认） 或快照。  
  
-   **动态集**： 指定的记录集是动态集。 动态集是查询的提供为查询的数据库的数据的索引的视图的结果。 动态集缓存仅的原始数据的整数索引并提供了一个性能因此获得比快照。 直接与每个记录的索引点找到作为查询结果，并指示是否删除一条记录。 查询记录中还有权访问更新信息。 这是默认设置。  
  
-   **快照**： 指定记录集是快照。 快照是查询的结果，并且是时间点的数据库。 由于查询找到的所有记录会都缓存，因此你看不到对原始记录的任何更改。  
  
 **将所有列都绑定**  
 指定是否绑定中所选表的所有列。 如果选择此框 （默认值） 时，绑定所有列;如果不选择此框，没有列被绑定，并在记录集类，必须手动绑定它们。  
  
## <a name="see-also"></a>请参阅  
 [MFC ODBC 使用](../../mfc/reference/adding-an-mfc-odbc-consumer.md)   
 [用代码向导添加功能](../../ide/adding-functionality-with-code-wizards-cpp.md)


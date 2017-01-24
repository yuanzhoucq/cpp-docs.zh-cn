---
title: "在 Visual C++ 中使用 RDO 数据绑定 | Microsoft Docs"
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
  - "数据绑定 [C++], RDO"
  - "RDO [C++], 数据绑定"
  - "RDO RemoteData 控件, 在 Visual C++ 中绑定数据"
  - "RemoteData 控件, 在 Visual C++ 中绑定数据"
ms.assetid: 02b9cfe7-7bbe-4a01-b075-e28d9536ac4b
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 在 Visual C++ 中使用 RDO 数据绑定
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

若要在 Visual C\+\+ 中使用 RDO 数据绑定，需要添加 RDO RemoteData 控件并指向数据源和记录源（SQL 查询）。  还需要添加 RDO 数据绑定控件，将其指向 RDO RemoteData 控件，并选择要绑定到 RDO RemoteData 控件记录源的字段。  
  
### 在 Visual C\+\+ 中使用 RDO 数据绑定  
  
1.  如果尚未配置 [ODBC 数据源](../../data/ado-rdo/odbc-connections.md)，执行此操作。  
  
2.  使用“MFC 应用程序向导”创建 MFC 对话框应用程序或 MFC Formview 应用程序。  
  
3.  将 Microsoft RemoteData 控件（RDO RemoteData 控件）添加到对话框；请参见[将控件插入 Visual C\+\+ 应用程序](../../data/ado-rdo/inserting-the-control-into-a-visual-cpp-application.md)。  
  
4.  将 RDO RemoteData 控件指向 ODBC 数据源。  
  
    1.  右击该控件，然后单击**“属性”**。  
  
    2.  单击“控件”选项卡。  
  
    3.  将 **DataSource** 设置为 ODBC 数据源。  
  
    4.  根据需要，为 ODBC 数据源设置用户名和密码。  如果数据源不需要用户名或密码，则保留为空。  
  
    5.  将 SQL 查询输入到 **SQL** 属性中。  数据绑定控件可绑定到此查询的结果。  
  
5.  设置所需的任何其他 RDO RemoteData 控件属性。  
  
6.  添加数据绑定控件。  例如，添加“DBGrid 控件”，然后按如下所示设置数据源。  
  
    1.  右击该 DBGrid，然后单击**“属性”**。  
  
    2.  单击**“所有”**选项卡。  
  
    3.  将 **DataSource** 属性设置为 RDO RemoteData 控件。  单击该属性的下拉组合框并找到 RDO RemoteData 控件的 ID。  默认 ID 名称为 IDC\_REMOTEDATACTL1。  
  
7.  若要以测试模式运行，请使用 Ctrl\+T。  将能够在数据中滚动。  按 Esc 键或关闭对话框以结束测试模式。  
  
 如果编译和运行程序，同样能够在数据中滚动。  
  
## 请参阅  
 [RDO 数据绑定](../../data/ado-rdo/rdo-databinding.md)   
 [在 Visual C\+\+ 中使用 ActiveX 控件进行数据绑定](../../data/ado-rdo/databinding-with-activex-controls-in-visual-cpp.md)
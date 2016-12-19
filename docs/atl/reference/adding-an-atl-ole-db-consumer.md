---
title: "添加 ATL OLE DB 使用者 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL OLE DB 使用者"
  - "ATL 项目, 添加 ATL OLE DB 使用者"
  - "OLE DB, 添加 ATL OLE DB 使用者到项目"
ms.assetid: f940a513-4e42-4148-b521-dd0d7dc89fa2
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 添加 ATL OLE DB 使用者
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用此向导可向项目中添加 ATL OLE DB 使用者。  ATL OLE DB 使用者由 OLE DB 访问器类和访问数据源所需的数据绑定组成。  该项目必须是已创建好的 ATL COM 应用程序，或是已创建好的包含 ATL 支持（“ATL OLE DB 使用者向导”自动添加它）的 MFC 或 Win32 应用程序。  
  
 **Note** 可以将OLE DB使用者添加到MFC项目。  如果执行此操作，则“ATL OLE DB 使用者向导”将向项目中添加必要的 COM 支持。  这假定在创建 MFC 项目时选择了**“ActiveX 控件”**复选框（在“MFC 项目应用程序向导”的**“高级功能”**页中），默认情况下该复选框为选中状态。  选择此选项可确保应用程序调用 **CoInitialize** 和 **CoUninitialize**。  如果在创建 MFC 项目时未选择**“ActiveX 控件”**，则需要在主代码中调用 **CoInitialize** 和 **CoUninitialize**。  
  
### 向项目中添加 ATL OLE DB 使用者  
  
1.  在“类视图”中，右击该项目。  在快捷菜单上单击“添加”，然后单击“添加类”。  
  
2.  在 Visual C\+\+ 文件夹中，双击“ATL OLE DB 使用者”图标，或者选定它并单击“打开”。  
  
     即会打开“ATL OLE DB 使用者向导”。  
  
3.  按 [ATL OLE DB 使用者向导](../../atl/reference/atl-ole-db-consumer-wizard.md)中描述的那样定义设置。  
  
4.  单击**“完成”**关闭向导。  新创建的 OLE DB 使用者代码随即插入到项目中。  
  
## 请参阅  
 [用代码向导添加功能](../../ide/adding-functionality-with-code-wizards-cpp.md)
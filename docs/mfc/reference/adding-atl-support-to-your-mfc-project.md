---
title: "向 MFC 项目添加 ATL 支持 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.codewiz.adding.atl.mfc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL, MFC 项目"
  - "MFC, ATL 支持"
ms.assetid: b5fe15d6-7752-4818-b9f9-62482ad35c95
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# 向 MFC 项目添加 ATL 支持
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

如果已经创建了基于 MFC 的应用程序，则可以通过运行“向 MFC 项目向导添加 ATL 支持”轻松添加活动模板库 \(ATL\) 支持。  
  
> [!NOTE]
>  ATL 和 MFC 在 Visual Studio 速成编辑通常不支持。  
  
> [!NOTE]
>  该支持仅应用到添加到 MFC 可执行文件或 DLL 项目的简单 COM 对象。  可以向 MFC 项目添加其他 COM 对象（包括 ActiveX 控件），但对象可能不按预期的方式操作。  
  
### 向 MFC 项目添加 ATL 支持  
  
1.  在“解决方案资源管理器”中，右击要向其添加 ATL 支持的项目。  
  
2.  在快捷菜单上，单击“添加”，然后单击“添加类”。  
  
3.  选择“向 MFC 添加 ATL 支持”图标。  
  
    > [!NOTE]
    >  此图标位于**“类别”**窗格的 ATL 文件夹中。  
  
4.  得到提示时，单击**“是”**添加 ATL 支持。  
  
 有关添加 ATL 支持如何更改 MFC 项目代码的更多信息，请参见 [ATL 向导添加的 ATL 支持的详细信息](../../mfc/reference/details-of-atl-support-added-by-the-atl-wizard.md)  
  
## 请参阅  
 [添加类](../../ide/adding-a-class-visual-cpp.md)   
 [用代码向导添加功能](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [添加成员函数](../../ide/adding-a-member-function-visual-cpp.md)   
 [添加成员变量](../../ide/adding-a-member-variable-visual-cpp.md)   
 [重写虚函数](../../ide/overriding-a-virtual-function-visual-cpp.md)   
 [MFC 消息处理程序](../../mfc/reference/adding-an-mfc-message-handler.md)   
 [导航类结构](../../ide/navigating-the-class-structure-visual-cpp.md)
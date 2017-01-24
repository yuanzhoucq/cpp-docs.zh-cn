---
title: "创建 MFC 应用程序 | Microsoft Docs"
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
  - "应用程序 [MFC]"
  - "MFC [C++], 创建应用程序"
  - "MFC 应用程序"
ms.assetid: b8b8aa08-9c49-404c-8078-b42079ac18f0
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 创建 MFC 应用程序
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

MFC 应用程序是基于 Microsoft 基础类 \(MFC\) 库的 Windows 可执行应用程序。  创建 MFC 应用程序的最容易方法是使用 MFC 应用程序向导。  
  
> [!IMPORTANT]
>  Visual Studio Express 版本不支持 MFC 项目。  
  
 MFC 可执行程序通常分为五类：标准 Windows 应用程序、对话框、基于窗体的应用程序、资源管理器样式的应用程序和 Web 浏览器样式的应用程序。  有关详细信息，请参阅：  
  
-   [使用类编写 Windows 应用程序](../../mfc/using-the-classes-to-write-applications-for-windows.md)  
  
-   [创建并显示对话框](../../mfc/creating-and-displaying-dialog-boxes.md)  
  
-   [创建基于窗体的 MFC 应用程序](../../mfc/reference/creating-a-forms-based-mfc-application.md)  
  
-   [创建文件资源管理器样式的 MFC 应用程序](../../mfc/reference/creating-a-file-explorer-style-mfc-application.md)  
  
-   [创建 Web 浏览器样式的 MFC 应用程序](../../mfc/reference/creating-a-web-browser-style-mfc-application.md)  
  
 根据在向导中选择的选项，MFC 应用程序向导为上述任何应用程序生成适当的类和文件。  
  
### 使用 MFC 应用程序向导创建 MFC 应用程序  
  
1.  按照帮助主题[用 Visual C\+\+ 应用程序向导创建项目](../../ide/creating-desktop-projects-by-using-application-wizards.md)中的说明进行操作。  
  
2.  在**“新建项目”**对话框中，选择“模板”窗格中的**“MFC 应用程序”**打开向导。  
  
3.  使用 [MFC 应用程序向导](../../mfc/reference/mfc-application-wizard.md)定义应用程序设置。  
  
    > [!NOTE]
    >  跳过此步骤可保留向导的默认设置。  
  
4.  单击“完成”关闭向导并在开发环境中打开新项目。  
  
 创建项目后，可在**解决方案资源管理器**中查看创建的文件。  有关向导为项目创建的文件的更多信息，请参见项目生成的文件 ReadMe.txt。  有关文件类型的更多信息，请参见[为 Visual C\+\+ 项目创建的文件类型](../../ide/file-types-created-for-visual-cpp-projects.md)。  
  
## 请参阅  
 [Debugging Preparation: Visual C\+\+ Windows Applications](http://msdn.microsoft.com/zh-cn/a8bc54de-41a3-464d-9a12-db9bdcbc1ad5)   
 [用代码向导添加功能](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [属性页](../../ide/property-pages-visual-cpp.md)   
 [Deploying Applications](http://msdn.microsoft.com/zh-cn/4ff8881d-0daf-47e7-bfe7-774c625031b4)
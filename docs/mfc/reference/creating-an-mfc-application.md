---
title: "创建 MFC 应用程序 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- applications [MFC]
- MFC, creating applications
- MFC applications
ms.assetid: b8b8aa08-9c49-404c-8078-b42079ac18f0
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: eb5f30dfaf3710e1b3dbe782a0aa24b3cd02deb4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="creating-an-mfc-application"></a>创建 MFC 应用程序
MFC 应用程序是基于 Microsoft 基础类 (MFC) 库的 Windows 可执行应用程序。 创建 MFC 应用程序的最容易方法是使用 MFC 应用程序向导。  
  
> [!IMPORTANT]
>  Visual Studio Express 版本不支持 MFC 项目。  
  
 MFC 可执行程序通常分为五类： 标准 Windows 应用程序、 对话框、 基于窗体的应用程序，资源管理器样式的应用程序和 Web 浏览器样式的应用程序。 有关详细信息，请参见:  
  
-   [使用类编写 Windows 应用程序](../../mfc/using-the-classes-to-write-applications-for-windows.md)  
  
-   [创建并显示对话框](../../mfc/creating-and-displaying-dialog-boxes.md)  
  
-   [创建基于窗体的 MFC 应用程序](../../mfc/reference/creating-a-forms-based-mfc-application.md)  
  
-   [创建文件资源管理器样式的 MFC 应用程序](../../mfc/reference/creating-a-file-explorer-style-mfc-application.md)  
  
-   [创建 Web 浏览器样式的 MFC 应用程序](../../mfc/reference/creating-a-web-browser-style-mfc-application.md)  
  
 根据在向导中选择的选项，MFC 应用程序向导为上述任何应用程序生成适当的类和文件。  
  
### <a name="to-create-an-mfc-application-using-the-mfc-application-wizard"></a>使用 MFC 应用程序向导创建 MFC 应用程序  
  
1.  按照帮助主题中的说明[使用 Visual c + + 应用程序向导创建项目](../../ide/creating-desktop-projects-by-using-application-wizards.md)。  
  
2.  在**新项目**对话框中，选择**MFC 应用程序**在模板窗格中，以打开向导。  
  
3.  定义你使用的应用程序设置[MFC 应用程序向导](../../mfc/reference/mfc-application-wizard.md)。  
  
    > [!NOTE]
    >  跳过此步骤可保留向导的默认设置。  
  
4.  单击**完成**关闭向导并在开发环境中打开你的新项目。  
  
 你的项目创建后，你可以查看在中创建的文件**解决方案资源管理器**。 有关向导为项目创建的文件的更多信息，请参见项目生成的文件 ReadMe.txt。 有关文件类型的详细信息，请参阅[Visual c + + 项目创建的文件类型](../../ide/file-types-created-for-visual-cpp-projects.md)。  
  
## <a name="see-also"></a>另请参阅  
 [调试准备： Visual c + + Windows 应用程序](http://msdn.microsoft.com/en-us/a8bc54de-41a3-464d-9a12-db9bdcbc1ad5)   
 [用代码向导添加功能](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [属性页](../../ide/property-pages-visual-cpp.md)   
 [部署应用程序](http://msdn.microsoft.com/en-us/4ff8881d-0daf-47e7-bfe7-774c625031b4)


---
title: "创建 MFC ActiveX 控件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.appwiz.activex.project
dev_langs: C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], creating
- ActiveX controls [MFC], creating
ms.assetid: 8bd5a93c-d04d-414e-bb28-163fdc1c0dd5
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e01f0e0c1f24839f1d33184448559c1e8f48ceb4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="creating-an-mfc-activex-control"></a>创建 MFC ActiveX 控件
ActiveX 控件的程序设计为向父应用程序提供特定类型的功能的模块化程序。 例如，你可以创建如用于按钮的控件在对话框中或使用网页中的工具栏中。  
  
 创建 MFC ActiveX 控件的最简单方法是使用[MFC ActiveX 控件向导](../../mfc/reference/mfc-activex-control-wizard.md)。  
  
### <a name="to-create-an-mfc-activex-control-using-the-mfc-activex-control-wizard"></a>若要创建 MFC ActiveX 控件使用 MFC ActiveX 控件向导  
  
1.  按照帮助主题中的说明[使用 Visual c + + 应用程序向导创建项目](../../ide/creating-desktop-projects-by-using-application-wizards.md)。  
  
2.  在**新项目**对话框中，选择**MFC ActiveX 控件**在模板窗格中，若要打开 MFC ActiveX 控件向导图标。  
  
3.  定义你[应用程序设置](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)，[的控件名称](../../mfc/reference/control-names-mfc-activex-control-wizard.md)，和[控制设置](../../mfc/reference/control-settings-mfc-activex-control-wizard.md)使用 MFC ActiveX 控件向导。  
  
    > [!NOTE]
    >  跳过此步骤可保留向导的默认设置。  
  
4.  单击**完成**关闭向导并在开发环境中打开你的新项目。  
  
 创建你的项目后，你可以查看在中创建的文件**解决方案资源管理器**。 有关向导为项目创建的文件的更多信息，请参见项目生成的文件 ReadMe.txt。 有关文件类型的详细信息，请参阅[Visual c + + 项目创建的文件类型](../../ide/file-types-created-for-visual-cpp-projects.md)。  
  
 创建你的项目后，你可以使用代码向导添加[函数](../../ide/add-member-function-wizard.md)，[变量](../../ide/add-member-variable-wizard.md)，[事件](../../ide/add-event-wizard.md)，[属性](../../ide/names-add-property-wizard.md)，和[方法](../../ide/add-method-wizard.md)。 有关自定义 ActiveX 控件的详细信息，请参阅[MFC ActiveX 控件](../../mfc/mfc-activex-controls.md)。  
  
## <a name="see-also"></a>另请参阅  
 [用代码向导添加功能](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [属性页](../../ide/property-pages-visual-cpp.md)   
 [部署应用程序](http://msdn.microsoft.com/en-us/4ff8881d-0daf-47e7-bfe7-774c625031b4)


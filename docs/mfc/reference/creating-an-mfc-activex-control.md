---
title: 创建 MFC ActiveX 控件 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.activex.project
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], creating
- ActiveX controls [MFC], creating
ms.assetid: 8bd5a93c-d04d-414e-bb28-163fdc1c0dd5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 96ecae8445368357da3bc7b271156f961c1c1dca
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2018
ms.locfileid: "43687141"
---
# <a name="creating-an-mfc-activex-control"></a>创建 MFC ActiveX 控件
ActiveX 控件程序是功能的模块化设计用于为特定类型提供到父应用程序的程序。 例如，您可以在对话框中或在网页中使用的工具栏中创建等使用的按钮控件。  
  
 创建 MFC ActiveX 控件的最简单方法是使用[MFC ActiveX 控件向导](../../mfc/reference/mfc-activex-control-wizard.md)。  
  
### <a name="to-create-an-mfc-activex-control-using-the-mfc-activex-control-wizard"></a>若要创建 MFC ActiveX 控件使用 MFC ActiveX 控件向导  
  
1.  请按帮助主题[使用 Visual C++ 应用程序向导创建项目](../../ide/creating-desktop-projects-by-using-application-wizards.md)中的说明进行操作。  
  
2.  在中**新的项目**对话框中，选择**MFC ActiveX 控件**在模板窗格中，若要打开 MFC ActiveX 控件向导的图标。  
  
3.  定义你[应用程序设置](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)，[控件名称](../../mfc/reference/control-names-mfc-activex-control-wizard.md)，并[控制设置](../../mfc/reference/control-settings-mfc-activex-control-wizard.md)使用 MFC ActiveX 控件向导。  
  
    > [!NOTE]
    >  跳过此步骤可保留向导的默认设置。  
  
4.  单击**完成**关闭向导并在开发环境中打开新项目。  
  
 在创建项目后，可以查看中创建的文件**解决方案资源管理器**。 有关向导为项目创建的文件的更多信息，请参见项目生成的文件 ReadMe.txt。 有关文件类型的详细信息，请参阅[Visual c + + 项目创建的文件类型](../../ide/file-types-created-for-visual-cpp-projects.md)。  
  
 创建项目后，可以使用代码向导添加[函数](../../ide/add-member-function-wizard.md)，[变量](../../ide/add-member-variable-wizard.md)，[事件](../../ide/add-event-wizard.md)，[属性](../../ide/names-add-property-wizard.md)，和[方法](../../ide/add-method-wizard.md)。 有关自定义 ActiveX 控件的详细信息，请参阅[MFC ActiveX 控件](../../mfc/mfc-activex-controls.md)。  
  
## <a name="see-also"></a>请参阅  
 [用代码向导添加功能](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [属性页](../../ide/property-pages-visual-cpp.md)   



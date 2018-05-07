---
title: 创建 MFC DLL 项目 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfcdll.project
dev_langs:
- C++
helpviewer_keywords:
- MFC DLLs [MFC], creating projects
- DLLs [MFC], MFC
- projects [MFC], creating
- DLLs [MFC], creating
ms.assetid: 05540b93-4781-4a90-aadf-55158313f5b2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c5c560fecdaed6ea74442596aab685a08300b3fb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="creating-an-mfc-dll-project"></a>创建 MFC DLL 项目
MFC DLL 是作为共享库的多个应用程序可同时使用的函数的二进制文件。 创建非 MFC DLL 项目的最简单方法是使用 MFC DLL 向导。  
  
> [!NOTE]
>  在 IDE 中的功能的外观可以依赖于你现用的设置或版本，并可能会与不同帮助中的描述。 若要更改设置，请在 **“工具”** 菜单上选择 **“导入和导出设置”** 。 有关详细信息，请参阅 [在 Visual Studio 中自定义开发设置](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### <a name="to-create-an-mfc-dll-project-using-the-mfc-dll-wizard"></a>若要创建 MFC DLL 项目使用 MFC DLL 向导  
  
1.  按照帮助主题中的说明[使用 Visual c + + 应用程序向导创建项目](../../ide/creating-desktop-projects-by-using-application-wizards.md)。  
  
 **请注意**中**新项目**对话框中，选择`MFC DLL`在模板窗格中，若要打开 MFC DLL 向导图标。  
  
1.  定义你使用的应用程序设置[应用程序设置](../../mfc/reference/application-settings-mfc-dll-wizard.md)页[MFC DLL 向导](../../mfc/reference/mfc-dll-wizard.md)。  
  
    > [!NOTE]
    >  跳过此步骤可保留向导的默认设置。  
  
2.  单击**完成**要关闭向导并打开新项目中的**解决方案资源管理器**。  
  
 你的项目创建后，你可以查看在解决方案资源管理器中创建的文件。 有关向导为项目创建的文件的更多信息，请参见项目生成的文件 ReadMe.txt。 有关文件类型的详细信息，请参阅[Visual c + + 项目创建的文件类型](../../ide/file-types-created-for-visual-cpp-projects.md)。  
  
## <a name="see-also"></a>请参阅  
 [Visual c + + 项目类型](/visualstudio/debugger/debugging-preparation-visual-cpp-project-types)   
 [用代码向导添加功能](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [属性页](../../ide/property-pages-visual-cpp.md)   
 [部署应用程序](http://msdn.microsoft.com/en-us/4ff8881d-0daf-47e7-bfe7-774c625031b4)


---
title: 创建 MFC DLL 项目 |Microsoft Docs
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
ms.openlocfilehash: 5fa06417b93012c7d564a45c4e58f03edf1e2a39
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43215673"
---
# <a name="creating-an-mfc-dll-project"></a>创建 MFC DLL 项目
非 MFC DLL 是作为可同时由多个应用程序的函数的共享库的二进制文件。 若要创建非 MFC DLL 项目的最简单方法是使用 MFC DLL 向导。  
  
> [!NOTE]
>  在 IDE 中的功能的外观可以取决于您现用的设置或版本，并且可能不同于帮助中所述。 若要更改设置，请在 **“工具”** 菜单上选择 **“导入和导出设置”** 。 有关详细信息，请参阅[在 Visual Studio 中自定义开发设置](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### <a name="to-create-an-mfc-dll-project-using-the-mfc-dll-wizard"></a>若要创建 MFC DLL 项目使用 MFC DLL 向导  
  
1.  请按帮助主题[使用 Visual C++ 应用程序向导创建项目](../../ide/creating-desktop-projects-by-using-application-wizards.md)中的说明进行操作。  
  
 **请注意**中**新建项目**对话框中，选择`MFC DLL`模板窗格打开 MFC DLL 向导中的图标。  
  
1.  定义使用应用程序设置[应用程序设置](../../mfc/reference/application-settings-mfc-dll-wizard.md)页[MFC DLL 向导](../../mfc/reference/mfc-dll-wizard.md)。  
  
    > [!NOTE]
    >  跳过此步骤可保留向导的默认设置。  
  
2.  单击**完成**以关闭向导并打开新项目中的**解决方案资源管理器**。  
  
 你的项目创建后，可以查看在解决方案资源管理器中创建的文件。 有关向导为项目创建的文件的更多信息，请参见项目生成的文件 ReadMe.txt。 有关文件类型的详细信息，请参阅[Visual c + + 项目创建的文件类型](../../ide/file-types-created-for-visual-cpp-projects.md)。  
  
## <a name="see-also"></a>请参阅  
 [Visual C++ 项目类型](/visualstudio/debugger/debugging-preparation-visual-cpp-project-types)   
 [用代码向导添加功能](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [属性页](../../ide/property-pages-visual-cpp.md)   
 [部署应用程序](https://msdn.microsoft.com/4ff8881d-0daf-47e7-bfe7-774c625031b4)


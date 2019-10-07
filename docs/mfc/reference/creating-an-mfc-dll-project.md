---
title: 创建 MFC DLL 项目
ms.date: 08/19/2019
f1_keywords:
- vc.appwiz.mfcdll.project
helpviewer_keywords:
- MFC DLLs [MFC], creating projects
- DLLs [MFC], MFC
- projects [MFC], creating
- DLLs [MFC], creating
ms.assetid: 05540b93-4781-4a90-aadf-55158313f5b2
ms.openlocfilehash: 649a47abea23aedb9aa97bb4923e7a800348e27e
ms.sourcegitcommit: bf1940a39029dbbd861f95480f55e5e8bd25cda0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/28/2019
ms.locfileid: "70108482"
---
# <a name="creating-an-mfc-dll-project"></a>创建 MFC DLL 项目

MFC DLL 是一个二进制文件, 它充当可由多个应用程序同时使用的共享函数库。 创建 MFC DLL 项目的最简单方法是使用 MFC DLL 向导。

> [!NOTE]
>  IDE 中的功能的外观可能取决于您的活动设置或版本, 可能与帮助中描述的不同。 若要更改设置，请在 **“工具”** 菜单上选择 **“导入和导出设置”** 。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide)。

### <a name="to-create-an-mfc-dll-project-using-the-mfc-dll-wizard"></a>使用 MFC DLL 向导创建 MFC DLL 项目

1. 按照帮助主题[创建 Mfc 应用程序](creating-an-mfc-application.md)中的说明操作, 但从可用模板列表中选择**Mfc 动态链接库**或**mfc DLL** 。

1. 使用[MFC DLL 向导](../../mfc/reference/mfc-dll-wizard.md)的 "[应用程序设置](../../mfc/reference/application-settings-mfc-dll-wizard.md)" 页定义应用程序设置。

    > [!NOTE]
    >  跳过此步骤可保留向导的默认设置。

1. 单击 "**完成**" 关闭向导并在**解决方案资源管理器**中打开新项目。

创建项目后，可以在“解决方案资源管理器”中查看创建的文件。 有关向导为项目创建的文件的更多信息，请参见项目生成的文件 ReadMe.txt。 有关文件类型的详细信息，请参阅[为 Visual Studio C++ 项目创建的文件类型](../../build/reference/file-types-created-for-visual-cpp-projects.md)。

## <a name="see-also"></a>请参阅

[Visual Studio 中的 C++ 项目类型](/visualstudio/debugger/debugging-preparation-visual-cpp-project-types)<br/>
[用代码向导添加功能](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[属性页](../../build/reference/property-pages-visual-cpp.md)


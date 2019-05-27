---
title: 创建 ATL 项目
ms.date: 05/06/2019
f1_keywords:
- vc.appwiz.ATL.project
helpviewer_keywords:
- ATL projects, creating
- ATL70.DLL
- _ATL_MIN_CRT macro
- distributing files with ATL components
ms.assetid: 061d5f98-f669-440e-9380-42f017a0f9e8
ms.openlocfilehash: 971d6c05ad4669f32e3b232d5e91c501e197be30
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707428"
---
# <a name="creating-an-atl-project"></a>创建 ATL 项目

创建 ATL 项目最简单的方法是使用位于“新建项目”对话框的“Win32 Projects”文件夹中的 ATL 项目向导。

## <a name="to-create-an-atl-project-using-the-atl-project-wizard"></a>使用 ATL 项目向导创建 ATL 项目

1. 在 Visual Studio 中，从主菜单选择“文件”>“新建”>“项目”。

1. 在“模板”窗格中选择“ATL 项目”图标以打开“ATL 项目向导”。

1. 使用“ATL 项目向导”的[应用程序设置](../../atl/reference/application-settings-atl-project-wizard.md)页面来定义你的应用程序设置。

   > [!NOTE]
   > 跳过此步骤可保留向导的默认设置。

1. 单击“完成”关闭向导并在开发环境中打开新项目。

创建项目后，可以在“解决方案资源管理器”中查看创建的文件。 有关向导为项目创建的文件的更多信息，请参见项目生成的文件 ReadMe.txt。 有关文件类型的详细信息，请参阅[为 Visual Studio C++ 项目创建的文件类型](../../build/reference/file-types-created-for-visual-cpp-projects.md)。 有关新 ATL 项目的配置以及如何更改这些配置的详细信息，请参阅[默认 ATL 项目配置](../../atl/reference/default-atl-project-configurations.md)。

## <a name="see-also"></a>请参阅

[用代码向导添加功能](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[属性页](../../build/reference/property-pages-visual-cpp.md)

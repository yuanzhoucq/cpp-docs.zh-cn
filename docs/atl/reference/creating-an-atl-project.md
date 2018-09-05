---
title: 创建 ATL 项目 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.appwiz.ATL.project
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, creating
- ATL70.DLL
- _ATL_MIN_CRT macro
- distributing files with ATL components
ms.assetid: 061d5f98-f669-440e-9380-42f017a0f9e8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4b937212f49bd09f6498ebcda934e1aa362d959e
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43755525"
---
# <a name="creating-an-atl-project"></a>创建 ATL 项目

创建 ATL 项目的最简单方法是使用 ATL 项目向导的 Win32 项目文件夹中**新项目对话框**。

### <a name="to-create-an-atl-project-using-the-atl-project-wizard"></a>若要创建使用 ATL 项目向导的 ATL 项目

1. 按照本主题中的说明[使用 Visual c + + 应用程序向导创建项目](../../ide/creating-desktop-projects-by-using-application-wizards.md)。

2. 选择**ATL 项目**模板窗格打开 ATL 项目向导中的图标。

3. 定义使用应用程序设置[应用程序设置](../../atl/reference/application-settings-atl-project-wizard.md)页`ATL Project Wizard`。

   > [!NOTE]
   > 跳过此步骤可保留向导的默认设置。

4. 单击**完成**关闭向导并在开发环境中打开新项目。

你的项目创建后，可以查看中创建的文件**解决方案资源管理器**。 有关向导为项目创建的文件的更多信息，请参见项目生成的文件 ReadMe.txt。 有关文件类型的详细信息，请参阅[Visual c + + 项目创建的文件类型](../../ide/file-types-created-for-visual-cpp-projects.md)。 有关新的 ATL 项目中，以及如何更改它们的配置详细信息，请参阅[默认 ATL 项目配置](../../atl/reference/default-atl-project-configurations.md)。

## <a name="see-also"></a>请参阅

[用代码向导添加功能](../../ide/adding-functionality-with-code-wizards-cpp.md)   
[属性页](../../ide/property-pages-visual-cpp.md)   


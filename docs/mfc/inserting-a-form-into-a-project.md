---
title: 在项目中插入窗体
ms.date: 11/04/2016
helpviewer_keywords:
- inserting forms [MFC]
- Insert New dialog box [MFC]
- forms, adding to projects
ms.assetid: f3bd2998-3ce2-496d-ac5c-57ca70eec7cb
ms.openlocfilehash: 8e3162ac3917781920130bcbed23864eb90afa59
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618433"
---
# <a name="inserting-a-form-into-a-project"></a>在项目中插入窗体

窗体为控件提供了一个方便的容器。 只要应用程序支持 MFC 库，就可以轻松地将基于 MFC 的窗体插入应用程序。

### <a name="to-insert-a-form-into-your-project"></a>在项目中插入窗体

1. 在类视图中，选择要向其添加窗体的项目，然后单击鼠标右键。

1. 在快捷菜单中，依次单击“添加”**** 和“添加类”****。

   如果 "**新建窗体**" 命令不可用，则您的项目可能基于活动模板库（ATL）。 若要将窗体添加到 ATL 项目，必须在首次创建项目时[指定某些设置](../atl/reference/application-settings-atl-project-wizard.md)。

1. 从**mfc**文件夹中单击 " **mfc 类**"。

1. 使用 MFC 类向导，使新类派生自[CFormView](reference/cformview-class.md)。

Visual C++ 将窗体添加到您的应用程序中，在对话框编辑器中打开它，以便您可以开始添加控件并处理其总体设计。

你可能需要执行以下附加步骤（不适用于基于对话框的应用程序）：

1. 重写 `OnUpdate` 成员函数。

1. 实现一个成员函数以便将数据从视图移到您的文档中。

1. 创建 `OnPrint` 成员函数。

## <a name="see-also"></a>另请参阅

[窗体视图](form-views-mfc.md)

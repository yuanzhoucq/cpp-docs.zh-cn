---
title: 一个项目中插入窗体 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inserting forms [MFC]
- Insert New dialog box [MFC]
- forms, adding to projects
ms.assetid: f3bd2998-3ce2-496d-ac5c-57ca70eec7cb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ba22c87ee601d66ccfb1092047e69be42d8163c3
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50052743"
---
# <a name="inserting-a-form-into-a-project"></a>在项目中插入窗体

窗体的控件提供一个方便的容器。 只要应用程序支持的 MFC 库，您可以轻松插入到你的应用程序的基于 MFC 的窗体。

### <a name="to-insert-a-form-into-your-project"></a>若要向项目中插入窗体

1. 从类视图中，选择你想要添加窗体，的项目并单击鼠标右键。

1. 从快捷菜单中，单击**外**，然后单击**添加类**。

   如果**新的窗体**命令不可用，你的项目可能基于活动模板库 (ATL)。 若要将窗体添加到 ATL 项目中，您必须[指定某些设置](../atl/reference/application-settings-atl-project-wizard.md)首次创建项目时。

1. 从**MFC**文件夹中，单击**的 MFC 类**。

1. 使用 MFC 类向导，使新类派生自[CFormView](../mfc/reference/cformview-class.md)。

Visual c + + 将窗体添加到应用程序中，打开对话框编辑器内，以便可以开始添加控件和处理其整体设计。

您可能想要执行以下附加步骤 （不适用于基于对话框的应用程序）：

1. 重写`OnUpdate`成员函数。

1. 实现的成员函数将数据从你的视图移到你的文档。

1. 创建`OnPrint`成员函数。

## <a name="see-also"></a>请参阅

[窗体视图](../mfc/form-views-mfc.md)


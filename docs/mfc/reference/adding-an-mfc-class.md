---
title: 添加 MFC 类
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.classes.adding.mfc
helpviewer_keywords:
- classes [MFC], adding MFC
- MFC, adding classes
ms.assetid: 9a96b67f-40bf-43d4-8872-2f8dfc5404f1
ms.openlocfilehash: f9bed3814c4489cf3850ccab97efb23caeb51730
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50640799"
---
# <a name="adding-an-mfc-class"></a>添加 MFC 类

若要添加到你的项目从 Microsoft 基础类 (MFC) 库类派生的类，请使用**添加类**中的可用命令[类视图](/visualstudio/ide/viewing-the-structure-of-code)。 指定新类的名称、 选择基类，并选择它与之关联 （如果有） 对话框中的 ID。 代码向导创建一个标头文件和实现文件，并将它们添加到你的项目。

> [!NOTE]
>  可以将 MFC 类添加到 ATL COM 应用程序中，如果您最初[创建的应用程序具有 MFC 支持](../../atl/reference/mfc-support-in-atl-projects.md)。 您还可以向具有 MFC 支持的 Win32 项目添加 MFC 类。

### <a name="to-add-an-mfc-class-to-your-project"></a>若要向项目添加 MFC 类

1. 从类视图中，右键单击项目名称。 单击**外**，然后单击**添加类**以打开[添加类](../../ide/add-class-dialog-box.md)对话框。

1. 在模板窗格中选择**MFC 类**然后按**添加**按钮。

1. 定义中的新类的设置[MFC 类向导](../../mfc/reference/mfc-add-class-wizard.md)对话框。

1. 单击**完成**以关闭向导并在类视图中查看新类。 您还可以查看由向导创建的文件**解决方案资源管理器**。

## <a name="see-also"></a>请参阅

[用代码向导添加功能](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[添加类](../../ide/adding-a-class-visual-cpp.md)<br/>
[类概述](../../mfc/class-library-overview.md)


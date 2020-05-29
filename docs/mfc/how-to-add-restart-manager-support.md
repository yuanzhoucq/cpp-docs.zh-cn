---
title: 如何：添加重新启动管理器支持
ms.date: 11/04/2016
helpviewer_keywords:
- Restart manager [MFC]
- C++, application crash support
ms.assetid: 7f3f5867-d4bc-4ba8-b3c9-dc1e7be93642
ms.openlocfilehash: 7cf3fede663a7c4bc85573e17dd9c2f8bf3622b4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373319"
---
# <a name="how-to-add-restart-manager-support"></a>如何：添加重新启动管理器支持

重新启动管理器是添加到 Windows Vista 或更高版本的操作系统的 Visual Studio 的功能。 如果发生意外关闭或重启，重新启动管理器将为你的应用程序添加支持。 重新启动管理器的行为取决于应用程序的类型。 如果你的应用程序是文档编辑器，则重新启动管理器让应用程序能够自动保存任何打开文档的状态和内容，并在意外关闭后重启应用程序。 如果你的应用程序不是文档编辑器，则重新启动管理器将重启该应用程序，但无法默认保存应用程序的状态。

重启后，如果应用程序采用 Unicode 编码，则该应用程序将显示任务对话框。 如果是 ANSI 应用程序，则该应用程序将显示 Windows 消息框。 此时，用户可以选择是否要还原自动保存的文档。 如果用户不还原自动保存的文档，则重新启动管理器将放弃临时文件。

> [!NOTE]
> 可以重写重新启动管理器保存数据和重启应用程序的默认行为。

默认情况下，在具有 Windows Vista 或更高版本的操作系统的计算机上运行应用程序时，使用 Visual Studio 中的项目向导创建的 MFC 应用程序支持重新启动管理器。 如果不希望你的应用程序支持重新启动管理器，可以在新项目向导中禁用重新启动管理器。

### <a name="to-add-support-for-the-restart-manager-to-an-existing-application"></a>向现有应用程序添加重新启动管理器支持

1. 在可视化工作室中打开现有的 MFC 应用程序。

1. 打开主应用程序的源文件。 默认情况下，这是与你的应用程序具有相同名称的 .cpp 文件。 例如，MyProject 的主应用程序源文件为 MyProject.cpp。

1. 找到主应用程序的构造函数。 例如，如果你的项目是 MyProject，则构造函数为 `CMyProjectApp::CMyProjectApp()`。

1. 将以下代码行添加到你的构造函数。

```
    m_dwRestartManagerSupportFlags = AFX_RESTART_MANAGER_SUPPORT_ALL_ASPECTS;
```

1. 请确保应用程序的 `InitInstance` 方法将调用其父 `InitInstance` 方法： [CWinApp::InitInstance](../mfc/reference/cwinapp-class.md#initinstance) 或 `CWinAppEx::InitInstance`的一项功能。 该方法`InitInstance`负责检查*m_dwRestartManagerSupportFlags*参数。

1. 编译并运行应用程序。

## <a name="see-also"></a>另请参阅

[CData恢复处理程序类](../mfc/reference/cdatarecoveryhandler-class.md)<br/>
[CWinApp：m_dwRestartManagerSupportFlags](../mfc/reference/cwinapp-class.md#m_dwrestartmanagersupportflags)<br/>
[CWinApp 类](../mfc/reference/cwinapp-class.md)<br/>
[CWinApp：m_nAutosaveInterval](../mfc/reference/cwinapp-class.md#m_nautosaveinterval)<br/>
[CDocument：：在文档事件](../mfc/reference/cdocument-class.md#ondocumentevent)

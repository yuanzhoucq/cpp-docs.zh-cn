---
title: 从 ActiveX 控件添加类 (Visual C++)
ms.date: 09/07/2018
helpviewer_keywords:
- ActiveX controls [C++], adding classes
- classes [C++], creating
ms.assetid: 729fcb37-54b8-44d5-9b4e-50bb16e0eea4
ms.openlocfilehash: c78919aeee2d2577cd7371952d95c57c17b1e5ba
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50466620"
---
# <a name="adding-a-class-from-an-activex-control-visual-c"></a>从 ActiveX 控件添加类 (Visual C++)

使用此向导从可用的 ActiveX 控件中的接口创建 MFC 类。 可以将 MFC 类添加到 [MFC 应用程序](../mfc/reference/creating-an-mfc-application.md)、[MFC DLL](../mfc/reference/creating-an-mfc-dll-project.md) 或 [MFC ActiveX 控件](../mfc/reference/creating-an-mfc-activex-control.md)。

> [!WARNING]
> 在 Visual Studio 2017 版本 15.9 中，此代码向导已弃用，并将从 Visual Studio 的将来版本中删除。 很少用到此向导。 对 ATL 和 MFC 的常规支持不会受到删除此向导的影响。 如果你想要共享对此弃用的反馈，请完成[此调查](https://www.surveymonkey.com/r/QDWKKCN)。 你的反馈对我们很重要。

> [!NOTE]
>  无需在启用自动化的情况下创建 MFC 项目，即可从 ActiveX 控件中添加类。

ActiveX 控件是基于组件对象模型 (COM) 的可重用软件组件，支持各种 OLE 功能，并且可以进行自定义来满足多种软件所需。 在普通的 ActiveX 控件容器中和万维网页面中的 Internet 上均可使用 ActiveX 控件。

### <a name="to-add-an-mfc-class-from-an-activex-control"></a>从 ActiveX 控件添加 MFC 类

1. 在“解决方案资源管理器”或“[类视图](/visualstudio/ide/viewing-the-structure-of-code)”中，右键单击要向其添加 ActiveX 控件类的项目的名称。

1. 从快捷菜单中，单击“添加”，然后单击“添加类”。

1. 在“[添加类](../ide/add-class-dialog-box.md)”对话框的“模板”窗格中，单击“ActiveX 控件中的 MFC 类”，然后单击“打开”显示“[从 ActiveX 控件向导添加类](../ide/add-class-from-activex-control-wizard.md)”。

在向导中，可以在 ActiveX 控件中添加多个接口。 同样，还可以在单个向导会话中从多个 ActiveX 控件创建类。

可以从已在系统中注册的 ActiveX 控件添加类，也可以从位于类型库文件（.tlb、.olb、.dll、.ocx 或 .exe）中的 ActiveX 控件添加类，无需提前在系统中注册。 请参阅[注册 OLE 控件](../mfc/reference/registering-ole-controls.md)，获取有关注册 ActiveX 控件的详细信息。

该向导为从所选 ActiveX 控件添加的每个接口创建 MFC 类，该类派生自 [CWnd](../mfc/reference/cwnd-class.md) 或 [COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md)。

## <a name="see-also"></a>请参阅

[MFC ActiveX 控件](../mfc/mfc-activex-controls.md)<br>
[COM 和 ATL 介绍](../atl/introduction-to-com-and-atl.md)
---
title: MFC 对象之间的关系
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, relationships between key objects
- objects [MFC], relationships
- relationships, MFC objects
- MFC object relationships
ms.assetid: 6e8f3b51-e80f-4d88-94c8-4c1e4ee163ad
ms.openlocfilehash: d7e40e25b405d3f8ec50a518889cc2b89bc8c725
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372815"
---
# <a name="relationships-among-mfc-objects"></a>MFC 对象之间的关系

为了帮助正确地对待文档/视图创建过程，请考虑正在运行的程序：文档、用于包含视图的框架窗口以及与文档关联的视图。

- 文档用于保留其视图的列表和指向创建它的文档模板的指针。

- 视图用于保留指向其文档的指针并且是其父框架窗口的子级。

- 文档框架窗口用于保留指向其当前活动视图的指针。

- 文档模板用于保留其打开的文档的列表。

- 应用程序用于保留其文档模板的列表。

- 窗口用于跟踪所有打开的窗口以便能将消息发送到这些窗口。

这些关系在文档/视图创建期间建立。 下表显示了正在运行的程序中的对象如何访问其他对象。 任何对象都可以通过调用全局函数[AfxGetApp](../mfc/reference/application-information-and-management.md#afxgetapp)获得指向应用程序对象的指针。

### <a name="gaining-access-to-other-objects-in-your-application"></a>获取对应用程序中的其他对象的访问权限

|起始对象|如何访问其他对象|
|-----------------|---------------------------------|
|Document|使用[GetFirst 查看位置](../mfc/reference/cdocument-class.md#getfirstviewposition)和[GetNextView](../mfc/reference/cdocument-class.md#getnextview)访问文档的视图列表。<br /><br /> 致电[GetDocTemplate](../mfc/reference/cdocument-class.md#getdoctemplate)获取文档模板。|
|查看|致电[GetDocument](../mfc/reference/cview-class.md#getdocument)获取文档。<br /><br /> 调用[获取父框架](../mfc/reference/cwnd-class.md#getparentframe)以获取帧窗口。|
|文档框架窗口|致电[获取活动视图](../mfc/reference/cframewnd-class.md#getactiveview)以获取当前视图。<br /><br /> 调用[GetActiveDocument](../mfc/reference/cframewnd-class.md#getactivedocument)获取文档附加到当前视图。|
|MDI 框架窗口|致电[MDIGetActive](../mfc/reference/cmdiframewnd-class.md#mdigetactive)获取当前处于活动状态的[CMDIChildwnd](../mfc/reference/cmdichildwnd-class.md)。|

通常，框架窗口包含一个视图，但在某些情况下（例如在拆分窗口中），同一框架窗口包含多个视图。 框架窗口保留指向当前处于活动状态的视图的指针；该指针在其他视图激活时更新。

> [!NOTE]
> 指向主框架窗口的指针存储在应用程序对象的[m_pMainWnd](../mfc/reference/cwinthread-class.md#m_pmainwnd)成员变量中。 在`OnFileNew``InitInstance``CWinApp`*重写集的成员*函数时，m_pMainWnd调用。 如果您未调用 `OnFileNew`，则必须自行在 `InitInstance` 中设置变量的值。 （如果 /嵌入位于命令行上，则 SDI COM 组件（服务器）应用程序可能无法设置变量。请注意 *，m_pMainWnd*现在是类`CWinThread`的成员，而不是`CWinApp`。

## <a name="see-also"></a>另请参阅

[文档模板和文档/视图创建过程](../mfc/document-templates-and-the-document-view-creation-process.md)<br/>
[文档模板创建](../mfc/document-template-creation.md)<br/>
[文档/视图创建](../mfc/document-view-creation.md)<br/>
[创建新文档、Windows 和视图](../mfc/creating-new-documents-windows-and-views.md)

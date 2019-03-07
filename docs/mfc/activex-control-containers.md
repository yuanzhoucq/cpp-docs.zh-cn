---
title: ActiveX 控件容器
ms.date: 09/12/2018
helpviewer_keywords:
- ActiveX control containers [MFC]
- OLE controls [MFC], containers
ms.assetid: 0eb1a713-e607-4c79-a0c7-67c5f1fd5fab
ms.openlocfilehash: e8340acafc81447052fcb8d90df8997e81dc4117
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57296496"
---
# <a name="activex-control-containers"></a>ActiveX 控件容器

ActiveX 控件容器是完全支持 ActiveX 控件并且可将这些控件整合到其自己的窗口或对话框中的容器。 ActiveX 控件是您可以在许多开发项目中使用的可重用软件元素。 控件允许应用程序的用户访问数据库、监视数据以及在应用程序中作出各种选择。 ActiveX 控件的详细信息，请参阅文章[MFC ActiveX 控件](../mfc/mfc-activex-controls.md)。

>[!IMPORTANT]
> ActiveX 是一项传统技术，不应使用新的开发。 有关详细信息，请参阅[ActiveX 控件](activex-controls.md)。

控件容器通常在一个项目中采用两种形式：

- 对话框和类似对话框的窗口（如窗体视图），其中将在对话框的某个位置使用 ActiveX 控件。

- 应用程序中的窗口（其中将在工具栏中使用 ActiveX 控件）或用户窗口中的其他位置。

ActiveX 控件容器与通过该控件交互公开[方法](../mfc/mfc-activex-controls-methods.md)并[属性](../mfc/mfc-activex-controls-properties.md)。 可以通过控件容器访问和修改的这些方法和属性将通过 ActiveX 控件容器项目中的包装器类进行访问。 嵌入的 ActiveX 控件还可以通过触发 （发送） 交互与容器[事件](../mfc/mfc-activex-controls-events.md)通知发生操作的容器。 控件容器可选择在收到这些通知后是否操作。

其他文章讨论了若干主题，从创建 ActiveX 控件容器项目到与使用 Visual C++ 生成的 ActiveX 控件容器有关的基础实现问题：

- [创建 MFC ActiveX 控件容器](../mfc/reference/creating-an-mfc-activex-control-container.md)

- [ActiveX 控件的容器](../mfc/containers-for-activex-controls.md)

- [ActiveX 控件容器：手动启用 ActiveX 控件包含](../mfc/activex-control-containers-manually-enabling-activex-control-containment.md)

- [ActiveX 控件容器：将控件插入控件容器应用程序](../mfc/inserting-a-control-into-a-control-container-application.md)

- [ActiveX 控件容器：将 ActiveX 控件连接到成员变量](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md)

- [ActiveX 控件容器：ActiveX 控件中处理事件](../mfc/activex-control-containers-handling-events-from-an-activex-control.md)

- [ActiveX 控件容器：查看和修改控件属性](../mfc/activex-control-containers-viewing-and-modifying-control-properties.md)

- [ActiveX 控件容器：ActiveX 控件容器中的 ActiveX 控件编程](../mfc/programming-activex-controls-in-a-activex-control-container.md)

- [ActiveX 控件容器：使用非对话框容器中的控件](../mfc/activex-control-containers-using-controls-in-a-non-dialog-container.md)

在对话框中使用 ActiveX 控件的详细信息，请参阅[对话框编辑器](../windows/dialog-editor.md)主题。

这些文章说明了使用 Visual c + + 和 MFC ActiveX 控件类开发 ActiveX 控件的详细信息的列表，请参阅[MFC ActiveX 控件](../mfc/mfc-activex-controls.md)。 文章将按功能类别进行分组。

## <a name="see-also"></a>请参阅

[MFC ActiveX 控件](../mfc/mfc-activex-controls.md)

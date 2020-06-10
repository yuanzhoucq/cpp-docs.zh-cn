---
title: ActiveX 控件容器
ms.date: 09/12/2018
helpviewer_keywords:
- ActiveX control containers [MFC]
- OLE controls [MFC], containers
ms.assetid: 0eb1a713-e607-4c79-a0c7-67c5f1fd5fab
ms.openlocfilehash: 42fa18c41ebd960aa8de080df00556ad5c909d40
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620757"
---
# <a name="activex-control-containers"></a>ActiveX 控件容器

ActiveX 控件容器是完全支持 ActiveX 控件并且可将这些控件整合到其自己的窗口或对话框中的容器。 ActiveX 控件是您可以在许多开发项目中使用的可重用软件元素。 控件允许应用程序的用户访问数据库、监视数据以及在应用程序中作出各种选择。 有关 ActiveX 控件的详细信息，请参阅[MFC ActiveX 控件](mfc-activex-controls.md)一文。

>[!IMPORTANT]
> ActiveX 是一种不能用于新开发的旧技术。 有关详细信息，请参阅[ActiveX 控件](activex-controls.md)。

控件容器通常在一个项目中采用两种形式：

- 对话框和类似对话框的窗口（如窗体视图），其中将在对话框的某个位置使用 ActiveX 控件。

- 应用程序中的窗口（其中将在工具栏中使用 ActiveX 控件）或用户窗口中的其他位置。

ActiveX 控件容器通过公开的[方法](mfc-activex-controls-methods.md)和[属性](mfc-activex-controls-properties.md)与控件进行交互。 可以通过控件容器访问和修改的这些方法和属性将通过 ActiveX 控件容器项目中的包装器类进行访问。 嵌入的 ActiveX 控件还可以通过触发（发送）[事件](mfc-activex-controls-events.md)与容器进行交互，通知容器发生了某个操作。 控件容器可选择在收到这些通知后是否操作。

其他文章讨论了若干主题，从创建 ActiveX 控件容器项目到与使用 Visual C++ 生成的 ActiveX 控件容器有关的基础实现问题：

- [创建 MFC ActiveX 控件容器](reference/creating-an-mfc-activex-control-container.md)

- [ActiveX 控件的容器](containers-for-activex-controls.md)

- [ActiveX 控件容器：手动启用 ActiveX 控件包容](activex-control-containers-manually-enabling-activex-control-containment.md)

- [ActiveX 控件容器：将控件插入控件容器应用程序](inserting-a-control-into-a-control-container-application.md)

- [ActiveX 控件容器：将 ActiveX 控件连接到成员变量](activex-control-containers-connecting-an-activex-control-to-a-member-variable.md)

- [ActiveX 控件容器：处理 ActiveX 控件中的事件](activex-control-containers-handling-events-from-an-activex-control.md)

- [ActiveX 控件容器：查看和修改控件属性](activex-control-containers-viewing-and-modifying-control-properties.md)

- [ActiveX 控件容器：对 ActiveX 控件容器中的 ActiveX 控件编程](programming-activex-controls-in-a-activex-control-container.md)

- [ActiveX 控件容器：使用非对话框容器中的控件](activex-control-containers-using-controls-in-a-non-dialog-container.md)

有关在对话框中使用 ActiveX 控件的详细信息，请参阅[对话框编辑器](../windows/dialog-editor.md)主题。

有关使用 Visual C++ 和 MFC ActiveX 控件类来说明开发 ActiveX 控件的详细信息的文章列表，请参阅[Mfc activex 控件](mfc-activex-controls.md)。 文章将按功能类别进行分组。

## <a name="see-also"></a>另请参阅

[MFC ActiveX 控件](mfc-activex-controls.md)

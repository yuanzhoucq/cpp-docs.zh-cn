---
title: ActiveX 控件容器：使用非对话框容器中的控件
ms.date: 11/04/2016
helpviewer_keywords:
- Create method [MFC], ActiveX controls
- CreateControl method [MFC]
- ActiveX controls [MFC], creating
- ActiveX control containers [MFC], non-dialog containers
- ActiveX control containers [MFC], inserting controls
ms.assetid: 46f195b0-b8ca-4409-8cca-fbfaf2c9ab9f
ms.openlocfilehash: 70a67a6952d5361177b89e3ba514d7036b5799b6
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57284237"
---
# <a name="activex-control-containers-using-controls-in-a-non-dialog-container"></a>ActiveX 控件容器：使用非对话框容器中的控件

在某些应用程序（如 SDI 或 MDI 应用程序）中，您需要将在应用程序的窗口中嵌入一个控件。 **创建**包装器类，由 Visual c + +，插入成员函数可以动态地创建控件的实例，而无需对话框。

**创建**成员函数具有以下参数：

*lpszWindowName*<br/>
指向要在控件的“Text”或“Caption”属性（如果有）中显示的文本的指针。

*dwStyle*<br/>
窗口样式。 有关完整列表，请参阅[cwnd:: Createcontrol](../mfc/reference/cwnd-class.md#createcontrol)。

*rect*<br/>
指定控件的大小和位置。

*pParentWnd*<br/>
指定控件的父窗口，通常为 `CDialog`。 不能**NULL**。

*nID*<br/>
指定控件 ID，并且可由容器用来引用控件。

使用此函数动态创建 ActiveX 控件的一个示例是在 SDI 应用程序的窗体视图中。 然后，可以在应用程序的 `WM_CREATE` 处理程序中创建控件的实例。

对于此示例，`CMyView` 是主视图类，`CCirc` 是包装器类，而 CIRC.H 是包装器类的头 (.H) 文件。

实现此功能的过程分为四个步骤。

### <a name="to-dynamically-create-an-activex-control-in-a-non-dialog-window"></a>在非对话框窗口中动态创建 ActiveX 控件

1. 在 CMYVIEW.H 中插入 CIRC.H 并刚好放置在 `CMyView` 类定义的前面：

   [!code-cpp[NVC_MFC_AxCont#12](../mfc/codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_1.h)]

1. 将一个成员变量（类型为 `CCirc`）添加到 CMYVIEW.H 中的 `CMyView` 类定义的受保护部分：

   [!code-cpp[NVC_MFC_AxCont#13](../mfc/codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_2.h)]
    [!code-cpp[NVC_MFC_AxCont#14](../mfc/codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_3.h)]

1. 将 `WM_CREATE` 消息处理程序添加到 `CMyView` 类中。

1. 在处理程序函数中， `CMyView::OnCreate`，该控件的调用`Create`函数使用**这**作为父窗口的指针：

   [!code-cpp[NVC_MFC_AxCont#15](../mfc/codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_4.cpp)]

1. 重新生成项目。 每当创建应用程序的视图时，都会动态创建一个 Circ 控件。

## <a name="see-also"></a>请参阅

[ActiveX 控件容器](../mfc/activex-control-containers.md)

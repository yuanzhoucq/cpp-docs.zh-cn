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
ms.openlocfilehash: b010c35f32462810cbdb008e5688d4b41254fad1
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620762"
---
# <a name="activex-control-containers-using-controls-in-a-non-dialog-container"></a>ActiveX 控件容器：使用非对话框容器中的控件

在某些应用程序（如 SDI 或 MDI 应用程序）中，您需要将在应用程序的窗口中嵌入一个控件。 Visual C++ 插入的包装类的**create**成员函数可以动态创建控件的实例，而无需使用对话框。

**Create**成员函数具有以下参数：

*lpszWindowName*<br/>
指向要在控件的“Text”或“Caption”属性（如果有）中显示的文本的指针。

*dwStyle*<br/>
窗口样式。 有关完整列表，请参阅[CWnd：： CreateControl](reference/cwnd-class.md#createcontrol)。

*rect*<br/>
指定控件的大小和位置。

*pParentWnd*<br/>
指定控件的父窗口，通常为 `CDialog`。 它不能为**NULL**。

*nID*<br/>
指定控件 ID，并且可由容器用来引用控件。

使用此函数动态创建 ActiveX 控件的一个示例是在 SDI 应用程序的窗体视图中。 然后，可以在应用程序的 `WM_CREATE` 处理程序中创建控件的实例。

对于此示例，`CMyView` 是主视图类，`CCirc` 是包装器类，而 CIRC.H 是包装器类的头 (.H) 文件。

实现此功能的过程分为四个步骤。

### <a name="to-dynamically-create-an-activex-control-in-a-non-dialog-window"></a>在非对话框窗口中动态创建 ActiveX 控件

1. 在 CMYVIEW.H 中插入 CIRC.H 并刚好放置在 `CMyView` 类定义的前面：

   [!code-cpp[NVC_MFC_AxCont#12](codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_1.h)]

1. 将一个成员变量（类型为 `CCirc`）添加到 CMYVIEW.H 中的 `CMyView` 类定义的受保护部分：

   [!code-cpp[NVC_MFC_AxCont#13](codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_2.h)]
    [!code-cpp[NVC_MFC_AxCont#14](codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_3.h)]

1. 将 `WM_CREATE` 消息处理程序添加到 `CMyView` 类中。

1. 在处理程序函数中， `CMyView::OnCreate` `Create` 使用**this**指针作为父窗口对控件的函数进行调用：

   [!code-cpp[NVC_MFC_AxCont#15](codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_4.cpp)]

1. 重新生成项目。 每当创建应用程序的视图时，都会动态创建一个 Circ 控件。

## <a name="see-also"></a>另请参阅

[ActiveX 控件容器](activex-control-containers.md)

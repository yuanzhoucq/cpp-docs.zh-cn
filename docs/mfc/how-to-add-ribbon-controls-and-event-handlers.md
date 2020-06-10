---
title: 如何：添加功能区控件和事件处理程序
ms.date: 11/04/2016
helpviewer_keywords:
- event handlers [MFC], adding
- ribbon controls [MFC], adding
ms.assetid: b31f25bc-ede7-49c3-9e3c-dffe4e174a69
ms.openlocfilehash: 560524c36dbf57faec3b4b6372cade047f9fe7de
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618482"
---
# <a name="how-to-add-ribbon-controls-and-event-handlers"></a>如何：添加功能区控件和事件处理程序

功能区控件是添加到面板的元素，如按钮和组合框。 面板是显示一组相关控件的功能区栏区域。

在本主题中，你将打开功能区设计器，添加一个按钮，然后链接显示 "Hello World" 的事件。

### <a name="to-open-the-ribbon-designer"></a>打开功能区设计器

1. 在 Visual Studio 的 "**视图**" 菜单上，单击 "**资源视图**"。

1. 在**资源视图**中，双击功能区资源以在设计图面上显示它。

### <a name="to-add-a-button-and-an-event-handler"></a>添加按钮和事件处理程序

1. 从**工具栏**中，单击 "**按钮**"，然后将其拖到设计图面中的一个面板上。

1. 右键单击该按钮，然后单击 "**添加事件处理程序**"。

1. 在**事件处理程序向导**中，确认默认设置，然后单击 "**添加" 和 "编辑**"。 有关详细信息，请参阅[事件处理程序向导](../ide/event-handler-wizard.md)。

1. 在代码编辑器中，将以下代码添加到处理程序函数：

```
    MessageBox((LPCTSTR)L"Hello World");
```

## <a name="see-also"></a>另请参阅

[RibbonGadgets 示例：功能区小工具应用程序](../overview/visual-cpp-samples.md)<br/>
[功能区设计器（MFC）](ribbon-designer-mfc.md)

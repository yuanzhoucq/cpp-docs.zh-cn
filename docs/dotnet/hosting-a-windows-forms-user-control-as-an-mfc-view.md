---
title: 以 MFC 视图的形式承载 Windows 窗体用户控件
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms support
- Windows Forms controls [C++], hosting as an MFC view
- hosting Windows Forms control [C++]
ms.assetid: 43c02ab4-1366-434c-a980-0b19326d6ea0
ms.openlocfilehash: bf91730f98685935d50ee0076739b436e8d9da60
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2019
ms.locfileid: "79544783"
---
# <a name="hosting-a-windows-forms-user-control-as-an-mfc-view"></a>以 MFC 视图的形式承载 Windows 窗体用户控件

MFC 使用 CWinFormsView 类在 MFC 视图中承载 Windows 窗体用户控件。 MFC Windows 窗体视图是 ActiveX 控件。 用户控件作为本机视图的子级承载，并占据本机视图的整个工作区。

最终结果类似于[CFormView 类](../mfc/reference/cformview-class.md)使用的模型。 这使您可以利用 Windows 窗体设计器和运行时来创建基于窗体的丰富视图。

因为 MFC Windows 窗体视图是 ActiveX 控件，所以它们的 `hwnd` 与 MFC 视图相同。 此外，不能将它们作为指向[CView](../mfc/reference/cview-class.md)视图的指针传递。 通常，使用 .NET Framework 方法来处理 Windows 窗体视图，并在 Win32 上依赖更少。

有关演示与 MFC 一起使用 Windows 窗体的示例应用程序，请参阅[mfc 和 Windows 窗体集成](https://www.microsoft.com/download/details.aspx?id=2113)。

## <a name="in-this-section"></a>本节内容

[如何：创建用户控件并承载 MDI 视图](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md)

[如何：向 Windows 窗体控件添加命令传送](../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)

[如何：调用 Windows 窗体控件的属性和方法](../dotnet/how-to-call-properties-and-methods-of-the-windows-forms-control.md)

## <a name="see-also"></a>另请参阅

[在 MFC 中使用 Windows 窗体用户控件](../dotnet/using-a-windows-form-user-control-in-mfc.md)<br/>
[如何：创作复合控件](/dotnet/framework/winforms/controls/how-to-author-composite-controls)

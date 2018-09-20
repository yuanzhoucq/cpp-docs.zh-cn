---
title: 承载 Windows 窗体用户控件作为 MFC 视图 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], Windows Forms support
- Windows Forms controls [C++], hosting as an MFC view
- hosting Windows Forms control [C++]
ms.assetid: 43c02ab4-1366-434c-a980-0b19326d6ea0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: b80b3a9d206ef48df1219d60afdc344874d3bab4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46374511"
---
# <a name="hosting-a-windows-forms-user-control-as-an-mfc-view"></a>以 MFC 视图的形式承载 Windows 窗体用户控件

MFC 使用 CWinFormsView 类承载 Windows 窗体用户控件在 MFC 视图中。 MFC Windows 窗体视图是 ActiveX 控件。 用户控件的本机视图子级作为托管并占据整个工作区的本机视图。

最终结果将类似于使用的模型[CFormView 类](../mfc/reference/cformview-class.md)。 这样可以充分利用 Windows 窗体设计器和运行时创建丰富的基于窗体的视图。

MFC Windows 窗体视图是 ActiveX 控件，因为它们没有相同`hwnd`作为 MFC 视图。 也不能作为指向的指针传递它们[CView](../mfc/reference/cview-class.md)视图。 一般情况下，使用.NET Framework 方法以使用 Windows 窗体视图和很少 Win32 依赖。

显示与 MFC 一起使用的 Windows 窗体的示例应用程序，请参阅[MFC 和 Windows 窗体集成](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en)。

## <a name="in-this-section"></a>本节内容

[如何：创建用户控件并承载 MDI 视图](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md)

[如何：向 Windows 窗体控件添加命令传送](../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)

[如何：调用 Windows 窗体控件的属性和方法](../dotnet/how-to-call-properties-and-methods-of-the-windows-forms-control.md)

## <a name="see-also"></a>请参阅

[在 MFC 中使用 Windows 窗体用户控件](../dotnet/using-a-windows-form-user-control-in-mfc.md)<br/>
[如何：创作复合控件](/dotnet/framework/winforms/controls/how-to-author-composite-controls)
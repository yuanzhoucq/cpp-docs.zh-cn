---
title: 在 MFC 对话框中承载 Windows 窗体用户控件
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms support
- hosting Windows Forms control [C++]
- Windows Forms [C++], MFC support
ms.assetid: 9f66ee52-b7cb-4ffd-8306-392a5da990d8
ms.openlocfilehash: 2704e04df3792edfee6c39f597fcbe71b6ce51b4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374485"
---
# <a name="hosting-a-windows-form-user-control-in-an-mfc-dialog-box"></a>在 MFC 对话框中承载 Windows 窗体用户控件

MFC 将 Windows 窗体控件托管为一种特殊的 ActiveX 控件，并使用 ActiveX 接口以及<xref:System.Windows.Forms.Control>类的属性和方法与控件通信。 我们建议您使用 .NET Framework 属性和方法对控件进行操作。

有关显示与 MFC 一起使用的 Windows 窗体的示例应用程序，请参阅[MFC 和 Windows 窗体集成](https://www.microsoft.com/download/details.aspx?id=2113)。

> [!NOTE]
> 在当前版本中，`CDialogBar`对象无法承载 Windows 窗体控件。

## <a name="in-this-section"></a>本节内容

[如何：创建用户控件并将它承载在对话框中](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)

[如何操作：使用 Windows 窗体进行 DDX/DDV 数据绑定](../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md)

[如何：接收来自本机 C++ 类的 Windows 窗体事件](../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)

## <a name="reference"></a>参考

[CWinForms 控制类](../mfc/reference/cwinformscontrol-class.md)&#124; [CDialog 类](../mfc/reference/cdialog-class.md)&#124; [Cwnd 类](../mfc/reference/cwnd-class.md)&#124;<xref:System.Windows.Forms.Control>

## <a name="see-also"></a>另请参阅

[在 MFC 中使用 Windows 窗体用户控件](../dotnet/using-a-windows-form-user-control-in-mfc.md)<br/>
[窗口窗体/MFC 编程差异](../dotnet/windows-forms-mfc-programming-differences.md)<br/>
[以 MFC 视图的形式承载 Windows 窗体用户控件](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)<br/>
[以 MFC 对话框的形式承载 Windows 窗体用户控件](../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md)

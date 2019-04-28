---
title: 在 MFC 对话框中承载 Windows 窗体用户控件
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms support
- hosting Windows Forms control [C++]
- Windows Forms [C++], MFC support
ms.assetid: 9f66ee52-b7cb-4ffd-8306-392a5da990d8
ms.openlocfilehash: 56cf00da71fe6c47e39de2a8fc06df572a301a61
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62222983"
---
# <a name="hosting-a-windows-form-user-control-in-an-mfc-dialog-box"></a>在 MFC 对话框中承载 Windows 窗体用户控件

MFC 为一种特殊的 ActiveX 控件承载 Windows 窗体控件和使用 ActiveX 接口和属性的方法与控件通信<xref:System.Windows.Forms.Control>类。 我们建议你使用.NET Framework 属性和方法来操作该控件。

显示与 MFC 一起使用的 Windows 窗体的示例应用程序，请参阅[MFC 和 Windows 窗体集成](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en)。

> [!NOTE]
>  在当前版本中，`CDialogBar`对象不能承载 Windows 窗体控件。

## <a name="in-this-section"></a>本节内容

[如何：创建用户控件并在对话框中托管](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)

[如何：执行 DDX/DDV 数据绑定与 Windows 窗体](../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md)

[如何：接收来自本机 C++ 类的 Windows 窗体事件](../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)

## <a name="reference"></a>参考

[CWinFormsControl Class](../mfc/reference/cwinformscontrol-class.md) &#124; [CDialog Class](../mfc/reference/cdialog-class.md) &#124; [CWnd Class](../mfc/reference/cwnd-class.md) &#124; <xref:System.Windows.Forms.Control>

## <a name="see-also"></a>请参阅

[在 MFC 中使用 Windows 窗体用户控件](../dotnet/using-a-windows-form-user-control-in-mfc.md)<br/>
[Windows 窗体/MFC 编程差异](../dotnet/windows-forms-mfc-programming-differences.md)<br/>
[以 MFC 视图的形式承载 Windows 窗体用户控件](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)<br/>
[以 MFC 对话框的形式承载 Windows 窗体用户控件](../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md)

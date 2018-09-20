---
title: 承载 Windows 窗体用户控件在 MFC 对话框中的 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], Windows Forms support
- hosting Windows Forms control [C++]
- Windows Forms [C++], MFC support
ms.assetid: 9f66ee52-b7cb-4ffd-8306-392a5da990d8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a1f2c042c1a4a97bc322a61cadccbd60d2a570ea
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392302"
---
# <a name="hosting-a-windows-form-user-control-in-an-mfc-dialog-box"></a>在 MFC 对话框中承载 Windows 窗体用户控件

MFC 为一种特殊的 ActiveX 控件承载 Windows 窗体控件和使用 ActiveX 接口和属性的方法与控件通信<xref:System.Windows.Forms.Control>类。 我们建议你使用.NET Framework 属性和方法来操作该控件。

显示与 MFC 一起使用的 Windows 窗体的示例应用程序，请参阅[MFC 和 Windows 窗体集成](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en)。

> [!NOTE]
>  在当前版本中，`CDialogBar`对象不能承载 Windows 窗体控件。

## <a name="in-this-section"></a>本节内容

[如何：创建用户控件并将它承载在对话框中](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)

[如何： 使用 Windows 窗体执行 DDX/DDV 数据绑定](../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md)

[如何：接收来自本机 C++ 类的 Windows 窗体事件](../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)

## <a name="reference"></a>参考

[CWinFormsControl 类](../mfc/reference/cwinformscontrol-class.md) &#124; [CDialog 类](../mfc/reference/cdialog-class.md) &#124; [CWnd 类](../mfc/reference/cwnd-class.md)&#124; <xref:System.Windows.Forms.Control>

## <a name="see-also"></a>请参阅

[在 MFC 中使用 Windows 窗体用户控件](../dotnet/using-a-windows-form-user-control-in-mfc.md)<br/>
[Windows 窗体/MFC 编程差异](../dotnet/windows-forms-mfc-programming-differences.md)<br/>
[以 MFC 视图的形式承载 Windows 窗体用户控件](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)<br/>
[以 MFC 对话框的形式承载 Windows 窗体用户控件](../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md)
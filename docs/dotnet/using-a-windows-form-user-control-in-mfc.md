---
title: 在 MFC 中使用 Windows 窗体用户控件
ms.date: 1/08/2018
helpviewer_keywords:
- MFC [C++], Windows Forms support
- interoperability [C++], Windows Forms in MFC
- interoperability [C++], MFC
- interop [C++], Windows Forms in MFC
- interop [C++], MFC
- Windows Forms [C++], MFC support
ms.assetid: 63fb099b-1dff-469c-9e34-dab52e122fcd
ms.openlocfilehash: 38c5c37712b430b137934d441056e60f2c130f78
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384486"
---
# <a name="using-a-windows-form-user-control-in-mfc"></a>在 MFC 中使用 Windows 窗体用户控件

使用 MFC Windows 窗体支持类，可以承载在 MFC 应用程序中 Windows 窗体控件作为 MFC 对话框或视图中的 ActiveX 控件。 此外，可作为 MFC 对话框承载 Windows 窗体。

以下各节介绍如何：

- 托管在 MFC 对话框中的 Windows 窗体控件。

- 作为 MFC 视图承载 Windows 窗体用户控件。

- MFC 对话框的形式承载 Windows 窗体。

> [!NOTE]
> MFC Windows 窗体集成适用于仅在动态链接 mfc 的项目中 (在其中的项目`_AFXDLL`定义)。

> [!NOTE]
> 在生成应用程序中使用的 MFC Windows 窗体界面 DLL (mfcmifc80.dll) 专用 （修改） 副本时，它将无法安装到 GAC 中，除非 Microsoft 密钥替换供应商密钥。 程序集签名的详细信息，请参阅[使用程序集编程](/dotnet/framework/app-domains/programming-with-assemblies)并[强名称程序集 （程序集签名） (C++/CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)。

如果您的 MFC 应用程序使用 Windows 窗体，您需要重新分发 mfcmifc80.dll 与你的应用程序。 有关详细信息，请参阅[重新分发 MFC 库](../windows/redistributing-the-mfc-library.md)。

## <a name="in-this-section"></a>本节内容

[在 MFC 对话框中承载 Windows 窗体用户控件](../dotnet/hosting-a-windows-form-user-control-in-an-mfc-dialog-box.md)

[以 MFC 视图的形式承载 Windows 窗体用户控件](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)

[以 MFC 对话框的形式承载 Windows 窗体用户控件](../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md)

## <a name="reference"></a>参考

[CWinFormsControl 类](../mfc/reference/cwinformscontrol-class.md)

[CWinFormsDialog 类](../mfc/reference/cwinformsdialog-class.md)

[CWinFormsView 类](../mfc/reference/cwinformsview-class.md)

[ICommandSource 接口](../mfc/reference/icommandsource-interface.md)

[ICommandTarget 接口](../mfc/reference/icommandtarget-interface.md)

[ICommandUI 接口](../mfc/reference/icommandui-interface.md)

[IView 接口](../mfc/reference/iview-interface.md)

[CommandHandler](../atl/commandhandler.md)

[DDX_ManagedControl](../mfc/reference/standard-dialog-data-exchange-routines.md#ddx_managedcontrol)

[UICheckState](../mfc/reference/uicheckstate-enumeration.md)

## <a name="related-sections"></a>相关章节

[Windows 窗体](/dotnet/framework/winforms/index)

[Windows 窗体控件](/dotnet/framework/winforms/controls/index)

## <a name="see-also"></a>请参阅

[用户界面元素](../mfc/user-interface-elements-mfc.md)<br/>
[窗体视图](../mfc/form-views-mfc.md)

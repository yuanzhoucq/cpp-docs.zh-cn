---
title: 在 MFC 中使用 Windows 窗体用户控件
ms.date: 01/08/2018
helpviewer_keywords:
- MFC [C++], Windows Forms support
- interoperability [C++], Windows Forms in MFC
- interoperability [C++], MFC
- interop [C++], Windows Forms in MFC
- interop [C++], MFC
- Windows Forms [C++], MFC support
ms.assetid: 63fb099b-1dff-469c-9e34-dab52e122fcd
ms.openlocfilehash: efabbf84778d925ec1de03f5f4ea0ca09185bd81
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "79544746"
---
# <a name="using-a-windows-form-user-control-in-mfc"></a>在 MFC 中使用 Windows 窗体用户控件

使用 MFC Windows 窗体支持类，可以在 mfc 应用程序中将 Windows 窗体控件作为 ActiveX 控件承载于 MFC 对话框或视图中。 此外，Windows 窗体窗体可以作为 MFC 对话框承载。

以下部分介绍如何执行以下操作：

- 在 MFC 对话框中承载 Windows 窗体控件。

- 将 Windows 窗体用户控件作为 MFC 视图承载。

- 将 Windows 窗体窗体作为 MFC 对话框进行托管。

> [!NOTE]
> MFC Windows 窗体集成仅适用于使用 MFC 动态链接的项目（定义了 `_AFXDLL` 的项目）。

> [!NOTE]
> 使用 MFC Windows 窗体接口 DLL （mfcmifc80.dll）的专用（已修改）副本生成应用程序时，除非将 Microsoft 密钥替换为你自己的供应商密钥，否则它将无法安装到 GAC 中。 有关程序集签名的详细信息，请参阅[通过程序集](/dotnet/framework/app-domains/programming-with-assemblies)和[强名称程序集（C++/cli）](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)进行编程。

如果 MFC 应用程序使用 Windows 窗体，则需要将 mfcmifc80.dll 与应用程序一起重新发布。 有关详细信息，请参阅重新[分发 MFC 库](../windows/redistributing-the-mfc-library.md)。

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

## <a name="see-also"></a>另请参阅

[用户界面元素](../mfc/user-interface-elements-mfc.md)<br/>
[窗体视图](../mfc/form-views-mfc.md)

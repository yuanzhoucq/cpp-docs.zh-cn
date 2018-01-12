---
title: "使用的是 Windows 中的窗体用户控件 MFC |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC [C++], Windows Forms support
- interoperability [C++], Windows Forms in MFC
- interoperability [C++], MFC
- interop [C++], Windows Forms in MFC
- interop [C++], MFC
- Windows Forms [C++], MFC support
ms.assetid: 63fb099b-1dff-469c-9e34-dab52e122fcd
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 59b4d974a6b25b896067bce0042d9a5ff9221cc2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="using-a-windows-form-user-control-in-mfc"></a>在 MFC 中使用 Windows 窗体用户控件
使用 MFC Windows 窗体支持类，可以承载 MFC 应用程序内 Windows 窗体控件作为 MFC 对话框或视图中的 ActiveX 控件。 此外，可以作为 MFC 对话框承载 Windows 窗体。  
  
 以下各节描述了如何：  
  
-   承载 Windows 窗体控件在 MFC 对话框中。  
  
-   作为 MFC 视图承载 Windows 窗体用户控件。  
  
-   作为 MFC 对话框承载 Windows 窗体。  
  
> [!NOTE]
>  MFC Windows 窗体集成仅在与 MFC 动态链接的项目中可以正常工作 （在其中定义 AFXDLL 项目）。  
  
> [!NOTE]
>  生成你的应用程序使用 MFC Windows 窗体接口 DLL (mfcmifc80.dll) 的专用 （已修改） 副本时，它将无法安装在 GAC 中，除非 Microsoft 密钥将替换为你自己供应商的密钥。 程序集签名的详细信息，请参阅[使用程序集编程](/dotnet/framework/app-domains/programming-with-assemblies)和[强名称程序集 （程序集签名） (C + + /cli CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)。  
  
 有关使用 Windows 窗体的示例应用程序，请参阅[BirthdayPicker 示例： 使用 Windows 窗体演示.NET Framework 资源](http://msdn.microsoft.com/en-us/ac932aed-5502-4667-be29-709bca435317)，[计算器示例： Windows 窗体 Pocket 计算器](http://msdn.microsoft.com/en-us/2283b516-3b7e-45f2-80c4-fdcfb366ce25)，和[Scribble 示例： MDI 绘图应用程序](http://msdn.microsoft.com/en-us/f025da3e-659b-4222-b991-554a1b8b2358)。  
  
 显示与 MFC 一起使用的 Windows 窗体的示例应用，请参阅[MFC 和 Windows 窗体集成](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en)。  
  
 如果你的 MFC 应用程序使用 Windows 窗体，需要重新分发 mfcmifc90.dll 与你的应用程序。 有关详细信息，请参阅[重新分发 MFC 库](../ide/redistributing-the-mfc-library.md)。  
  
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
 [用户界面元素](../mfc/user-interface-elements-mfc.md)   
 [窗体视图](../mfc/form-views-mfc.md)
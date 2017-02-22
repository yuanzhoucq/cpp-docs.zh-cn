---
title: "在 MFC 中使用 Windows 窗体用户控件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Windows 窗体支持的 MFC [c + +]"
  - "互操作性 [c + +] 在 MFC 中的 Windows 窗体"
  - "互操作性 [c + +] MFC"
  - "互操作 [c + +] 在 MFC 中的 Windows 窗体"
  - "互操作 [c + +] MFC"
  - "Windows 窗体 [c + +]，MFC 支持"
ms.assetid: 63fb099b-1dff-469c-9e34-dab52e122fcd
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 19
---
# 在 MFC 中使用 Windows 窗体用户控件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用 MFC Windows 窗体支持类，您可以承载 Windows 窗体控件在 MFC 应用程序作为 ActiveX 控件在 MFC 对话框或视图中。 此外，可作为 MFC 对话框承载 Windows 窗体。  
  
 以下各节描述了如何︰  
  
-   承载 Windows 窗体控件在 MFC 对话框中。  
  
-   作为 MFC 视图承载 Windows 窗体用户控件。  
  
-   作为 MFC 对话框承载 Windows 窗体。  
  
> [!NOTE]
>  MFC Windows 窗体集成可以正常工作只能在动态与 MFC 链接的项目中 （在其中定义 AFXDLL 个项目）。  
  
> [!NOTE]
>  在生成应用程序使用 MFC Windows 窗体接口 DLL (将 mfcmifc80.dll) 的专用 （已修改） 副本时，它将无法安装到 GAC 中，除非 Microsoft 密钥替换自己供应商的密钥。 程序集签名的详细信息，请参阅 [使用程序集编程](../Topic/Programming%20with%20Assemblies.md) 和 [强名称程序集 （程序集签名） (C + + /cli CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)。  
  
 有关使用 Windows 窗体的示例应用程序，请参阅 [BirthdayPicker 示例︰ 使用 Windows 窗体演示了.NET Framework 资源](http://msdn.microsoft.com/zh-cn/ac932aed-5502-4667-be29-709bca435317), ，[计算器示例︰ Windows 窗体的袖珍计算器](http://msdn.microsoft.com/zh-cn/2283b516-3b7e-45f2-80c4-fdcfb366ce25), ，和 [Scribble 示例︰ MDI 绘图应用程序](http://msdn.microsoft.com/zh-cn/f025da3e-659b-4222-b991-554a1b8b2358)。  
  
 显示 Windows 窗体与 MFC 一起使用的示例应用，请参阅 [MFC 和 Windows 窗体集成](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en)。  
  
 如果您的 MFC 应用程序使用 Windows 窗体，您需要重新分发 mfcmifc90.dll 与您的应用程序。 有关详细信息，请参阅 [重新分发 MFC 库](../ide/redistributing-the-mfc-library.md)。  
  
## <a name="in-this-section"></a>本节内容  
 [承载 Windows 窗体用户控件在 MFC 对话框](../dotnet/hosting-a-windows-form-user-control-in-an-mfc-dialog-box.md)  
  
 [作为 MFC 视图承载 Windows 窗体用户控件](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)  
  
 [以 MFC 对话框的形式承载 Windows 窗体用户控件](../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md)  
  
## <a name="reference"></a>参考  
 [CWinFormsControl 类](../mfc/reference/cwinformscontrol-class.md)  
  
 [CWinFormsDialog 类](../mfc/reference/cwinformsdialog-class.md)  
  
 [CWinFormsView 类](../mfc/reference/cwinformsview-class.md)  
  
 [ICommandSource 接口](../mfc/reference/icommandsource-interface.md)  
  
 [ICommandTarget 接口](../mfc/reference/icommandtarget-interface.md)  
  
 [ICommandUI 接口](../mfc/reference/icommandui-interface.md)  
  
 [IView 接口](../mfc/reference/iview-interface.md)  
  
 [CommandHandler](../Topic/CommandHandler%20Delegate.md)  
  
 [CommandUIHandler](../Topic/CommandUIHandler%20Delegate.md)  
  
 [DDX_ManagedControl](../Topic/DDX_ManagedControl.md)  
  
 [UICheckState](../Topic/UICheckState%20Enumeration.md)  
  
## <a name="related-sections"></a>相关章节  
 [Windows 窗体](../Topic/Windows%20Forms.md)  
  
 [Windows 窗体控件](../Topic/Windows%20Forms%20Controls.md)  
  
 [ASP.NET 用户控件](../Topic/ASP.NET%20User%20Controls.md)  
  
## <a name="see-also"></a>另请参阅  
 [用户界面元素](../mfc/user-interface-elements-mfc.md)   
 [窗体视图](../mfc/form-views-mfc.md)
---
title: "管理工具箱 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "工具箱 [Visual Studio SDK], 自动选项卡选择"
  - "工具箱 [Visual Studio SDK], 管理"
ms.assetid: 3b052047-f6db-46dd-b3bf-da1c348ee410
caps.latest.revision: 33
caps.handback.revision: 33
manager: "douge"
---
# 管理工具箱
[!INCLUDE[vsipsdk](../mfc/includes/vsipsdk_md.md)] 允许 VSPackage（如编辑器或设计器）管理“工具箱”的成员资格和外观。  
  
 此外，还可以使用自动化管理“工具箱”本身。 有关通过自动化管理工具箱的详细信息，请参阅[如何：控制工具箱](../Topic/How%20to:%20Control%20the%20Toolbox.md)。  
  
## 自动工具箱选项卡选择  
 可以基于当前处于活动状态的编辑器或设计器，自动激活特定的“工具箱”选项卡或类别。 例如，如果已激活窗体设计器，那么你可能希望选中“所有 Windows 窗体”选项卡。  
  
 此支持仅限于编辑器和设计器，并要求：  
  
1.  实现工厂对象以提供编辑器或设计器实例。 有关实现设计器或编辑器工厂对象的详细信息，请参阅[编辑器工厂](../Topic/Editor%20Factories.md)。  
  
2.  如果存在编辑器或设计器，则将自动激活工具箱选项卡的注册。  
  
## 控制工具箱  
 [!INCLUDE[vsipsdk](../mfc/includes/vsipsdk_md.md)] 提供以下接口，使 VSPackage 能够更好地控制对“工具箱”的管理方式，对自动支持进行了补充。  
  
|接口|描述|  
|--------|--------|  
|<xref:System.Drawing.Design.IToolboxService>|允许应用程序从“工具箱”中管理、添加和删除 <xref:System.Drawing.Design.ToolboxItem> 对象。 此外，还允许配置外观和“工具箱”类别。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>|允许应用程序管理、添加和删除基于活动的“工具箱”控件，以及配置“工具箱”类别和外观。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3>|通过为持久性和本地化提供全面的支持，可在 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> 中找到扩展功能。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox4>||  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox5>||  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox6>||  
  
 使用这些接口时，需要注意以下几个要点：  
  
-   <xref:System.Drawing.Design.IToolboxService> 仅适用于基于托管的包框架的 VSPackage。  
  
-   无法通过使用 <xref:System.Drawing.Design.IToolboxService> 将控件直接添加到“工具箱”。  
  
-   VSPackage 必须使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> 来添加控件或托管派生自 <xref:System.Windows.Forms.AxHost> 的包装器控件中的控件。  
  
     Visual Studio 提供了 `Aximp.exe` 工具，以自动包装派生自 <xref:System.Windows.Forms.AxHost> 的控件中的 ActiveX 控件。 有关详细信息，请参阅[Aximp.exe（Windows 窗体 ActiveX 控件导入程序）](../Topic/Aximp.exe%20\(Windows%20Forms%20ActiveX%20Control%20Importer\).md)。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox>、<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> 是基于 COM 的接口，可通过互操作程序集获得。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> 派生自 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox>，并实现其所有方法。  
  
     对象仅获取 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> 的实例。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> 不是派生自 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>，且不会实现其方法。  
  
     如果对象需要两个接口中的功能，则该对象必须从环境中获取这两个接口的实例。  
  
-   在使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> 时，有关选项卡的规范（非本地化）名称的信息由 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3.GetIDOfTab%2A> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3.SetIDOfTab%2A> 方法进行处理。  
  
-   当使用 <xref:System.Drawing.Design.IToolboxService> 时，由实现者管理本地化信息，如类别的名称。  
  
 使用设置机制以允许用户保存“工具箱”设置，用户可以通过 IDE 的“工具”菜单上的“导入\/导出设置”命令访问这些设置。 有关如何使用设置的详细信息，请参阅[扩展的用户设置和选项](../Topic/Extending%20User%20Settings%20and%20Options.md)。  
  
## 请参阅  
 [扩展工具箱](../misc/extending-the-toolbox.md)
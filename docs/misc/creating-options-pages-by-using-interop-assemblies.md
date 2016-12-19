---
title: "使用互操作程序集创建选项页 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "工具选项页 [Visual Studio SDK]，使用互操作程序集创建"
  - "互操作程序集，创建工具选项页"
ms.assetid: 7a03f2f5-a53e-4a46-877f-5b10dd82dbc3
caps.latest.revision: 30
caps.handback.revision: 30
manager: "douge"
---
# 使用互操作程序集创建选项页
托管的 VSPackage 可以使用 [!INCLUDE[vsipsdk](../mfc/includes/vsipsdk_md.md)] 的基于 COM 的互操作程序集通过将“选项”页添加到“工具”菜单来扩展 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 集成开发环境 \(IDE\)。  
  
 从根本上而言，“工具选项”页是一个用户控件，因此可以采用与任何其他用户控件相同的方式进行编码。 通常情况下，可以使用其中一种 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] IDE 的设计器来创建对象和添加用户控件。  
  
> [!NOTE]
>  作为一个对话框（使用 DialogProc 处理窗口消息）实现的“工具选项”页必须是一个无模式对话框，且不能调用 EndDialog 函数。  
  
 应使用 VSPackage 提供给环境用以支持用户控件显示的属性的自动化对象。  
  
 实现“工具选项”页的 VSPackage 可以直接或通过 IDE 的自动化模型支持其属性的编程控件。 有关通过自动化支持“工具选项”页的详细信息，请参阅[使用自动化创建选项页](../misc/creating-options-pages-by-using-automation.md)。  
  
## 使“工具选项”页对 IDE 可用  
 除了实现用户控件，VSPackage 还必须使该控件对 IDE 可用。  
  
 为此，可通过实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> 方法完成，该方法基于传递的 GUID 将返回一个 <xref:Microsoft.VisualStudio.Shell.Interop.VSPROPSHEETPAGE> 结构。  
  
 IDE 使用 <xref:Microsoft.VisualStudio.Shell.Interop.VSPROPSHEETPAGE> 结构设置“属性”页的特性。  
  
 包含在其 `dwFlags` 成员中的设置确定 <xref:Microsoft.VisualStudio.Shell.Interop.VSPROPSHEETPAGE> 其他成员的确切解释。 该结构通常提供以下内容：  
  
-   要从其中加载图标或字符串资源的实例的句柄。  
  
-   页面对话框模板的资源标识符。  
  
-   指向该页面 DialogProc 的指针。  
  
## 注册“工具选项”页  
 可通过在以下注册表位置创建条目注册“工具选项”页：HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\<Version\>*\\ToolsOptionsPages，其中 *\<Version\>* 是 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 的版本，例如 8.0。  
  
 要注册该页面，你可以手动编辑注册表或使用注册表脚本 \(.rgs file\)。 有关更多信息，请参见[Creating Registrar Scripts](../atl/creating-registrar-scripts.md)。  
  
## 请参阅  
 [扩展 Visual Studio 环境](../Topic/Extending%20the%20Visual%20Studio%20Environment.md)   
 [Creating Registrar Scripts](../atl/creating-registrar-scripts.md)   
 [选项页的自动化支持](../Topic/Automation%20Support%20for%20Options%20Pages.md)   
 [使用选项页](../misc/using-options-pages.md)   
 [创建选项页](../Topic/Creating%20Options%20Pages.md)   
 [使用自动化创建选项页](../misc/creating-options-pages-by-using-automation.md)
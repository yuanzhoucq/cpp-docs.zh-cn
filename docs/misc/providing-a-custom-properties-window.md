---
title: "提供自定义属性窗口 | Microsoft Docs"
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
  - "属性浏览器, 提供"
  - "属性窗口, 提供自定义"
ms.assetid: 408dcdef-8ef9-4644-97d2-f311cd35824f
caps.latest.revision: 12
caps.handback.revision: 12
manager: "douge"
---
# 提供自定义属性窗口
针对给定项目系统提供您的 **属性** 窗口是可能的，而不是扩展 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 集成开发环境提供的 **属性** 窗口 \(IDE\)。  该 most\-often 遇到的情况是您您实现对象在窗架已经放置。  
  
 在事件不实现在窗架站点的对象，但是，使用其他一些方法仍可以使用它的，有许多方法可以访问 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> 接口 \(在此页上的最后程序列表中。  
  
### 提供自己的 " 属性 " 窗口  
  
1.  定义表示您的 **属性** 窗口实现的 GUID。  
  
2.  在您的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> 实现中，使用 <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> 服务提供您的 **属性** 窗口作为服务到 Visual Studio 环境。  
  
### 调用您的 " 属性 " 窗口  
  
1.  调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane.SetSite%2A> 方法。  
  
2.  <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> 的`QueryService` 从 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> 传递到 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane.SetSite%2A> 方法。  
  
3.  获取从 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> 服务的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> 。  
  
4.  调用与第一个参数的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A> 设置为 `SEID_PropertyBrowserSID` \(来自 <xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID> 枚举\) 和第三个参数， `varValue`，表示表示您的 **属性** 窗口的 GUID 的字符串形式。  使此调用您的 **属性** 窗口的第一个创建一次只文档窗口。  在调用之后此 **属性** 窗口与您的窗架。  
  
### 获取窗架对象，而不是实现  
  
-   可以 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> 服务的 `QueryService` 从与参数 `propid` 的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> 设置为 <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>。  
  
-   可以获取活动通过调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> 文档窗口通过 SVsMonitorSelection 服务。  将参数 `elementid` 到 `SEID_WindowFrame`，将 <xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID> 枚举。  
  
## 请参阅  
 [将属性扩展](../Topic/Extending%20Properties.md)   
 [属性窗口字段和接口](../Topic/Properties%20Window%20Fields%20and%20Interfaces.md)
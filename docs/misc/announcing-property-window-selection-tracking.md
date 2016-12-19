---
title: "宣布属性窗口选定内容跟踪 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "编辑器 [Visual Studio SDK], 属性页支持"
  - "属性页, 跟踪选定内容"
  - "属性窗口, 跟踪选定内容"
  - "选定内容, 跟踪"
  - "编辑器 [Visual Studio SDK], 属性窗口支持"
ms.assetid: a7536f82-afd7-4894-9a60-84307fb92b7e
caps.latest.revision: 13
caps.handback.revision: 13
manager: "douge"
---
# 宣布属性窗口选定内容跟踪
如果您要使用 **属性** 窗口时使用或 **属性** 页，例如，窗体，文本，或者一个选择要查看的属性，则必须具有完全知道如何协调选择。  例如，必须知道是否具有唯一选择或多个选择。  然后需要以选择类型 \(一个或多个\) 使用 <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> 接口，到 IDE 中。  此接口提供 **属性** 窗口需要的信息。  
  
### 要选择到环境  
  
1.  调用 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>的 `QueryInterface` 。  
  
    1.  ，在创建了，为此，请使用站点指针传递给视图。  
  
    2.  调用从视图中 `QueryService``SID_STrackSelection` services。  
  
         这将返回指向 <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>。  
  
2.  调用 <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> 方法中，选择每次更改，并通过指向对象实现 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>。  
  
     选择容器对象可以使用一个或多个选定内容并在 `IDispatch` 对象包含选择信息。  调用 <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> 方法通知 **属性** 窗口选定内容已经更改。  **属性** 窗口然后使用在 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 的对象确定一个或多个选择是否发生的事件，，以及实际对象选择为。  
  
     如果指定一个多重选择，则 **属性** " 窗口查找在公共属性之间的交集对象的。  如果指定单个对象选择，然后 **属性** 窗口显示所有对象的属性。  
  
## 请参阅  
 [将属性扩展](../Topic/Extending%20Properties.md)   
 [属性页](../Topic/Property%20Pages.md)
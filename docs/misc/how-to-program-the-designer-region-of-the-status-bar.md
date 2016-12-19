---
title: "如何：对状态栏的设计器区域进行编程 | Microsoft Docs"
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
  - "设计器区域, 状态栏"
  - "状态栏, 编程"
  - "状态栏, 设计器区域"
ms.assetid: 735a86bb-80b2-4557-9677-00799856017f
caps.latest.revision: 11
caps.handback.revision: 11
manager: "douge"
---
# 如何：对状态栏的设计器区域进行编程
[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 状态栏的设计器区域显示与编辑器，如，行号或光标位置的列数的信息。  
  
### 对程序 Visual Studio 状态栏的设计器区域  
  
1.  获取 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> 接口的实例，能通过 <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> 服务。  
  
2.  通过调用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.SetInsMode%2A> 方法和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> 实例的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.SetLineColChar%2A> 方法更新状态栏的设计器区域。  
  
## 示例  
 此示例演示如何处理程序演示状态栏的设计器区域。  
  
 [!code-vb[VSSDKDesignerStatusBar#1](../misc/codesnippet/VisualBasic/how-to-program-the-designer-region-of-the-status-bar_1.vb)]
 [!code-cs[VSSDKDesignerStatusBar#1](../misc/codesnippet/CSharp/how-to-program-the-designer-region-of-the-status-bar_1.cs)]  
  
## 请参阅  
 [扩展状态栏](../Topic/Extending%20the%20Status%20Bar.md)   
 [如何：读取和写入到“状态栏”的“反馈区域”](../misc/how-to-read-from-and-write-to-the-feedback-region-of-the-status-bar.md)   
 [如何：对状态栏的进度栏区域进行编程](../misc/how-to-program-the-progress-bar-region-of-the-status-bar.md)   
 [如何：使用状态栏的动画区域](../misc/how-to-use-the-animation-region-of-the-status-bar.md)
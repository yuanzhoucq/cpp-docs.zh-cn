---
title: "以 MFC 视图的形式承载 Windows 窗体用户控件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "承载 Windows 窗体控件 [C++]"
  - "MFC [C++], Windows 窗体支持"
  - "Windows 窗体控件 [C++], 作为 MFC 视图承载"
ms.assetid: 43c02ab4-1366-434c-a980-0b19326d6ea0
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 以 MFC 视图的形式承载 Windows 窗体用户控件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 使用 CWinFormsView 类来在 MFC 视图中承载 Windows 窗体用户控件。  MFC Windows 窗体视图是 ActiveX 控件。  用户控件以本机视图的子视图的形式承载并且占用本机视图的整个工作区。  
  
 最终结果与 [CFormView Class](../mfc/reference/cformview-class.md) 使用的模型相似。  这使您可以利用 Windows 窗体设计器和运行时来创建多样的基于窗体的视图。  
  
 因为 MFC Windows 窗体视图是 ActiveX 控件，所以不像 MFC 视图那样具有 `hwnd`。  另外它们不能作为指针传递到 [CView](../mfc/reference/cview-class.md) 视图。  通常，应使用 .NET Framework 方法处理 Windows 窗体视图而少依赖 Win32。  
  
 有关能够显示与 MFC 一起使用的 Windows 窗体的示例应用程序信息，请参阅 [MFC 与 Windows 窗体集成](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en)。  
  
## 本节内容  
 [如何：创建用户控件并承载 MDI 视图](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md)  
  
 [如何：向 Windows 窗体控件添加命令传送](../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)  
  
 [如何：调用 Windows 窗体控件的属性和方法](../dotnet/how-to-call-properties-and-methods-of-the-windows-forms-control.md)  
  
## 请参阅  
 [在 MFC 中使用 Windows 窗体用户控件](../dotnet/using-a-windows-form-user-control-in-mfc.md)   
 [如何：创作复合控件](../Topic/How%20to:%20Author%20Composite%20Controls.md)
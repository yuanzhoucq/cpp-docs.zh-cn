---
title: "承载 Windows 窗体用户控件作为 MFC 视图 |Microsoft 文档"
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
- Windows Forms controls [C++], hosting as an MFC view
- hosting Windows Forms control [C++]
ms.assetid: 43c02ab4-1366-434c-a980-0b19326d6ea0
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 7e4e0b7bc081d3b16b3f9aa55719d298f710cdab
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="hosting-a-windows-forms-user-control-as-an-mfc-view"></a>以 MFC 视图的形式承载 Windows 窗体用户控件
MFC 使用 CWinFormsView 类承载 Windows 窗体用户控件在 MFC 视图。 MFC Windows 窗体视图是 ActiveX 控件。 用户控件的本机视图子级作为托管且占用整个工作区的本机视图。  
  
 最终结果将类似于使用的模型[CFormView 类](../mfc/reference/cformview-class.md)。 这使你充分利用 Windows 窗体设计器和运行时创建丰富的基于窗体的视图。  
  
 MFC Windows 窗体视图是 ActiveX 控件，因为他们没有相同`hwnd`作为 MFC 视图。 也不能将它们传递作为指向的[CView](../mfc/reference/cview-class.md)视图。 一般情况下，使用.NET Framework 方法来使用 Windows 窗体视图和很少 Win32 依赖。  
  
 显示与 MFC 一起使用的 Windows 窗体的示例应用，请参阅[MFC 和 Windows 窗体集成](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en)。  
  
## <a name="in-this-section"></a>本节内容  
 [如何：创建用户控件并承载 MDI 视图](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md)  
  
 [如何：向 Windows 窗体控件添加命令传送](../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)  
  
 [如何：调用 Windows 窗体控件的属性和方法](../dotnet/how-to-call-properties-and-methods-of-the-windows-forms-control.md)  
  
## <a name="see-also"></a>请参阅  
 [在 MFC 中使用 Windows 窗体用户控件](../dotnet/using-a-windows-form-user-control-in-mfc.md)   
 [如何：创作复合控件](/dotnet/framework/winforms/controls/how-to-author-composite-controls)
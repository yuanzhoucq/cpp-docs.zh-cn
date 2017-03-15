---
title: "在 MFC 对话框中承载 Windows 窗体用户控件 | Microsoft Docs"
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
  - "承载 Windows 窗体控件 [C++]"
  - "MFC [C++], Windows 窗体支持"
  - "Windows 窗体 [C++], MFC 支持"
ms.assetid: 9f66ee52-b7cb-4ffd-8306-392a5da990d8
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# 在 MFC 对话框中承载 Windows 窗体用户控件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 将 Windows 窗体控件作为一种特殊类型的 ActiveX 控件来承载，并使用 ActiveX 接口以及 <xref:System.Windows.Forms.Control> 类的属性和方法与该控件进行通信。  建议您使用 .NET Framework 属性和方法来操作该控件。  
  
 有关能够显示与 MFC 一起使用的 Windows 窗体的示例应用程序信息，请参阅 [MFC 与 Windows 窗体集成](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en)。  
  
> [!NOTE]
>  在当前的版本中，`CDialogBar`  对象不能承载 Windows 窗体控件。  
  
## 本节内容  
 [如何：创建用户控件并将它承载在对话框中](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)  
  
 [如何：使用 Windows 窗体执行 DDX\/DDV 数据绑定](../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md)  
  
 [如何：接收来自本机 C\+\+ 类的 Windows 窗体事件](../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)  
  
## 参考  
 [CWinFormsControl Class](../mfc/reference/cwinformscontrol-class.md) &#124; [CDialog Class](../mfc/reference/cdialog-class.md) &#124; [CWnd 类](../mfc/reference/cwnd-class.md) &#124; <xref:System.Windows.Forms.Control>  
  
## 请参阅  
 [在 MFC 中使用 Windows 窗体用户控件](../dotnet/using-a-windows-form-user-control-in-mfc.md)   
 [Windows 窗体\/MFC 编程差异](../dotnet/windows-forms-mfc-programming-differences.md)   
 [以 MFC 视图的形式承载 Windows 窗体用户控件](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)   
 [以 MFC 对话框的形式承载 Windows 窗体用户控件](../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md)
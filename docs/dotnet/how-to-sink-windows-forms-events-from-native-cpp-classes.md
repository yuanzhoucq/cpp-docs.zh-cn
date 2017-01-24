---
title: "如何：接收来自本机 C++ 类的 Windows 窗体事件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "事件处理, .NET/本机互操作"
  - "事件处理, 托管/本机互操作"
  - "事件处理, 在 C++ 中接收 .NET"
  - "事件处理, C++ 中的 Windows 窗体"
ms.assetid: 6e30ddee-d058-4c8d-9956-2a43d86f19d5
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：接收来自本机 C++ 类的 Windows 窗体事件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以启用本机 C\+\+ 类从 Windows 窗体控件或其他具有 MFC 宏映射格式的窗体所引发的托管事件中接收回调。  接收视图和对话框中的事件类似于接收控件中的事件。  
  
 为此，必须：  
  
-   使用 [MAKE\_DELEGATE](../Topic/MAKE_DELEGATE.md) 将 `OnClick` 事件处理程序附加到该控件。  
  
-   使用 [BEGIN\_DELEGATE\_MAP](../Topic/BEGIN_DELEGATE_MAP.md)、[END\_DELEGATE\_MAP](../Topic/END_DELEGATE_MAP.md) 和 [EVENT\_DELEGATE\_ENTRY](../Topic/EVENT_DELEGATE_ENTRY.md) 创建委托映射。  
  
 此示例继续执行您在[如何：使用 Windows 窗体执行 DDX\/DDV 数据绑定](../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md) 中完成的工作。  
  
 现在，将 MFC 控件 \(`m_MyControl`\) 与托管 <xref:System.Windows.Forms.Control.Click> 事件的名为 `OnClick` 的托管事件处理程序委托相关联。  
  
### 附加 OnClick 事件处理程序：  
  
1.  将以下代码添加到 BOOL CMFC01Dlg::OnInitDialog 的实现中：  
  
    ```  
    m_MyControl.GetControl()->button1->Click += MAKE_DELEGATE( System::EventHandler, OnClick );  
    ```  
  
2.  将以下代码添加到 CMFC01Dlg : public CDialog 类声明的 public 节中。  
  
    ```  
    // delegate map  
    BEGIN_DELEGATE_MAP( CMFC01Dlg )  
    EVENT_DELEGATE_ENTRY( OnClick, System::Object^, System::EventArgs^ )  
    END_DELEGATE_MAP()  
  
    void OnClick( System::Object^ sender, System::EventArgs^ e );  
    ```  
  
3.  最后，将 `OnClick` 的实现添加到 CMFC01Dlg.cpp 中：  
  
    ```  
    void CMFC01Dlg::OnClick(System::Object^ sender, System::EventArgs^ e)  
    {  
        AfxMessageBox(_T("Button clicked"));  
    }  
    ```  
  
## 请参阅  
 [MAKE\_DELEGATE](../Topic/MAKE_DELEGATE.md)   
 [BEGIN\_DELEGATE\_MAP](../Topic/BEGIN_DELEGATE_MAP.md)   
 [END\_DELEGATE\_MAP](../Topic/END_DELEGATE_MAP.md)   
 [EVENT\_DELEGATE\_ENTRY](../Topic/EVENT_DELEGATE_ENTRY.md)
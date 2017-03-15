---
title: "ActiveX 控件容器：使用非对话框容器中的控件 | Microsoft Docs"
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
  - "ActiveX 控件容器 [C++], 插入控件"
  - "ActiveX 控件容器 [C++], 非对话框容器"
  - "ActiveX 控件 [C++], 创建"
  - "Create 方法 [C++], ActiveX 控件"
  - "CreateControl 方法"
ms.assetid: 46f195b0-b8ca-4409-8cca-fbfaf2c9ab9f
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# ActiveX 控件容器：使用非对话框容器中的控件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在某些应用程序中，例如 SDI 或 MDI 应用程序中，您将希望将在应用程序的窗口嵌入控件。  包装类的 **创建** 成员函数，由 Visual C\+\+ 插入，可动态创建控件的实例，而不需要对话框。  
  
 **创建** 成员函数有下列参数：  
  
 `lpszWindowName`  
 指向要在控件的文本或标题属性中显示的文本的指针 \(如果有\)。  
  
 `dwStyle`  
 窗口样式  有关更完整的列表，请参见 [CWnd::CreateControl](../Topic/CWnd::CreateControl.md).  
  
 `rect`  
 指定控件的大小和位置。  
  
 `pParentWnd`  
 指定控件的父窗口，通常为 `CDialog`。  它不得为 **NULL**。  
  
 `nID`  
 指定控件 ID，并且可以由容器使用引用控件。  
  
 使用此函数动态创建 ActiveX 控件的一个示例为 SDI 应用程序中的窗体视图。  然后可以创建控件的实例在应用程序的 `WM_CREATE` 处理程序中。  
  
 对于此示例，`CMyView` 是主视图类，`CCirc` 是包装类，而 CIRC.H 是包装类的头 \(.H\) 文件。  
  
 实现此功能是一个四步过程。  
  
### 在非对话框窗口中动态创建 ActiveX 控件  
  
1.  在 CMYVIEW.H 中插入 CIRC.H，置于 `CMyView` 类定义的前面：  
  
     [!code-cpp[NVC_MFC_AxCont#12](../mfc/codesnippet/CPP/activex-control-containers-using-controls-in-a-non-dialog-container_1.h)]  
  
2.  添加成员变量 \(类型为 `CCirc`\) 到 CMYVIEW.H 中的 `CMyView` 类定义的受保护部分：  
  
     [!code-cpp[NVC_MFC_AxCont#13](../mfc/codesnippet/CPP/activex-control-containers-using-controls-in-a-non-dialog-container_2.h)]  
    [!code-cpp[NVC_MFC_AxCont#14](../mfc/codesnippet/CPP/activex-control-containers-using-controls-in-a-non-dialog-container_3.h)]  
  
3.  为 `CMyView` 类添加 `WM_CREATE` 消息处理程序。  
  
4.  在处理程序函数中，即 `CMyView::OnCreate`，调用控件的 `Create` 函数使用 **this** 指针作为父窗口：  
  
     [!code-cpp[NVC_MFC_AxCont#15](../mfc/codesnippet/CPP/activex-control-containers-using-controls-in-a-non-dialog-container_4.cpp)]  
  
5.  重新生成项目。  Circ 控件将被动态创建，每当应用程序的视图被创建时。  
  
## 请参阅  
 [ActiveX 控件容器](../mfc/activex-control-containers.md)
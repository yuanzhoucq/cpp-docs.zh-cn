---
title: "从对话框对象检索数据 | Microsoft Docs"
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
  - "捕获用户输入"
  - "数据 [MFC], 对话框"
  - "数据 [MFC], 检索"
  - "数据检索 [C++], 对话框"
  - "DDX（对话框数据交换）[C++]"
  - "DDX（对话框数据交换）[C++], 关于 DDX"
  - "DDX（对话框数据交换）[C++], 从 Dialog 对象检索数据"
  - "对话框控件 [C++], 初始化值"
  - "对话框数据 [C++]"
  - "对话框数据 [C++], 检索"
  - "对话框 [C++], 检索用户数据"
  - "GetDlgItemText 方法"
  - "GetWindowText 方法"
  - "MFC 对话框, 检索用户输入"
  - "检索数据"
  - "SetDlgItemText 方法"
  - "SetWindowText 方法"
  - "用户输入 [C++], 从 MFC 对话框检索"
ms.assetid: bdca2b61-6b53-4c2e-b426-8712c7a38ec0
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 从对话框对象检索数据
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

框架提供一种简便方法初始化值在对话框的控件并从控件中检索值。  更费力的方法手动将调用函数 \(例如\) 的 `CWnd`类的 `SetDlgItemText` 和 `GetDlgItemText` 成员函数，应用于控件窗口。  这些函数，可以逐个访问的每个控件以设置或获取值，调用函数 \(如 `SetWindowText` 和 `GetWindowText`\)。  框架的方法自动初始化和检索。  
  
 对话框数据交换 \(DDX\) 可以在对话框中的变量对象轻松的控件在对话框和成员之间交换数据。  此交换工作这两种方式。  若要初始化在对话框的控制，可以设置对话框值对象的数据成员，并且，则框架将值传递到控件，将在显示对话框之前。  然后您可以随时更新具有用户输入的数据的对话框数据成员。  此时，通过指数据成员变量使用数据。  
  
 可以对值将自动验证的对话框控件还具有使用对话框数据验证 \(DDV\)。  
  
 DDX 和 DDV 在 [对话框数据交换和验证](../mfc/dialog-data-exchange-and-validation.md)更详细说明。  
  
 对于模式对话框，因此，当销毁时，可以检索所有数据，但用户输入对话框在对象之前的 `DoModal` 返回 **IDOK**。  对于无模式对话框，可以随时从对话框对象检索数据通过调用带有参数 **TRUE** 的 `UpdateData` 和访问对话框类成员变量。  此主题中 [对话框数据交换和验证](../mfc/dialog-data-exchange-and-validation.md)更详细的讨论。  
  
## 请参阅  
 [对话框的生命周期](../mfc/life-cycle-of-a-dialog-box.md)
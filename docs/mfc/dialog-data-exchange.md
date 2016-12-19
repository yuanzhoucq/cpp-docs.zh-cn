---
title: "对话框数据交换 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "取消数据交换"
  - "捕获用户输入"
  - "CDataExchange 类, 使用 DDX"
  - "对话框数据交换 (DDX), 取消"
  - "对话框数据交换 (DDX), 数据交换机制"
  - "对话框数据"
  - "对话框数据, 检索"
  - "对话框, 数据交换"
  - "对话框, 初始化"
  - "对话框, 使用 DDX 检索用户输入"
  - "DoDataExchange 方法"
  - "初始化对话框"
  - "检索对话框数据"
  - "传输对话框数据"
  - "UpdateData 方法"
  - "用户输入, 从 MFC 对话框检索"
ms.assetid: 4675f63b-41d2-45ed-b6c3-235ad8ab924b
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 对话框数据交换
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果使用 DDX 机制，可设置对话框对象的成员变量的初始值，通常在 `OnInitDialog` 处理程序或此对话框构造函数中。  在立即显示对话框之前，框架的 DDX 机制转移成员变量的值到对话框的控件，在对话框中，当对话框自己响应 `DoModal` 或 **创建** 时出现在它们出现的位置。  `CDialog` 中的 `OnInitDialog` 的默认实现调用  `CWnd` 类的 `UpdateData` 成员函数初始化在对话框中的控件。  
  
 当用户单击 OK 按钮时，从空间到成员变量的值得转移机制是相同的\(或者，每次调用 `UpdateData` 成员函数时，使用的参数为 **TRUE**\) 。  对话框数据验证机制验证指定验证规则的所有数据项。  
  
 下图演示对话框数据交换。  
  
 ![对话框数据交换](../mfc/media/vc379d1.png "vc379D1")  
对话框数据交换  
  
 `UpdateData` 在两个方向运行，根据传递给它的 **BOOL** 参数。  若要执行交换， `UpdateData` 设置 `CDataExchange` 对象并调用对话框类 `CDialog` 的 `DoDataExchange` 成员函数的重写。  `DoDataExchange` 采用 `CDataExchange` 类型的参数。  `CDataExchange` 对象将传递到 `UpdateData` 表示上下文交换，如交换指示的一样定义此类信息。  
  
 当您 \(或代码向导\) 重写 `DoDataExchange` 时，可以指定每个数据成员 \(控件\) 调用一个 DDX 功能。  每 DDX 幻术知道如何根据通过 `UpdateData` 传递 `CDataExchange` 参数到 `DoDataExchange` 的上下文中双向交换数据。  
  
 MFC 提供许多 DDX 函数用于不同类型的交换。  下面的示例演示两 DDX 函数和一 DDV 函数调用的 `DoDataExchange` 重写：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#49](../mfc/codesnippet/CPP/dialog-data-exchange_1.cpp)]  
  
 `DDX_` 和 `DDV_` 行是数据映射。  示例显示的 DDX 和 DDV 函数分别为复选框控件和编辑框控件。  
  
 如果用户取消模式对话框，`OnCancel` 成员函数终止对话框，同时 `DoModal` 返回 **IDCANCEL** 值。  在这种情况下，在对话框和对话框对象之间没有数据交换。  
  
## 请参阅  
 [对话框数据交换和验证](../mfc/dialog-data-exchange-and-validation.md)   
 [对话框的生命周期](../mfc/life-cycle-of-a-dialog-box.md)   
 [对话框数据验证](../mfc/dialog-data-validation.md)
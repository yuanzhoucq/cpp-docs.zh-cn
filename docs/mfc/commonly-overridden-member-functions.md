---
title: "经常重写的成员函数 | Microsoft Docs"
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
  - "CDialog 类, 成员"
  - "对话框类, 经常重写的成员函数"
  - "MFC 对话框, 重写成员函数"
  - "OnCancel 函数"
  - "OnInitDialog 函数"
  - "OnOK 函数"
  - "重写, 对话框类成员"
ms.assetid: 78eb566c-e361-4c86-8db5-c7e2791b249a
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 经常重写的成员函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下表列出在 `CDialog`派生类可能重写成员函数。  
  
### 通常 CDialog 类重写的成员函数  
  
|成员函数|该响应的信息|重载的用途。|  
|----------|------------|------------|  
|`OnInitDialog`|**WM\_INITDIALOG**|初始化对话框的控件。|  
|`OnOK`|按钮的 **IDOKBN\_CLICKED**|当用户单击"确定"按钮，则响应。|  
|`OnCancel`|按钮的 **IDCANCELBN\_CLICKED**|当用户单击"取消"按钮，则响应。|  
  
 `OnInitDialog`、`OnOK`和 `OnCancel` 都是虚函数。  使用 [属性窗口](../Topic/Properties%20Window.md)，若要重写，也声明在派生的对话框类中的重写函数。  
  
 在显示对话框之前，将调用`OnInitDialog`。  必须调用从重写的默认 `OnInitDialog` \(通常在处理程序作为处理程序的第一个操作。  默认情况下，`OnInitDialog` 将返回 **TRUE** 指示应设置为焦点在对话框第一个控件。  
  
 `OnOK` 不为非模式，而不是模式对话框通常重写。  如果重写模式对话框的此处理程序中，调用该重写 \- 确保调用 `EndDialog` \) 或调用 `EndDialog` 的基类版本。  
  
 `OnCancel` 用于非模式对话框通常重写。  
  
 有关这些成员函数的更多信息，请参见类 [CDialog](../mfc/reference/cdialog-class.md) " *MFC 参考* 和讨论有关中 [对话框的生命周期](../mfc/life-cycle-of-a-dialog-box.md)。  
  
## 请参阅  
 [对话框](../mfc/dialog-boxes.md)   
 [经常添加的成员函数](../mfc/commonly-added-member-functions.md)
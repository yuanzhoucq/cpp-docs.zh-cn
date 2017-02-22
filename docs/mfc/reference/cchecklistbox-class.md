---
title: "CCheckListBox Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CCheckListBox"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CCheckListBox class"
  - "checklist boxes"
ms.assetid: 1dd78438-00e8-441c-b36f-9c4f9ac0d019
caps.latest.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 27
---
# CCheckListBox Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供Windows检查表框中的功能。  
  
## 语法  
  
```  
  
class CCheckListBox : public CListBox  
  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CCheckListBox::CCheckListBox](../Topic/CCheckListBox::CCheckListBox.md)|构造 `CCheckListBox` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CCheckListBox::Create](../Topic/CCheckListBox::Create.md)|创建Windows检查表框并附加到 `CCheckListBox` 对象。|  
|[CCheckListBox::DrawItem](../Topic/CCheckListBox::DrawItem.md)|调用由结构，当所有者描述的可视方面是列表框更改。|  
|[CCheckListBox::Enable](../Topic/CCheckListBox::Enable.md)|启用或禁用检查表框项。|  
|[CCheckListBox::GetCheck](../Topic/CCheckListBox::GetCheck.md)|获取项目的复选框的状态。|  
|[CCheckListBox::GetCheckStyle](../Topic/CCheckListBox::GetCheckStyle.md)|获取控件的复选框的样式。|  
|[CCheckListBox::IsEnabled](../Topic/CCheckListBox::IsEnabled.md)|确定项目是否启用。|  
|[CCheckListBox::MeasureItem](../Topic/CCheckListBox::MeasureItem.md)|调用由结构，当具有所有者描述样式的列表框创建。|  
|[CCheckListBox::OnGetCheckPosition](../Topic/CCheckListBox::OnGetCheckPosition.md)|调用由框架获取项目的复选框的位置。|  
|[CCheckListBox::SetCheck](../Topic/CCheckListBox::SetCheck.md)|设置项目的复选框的状态。|  
|[CCheckListBox::SetCheckStyle](../Topic/CCheckListBox::SetCheckStyle.md)|设置控件的复选框的样式。|  
  
## 备注  
 “检查表框中”显示一个项列表，例如文件名。  在列表中的每个项都有一个复选框旁边的用户可以选中或清除。  
  
 `CCheckListBox` 仅用于所有者描述的控件，因为列表比文本字符串包含更多。  在其最简单，检查表框包含文本字符串和复选框，但是，您根本不需要具有文本。  例如，可以在每个项旁边的小的位图列出了与复选框。  
  
 若要创建自己的检查表框中，必须从 `CCheckListBox`派生您的选件类。  派生您的选件类，编写派生类的构造函数，然后调用 **Create**。  
  
 如果希望处理Windows列表框发送的通知消息到其父\(通常从 [CDialog](../../mfc/reference/cdialog-class.md)派生的选件类\)中，添加一个消息映射项和消息处理程序成员函数为每个消息的父选件类。  
  
 每个消息映射项采用以下形式:  
  
 **ON\_**通知**\(**`id`，`memberFxn`**\)**  
  
 其中 `id` 指定将控件的子窗口ID通知和 `memberFxn` 是您处理编写通知父成员函数的名称。  
  
 父的函数原型如下所示:  
  
 **afx\_msg** `void` `memberFxn` **\( \);**  
  
 只有专门与 **CCheckListBox** 的消息地图项\(但是，对于 [CListBox](../../mfc/reference/clistbox-class.md)还请参见消息映射项\):  
  
-   **ON\_CLBN\_CHKCHANGE** 用户更改了项目的复选框的状态。  
  
 如果您的检查表框是默认检查表框\(字符串列表与默认大小复选框的在每个左侧\)，可以使用默认 [CCheckListBox::DrawItem](../Topic/CCheckListBox::DrawItem.md) 绘制检查表框。  否则，必须重写 [CListBox::CompareItem](../Topic/CListBox::CompareItem.md) 功能和 [CCheckListBox::DrawItem](../Topic/CCheckListBox::DrawItem.md) 和 [CCheckListBox::MeasureItem](../Topic/CCheckListBox::MeasureItem.md) 功能。  
  
 您可以创建一个检查表框将从对话框模板或直接在代码。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CListBox](../../mfc/reference/clistbox-class.md)  
  
 `CCheckListBox`  
  
## 要求  
 **标头：**afxwin.h  
  
## 请参阅  
 [MFC示例TSTCON](../../top/visual-cpp-samples.md)   
 [CListBox Class](../../mfc/reference/clistbox-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CListBox Class](../../mfc/reference/clistbox-class.md)
---
title: "CListBox Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CListBox"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CListBox 类"
  - "列表框"
ms.assetid: 7ba3c699-c286-4cd9-9066-532c41ec05d1
caps.latest.revision: 26
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CListBox Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供Windows的功能列表框。  
  
## 语法  
  
```  
class CListBox : public CWnd  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CListBox::CListBox](../Topic/CListBox::CListBox.md)|构造 `CListBox` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CListBox::AddString](../Topic/CListBox::AddString.md)|添加一个字符串到列表框。|  
|[CListBox::CharToItem](../Topic/CListBox::CharToItem.md)|提供自定义 `WM_CHAR` 的重写处理为所有者描述没有字符串的列表框。|  
|[CListBox::CompareItem](../Topic/CListBox::CompareItem.md)|调用由框架确定新项目的位置在已排序的所有者描述列表框。|  
|[CListBox::Create](../Topic/CListBox::Create.md)|创建Windows列表框并将它附加到 `CListBox` 对象。|  
|[CListBox::DeleteItem](../Topic/CListBox::DeleteItem.md)|调用由框架，当用户从所有者描述中删除项列表框。|  
|[CListBox::DeleteString](../Topic/CListBox::DeleteString.md)|从列表框删除字符串。|  
|[CListBox::Dir](../Topic/CListBox::Dir.md)|添加文件名，驱动器或两个从当前目录到列表框。|  
|[CListBox::DrawItem](../Topic/CListBox::DrawItem.md)|调用由结构，当所有者描述的可视方面是列表框更改。|  
|[CListBox::FindString](../Topic/CListBox::FindString.md)|搜索在列表框中的字符串。|  
|[CListBox::FindStringExact](../Topic/CListBox::FindStringExact.md)|查找与指定字符串匹配的第一个列表框字符串。|  
|[CListBox::GetAnchorIndex](../Topic/CListBox::GetAnchorIndex.md)|检索当前定位点项的从零开始的索引在列表框中。|  
|[CListBox::GetCaretIndex](../Topic/CListBox::GetCaretIndex.md)|确定具有焦点矩形在多个选择列表框项的索引。|  
|[CListBox::GetCount](../Topic/CListBox::GetCount.md)|返回字符串的数量在列表框中。|  
|[CListBox::GetCurSel](../Topic/CListBox::GetCurSel.md)|返回当前选定的字符串的从零开始的索引在列表框中。|  
|[CListBox::GetHorizontalExtent](../Topic/CListBox::GetHorizontalExtent.md)|返回在像素宽度列表框可以水平移动。|  
|[CListBox::GetItemData](../Topic/CListBox::GetItemData.md)|返回一个32位值与列表框项。|  
|[CListBox::GetItemDataPtr](../Topic/CListBox::GetItemDataPtr.md)|返回指向列表框项。|  
|[CListBox::GetItemHeight](../Topic/CListBox::GetItemHeight.md)|确定高度列表框中的项。|  
|[CListBox::GetItemRect](../Topic/CListBox::GetItemRect.md)|它在当前显示，返回列表框项的边框。|  
|[CListBox::GetListBoxInfo](../Topic/CListBox::GetListBoxInfo.md)|检索项的数目每列。|  
|[CListBox::GetLocale](../Topic/CListBox::GetLocale.md)|检索列表框的区域设置标识符。|  
|[CListBox::GetSel](../Topic/CListBox::GetSel.md)|返回列表框项的选择状态。|  
|[CListBox::GetSelCount](../Topic/CListBox::GetSelCount.md)|返回在多个选择当前选择的字符串的数量列表框。|  
|[CListBox::GetSelItems](../Topic/CListBox::GetSelItems.md)|返回列表框当前选择的字符串的索引。|  
|[CListBox::GetText](../Topic/CListBox::GetText.md)|将一个列表框项到缓冲区中。|  
|[CListBox::GetTextLen](../Topic/CListBox::GetTextLen.md)|在列表框项的字节数组返回长度。|  
|[CListBox::GetTopIndex](../Topic/CListBox::GetTopIndex.md)|返回第一个可见字符串的索引在列表框中。|  
|[CListBox::InitStorage](../Topic/CListBox::InitStorage.md)|预分配内存块为列表框项和字符串。|  
|[CListBox::InsertString](../Topic/CListBox::InsertString.md)|插入到特定位置的字符串列表框。|  
|[CListBox::ItemFromPoint](../Topic/CListBox::ItemFromPoint.md)|返回列表框项的索引最靠近点。|  
|[CListBox::MeasureItem](../Topic/CListBox::MeasureItem.md)|调用由结构，当所有者描述时列表框创建确定列表框维度。|  
|[CListBox::ResetContent](../Topic/CListBox::ResetContent.md)|清除列表框的所有项。|  
|[CListBox::SelectString](../Topic/CListBox::SelectString.md)|搜索并选中单选的字符串列表框。|  
|[CListBox::SelItemRange](../Topic/CListBox::SelItemRange.md)|选择或取消选择字符串的大小在多个选择的列表框。|  
|[CListBox::SetAnchorIndex](../Topic/CListBox::SetAnchorIndex.md)|设置在多个选定内容的定位点列表框启动一个扩展选择。|  
|[CListBox::SetCaretIndex](../Topic/CListBox::SetCaretIndex.md)|设置焦点矩形对项目在多重选择的指定索引列表框。|  
|[CListBox::SetColumnWidth](../Topic/CListBox::SetColumnWidth.md)|设置列宽的多列列表框。|  
|[CListBox::SetCurSel](../Topic/CListBox::SetCurSel.md)|选择列表框字符串。|  
|[CListBox::SetHorizontalExtent](../Topic/CListBox::SetHorizontalExtent.md)|将像素宽度列表框可以水平移动。|  
|[CListBox::SetItemData](../Topic/CListBox::SetItemData.md)|将32位值与列表框项。|  
|[CListBox::SetItemDataPtr](../Topic/CListBox::SetItemDataPtr.md)|设置指向列表框项。|  
|[CListBox::SetItemHeight](../Topic/CListBox::SetItemHeight.md)|设置高度列表框中的项。|  
|[CListBox::SetLocale](../Topic/CListBox::SetLocale.md)|设置列表框的区域设置标识符。|  
|[CListBox::SetSel](../Topic/CListBox::SetSel.md)|选择或取消选择在多个选择的列表框项列表框。|  
|[CListBox::SetTabStops](../Topic/CListBox::SetTabStops.md)|将列表框的制表位位置。|  
|[CListBox::SetTopIndex](../Topic/CListBox::SetTopIndex.md)|将第一个可见字符串的从零开始的索引在列表框中。|  
|[CListBox::VKeyToItem](../Topic/CListBox::VKeyToItem.md)|提供自定义 `WM_KEYDOWN` 的重写处理为设置了 **LBS\_WANTKEYBOARDINPUT** 样式的列表框。|  
  
## 备注  
 列表框将显示项列表，例如文件名，用户可以查看并选择。  
  
 在单只选择列表框，用户可以选择一项。  在多重选择列表框，项的大小可以选择。  当用户选择某个项时，该控件将突出显示，而列表框发送通知消息到父窗口。  
  
 可以创建一个列表框从对话框模板或直接在代码。  若要直接创建它，请构造 `CListBox` 对象，然后调用 [创建](../Topic/CListBox::Create.md) 成员函数创建Windows列表框控件并将其附加到 `CListBox` 对象。  若要使用列表框在对话框模板，请声明在对话框选件类的列表框变量，然后使用 `DDX_Control` 在对话框选件类的 `DoDataExchange` 功能将成员变量添加到控件中。  （这对于自动执行，将控件添加到变量您的对话框选件类。）  
  
 构造。`CListBox`从派生的类可以选件一步过程。  编写该派生类的构造函数和调用 **Create** 从构造函数内部。  
  
 如果希望处理Windows列表框发送的通知消息到其父\(通常从 [CDialog](../../mfc/reference/cdialog-class.md)派生的选件类\)中，添加一个消息映射项和消息处理程序成员函数为每个消息的父选件类。  
  
 每个消息映射项采用以下形式:  
  
 `ON_Notification( id, memberFxn )`  
  
 其中 `id` 指定发送列表框控件的子窗口ID通知和 `memberFxn` 是您处理编写通知父成员函数的名称。  
  
 父的函数原型如下所示:  
  
 `afx_msg void memberFxn( );`  
  
 以下潜在的消息映射项及其将发送到父用例说明的列表:  
  
-   **ON\_LBN\_DBLCLK** 用户双击在列表框中的字符串。  具有 [LBS\_NOTIFY](../../mfc/reference/list-box-styles.md) 样式仅的列表框将发送此通知消息。  
  
-   **ON\_LBN\_ERRSPACE** 列表框不能分配的内存量已经足以满足要求。  
  
-   **ON\_LBN\_KILLFOCUS** 列表框失去输入焦点。  
  
-   **ON\_LBN\_SELCANCEL** 当前列表框中选择取消。  此信息，当列表框包含 **LBS\_NOTIFY** 样式时，只发送。  
  
-   在列表框中选择更改的**ON\_LBN\_SELCHANGE**。  此通知，如果 [CListBox::SetCurSel](../Topic/CListBox::SetCurSel.md) 成员函数，更改选择不发送。  此通知仅适用于具有 **LBS\_NOTIFY** 样式的列表框。  **LBN\_SELCHANGE** 通知信息对多个选择向列表框，每当用户按一个箭头键，因此，即使选定内容不会更改。  
  
-   **ON\_LBN\_SETFOCUS** 列表框接收输入焦点。  
  
-   **ON\_WM\_CHARTOITEM** 所有者描述没有字符串 `WM_CHAR` 接收消息的列表框。  
  
-   **ON\_WM\_VKEYTOITEM** 具有 **LBS\_WANTKEYBOARDINPUT** 样式的列表框接收 `WM_KEYDOWN` 消息。  
  
 如果要创建在对话框中的一 `CListBox` 对象\(通过对话框资源\)，自动销毁 `CListBox` 对象，当用户关闭对话框时。  
  
 如果在中创建的一 `CListBox` 对象，则可能需要销毁 `CListBox` 对象。  如果在堆栈上创建 `CListBox` 对象，自动销毁它。  使用 **new** 功能，如果要创建在堆的 `CListBox` 对象，则必须对对象的 **delete** 销毁它，当用户关闭父窗口时。  
  
 如果将在 `CListBox` 对象的任何内存，请重写 `CListBox` 析构函数进程分配。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CListBox`  
  
## 要求  
 **标头：**afxwin.h  
  
## 请参阅  
 [MFC示例CTRLTEST](../../top/visual-cpp-samples.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [CButton Class](../../mfc/reference/cbutton-class.md)   
 [CComboBox Class](../../mfc/reference/ccombobox-class.md)   
 [CEdit Class](../../mfc/reference/cedit-class.md)   
 [CScrollBar Class](../../mfc/reference/cscrollbar-class.md)   
 [CStatic Class](../../mfc/reference/cstatic-class.md)
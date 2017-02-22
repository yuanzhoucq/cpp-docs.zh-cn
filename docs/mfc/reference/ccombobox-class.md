---
title: "CComboBox Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CComboBox"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComboBox 类"
  - "组合框, CComboBox objects"
ms.assetid: 4e73b5df-0d2e-4658-9706-38133fb10513
caps.latest.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# CComboBox Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供Windows组合框的功能。  
  
## 语法  
  
```  
class CComboBox : public CWnd  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CComboBox::CComboBox](../Topic/CComboBox::CComboBox.md)|构造 `CComboBox` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CComboBox::AddString](../Topic/CComboBox::AddString.md)|添加一个字符串到列表的末尾在组合框的列表框中，或在已排序的位置具有 **CBS\_SORT** 样式的列表框。|  
|[CComboBox::Clear](../Topic/CComboBox::Clear.md)|删除（清除）当前选择，如果有，则在编辑控件。|  
|[CComboBox::CompareItem](../Topic/CComboBox::CompareItem.md)|调用由框架确定相对位置新列表中的已排序的所有者描述的组合框中的项。|  
|[CComboBox::Copy](../Topic/CComboBox::Copy.md)|复制当前选择，如果有，在剪贴板上。**CF\_TEXT** 格式。|  
|[CComboBox::Create](../Topic/CComboBox::Create.md)|创建组合框并将它附加到 `CComboBox` 对象。|  
|[CComboBox::Cut](../Topic/CComboBox::Cut.md)|删除\(剪辑\)当前选择，如果有，则在编辑控件和复制到剪贴板已删除的文本的 **CF\_TEXT** 格式。|  
|[CComboBox::DeleteItem](../Topic/CComboBox::DeleteItem.md)|调用由结构，在列表项从一个所有者描述的组合框中删除。|  
|[CComboBox::DeleteString](../Topic/CComboBox::DeleteString.md)|从组合框的列表框删除字符串。|  
|[CComboBox::Dir](../Topic/CComboBox::Dir.md)|添加文件名称列表。组合框的列表框。|  
|[CComboBox::DrawItem](../Topic/CComboBox::DrawItem.md)|调用由结构，在一个所有者描述的组合框的可视方面是更改。|  
|[CComboBox::FindString](../Topic/CComboBox::FindString.md)|查找在组合框的列表框包含指定的前缀的第一个字符串。|  
|[CComboBox::FindStringExact](../Topic/CComboBox::FindStringExact.md)|查找第一个列表框字符串\(在组合框\)。与指定字符串。|  
|[CComboBox::GetComboBoxInfo](../Topic/CComboBox::GetComboBoxInfo.md)|检索有关 `CComboBox` 对象的信息。|  
|[CComboBox::GetCount](../Topic/CComboBox::GetCount.md)|检索项的数目在组合框的列表框中。|  
|[CComboBox::GetCueBanner](../Topic/CComboBox::GetCueBanner.md)|获取的组合框控件中显示的提示文本。|  
|[CComboBox::GetCurSel](../Topic/CComboBox::GetCurSel.md)|检索当前选定项的索引，如果有，在组合框的列表框。|  
|[CComboBox::GetDroppedControlRect](../Topic/CComboBox::GetDroppedControlRect.md)|检索屏幕坐标可见\(拉\)一个下拉组合框中的列表框。|  
|[CComboBox::GetDroppedState](../Topic/CComboBox::GetDroppedState.md)|确定一个下拉组合框中的列表框是否可见\(拉）。|  
|[CComboBox::GetDroppedWidth](../Topic/CComboBox::GetDroppedWidth.md)|检索组合框的下拉式列表框部分的最小值允许的宽度。|  
|[CComboBox::GetEditSel](../Topic/CComboBox::GetEditSel.md)|获取当前选择的开始和结束字符位置在组合框中编辑控件。|  
|[CComboBox::GetExtendedUI](../Topic/CComboBox::GetExtendedUI.md)|确定组合框是否具有默认的用户界面或扩展的用户界面。|  
|[CComboBox::GetHorizontalExtent](../Topic/CComboBox::GetHorizontalExtent.md)|返回在像素宽度组合框的列表框部分可以水平滚动。|  
|[CComboBox::GetItemData](../Topic/CComboBox::GetItemData.md)|检索该由应用程序提供的32位值与指定的组合框项。|  
|[CComboBox::GetItemDataPtr](../Topic/CComboBox::GetItemDataPtr.md)|检索与指定的组合框中的项由应用程序提供的32位指针。|  
|[CComboBox::GetItemHeight](../Topic/CComboBox::GetItemHeight.md)|检索高度列表在组合框中的项。|  
|[CComboBox::GetLBText](../Topic/CComboBox::GetLBText.md)|从组合框的列表框中获取字符串。|  
|[CComboBox::GetLBTextLen](../Topic/CComboBox::GetLBTextLen.md)|获取一个字符串的长度在组合框的列表框中。|  
|[CComboBox::GetLocale](../Topic/CComboBox::GetLocale.md)|检索组合框的区域设置标识符。|  
|[CComboBox::GetMinVisible](../Topic/CComboBox::GetMinVisible.md)|获取可见项的最小值在下拉列表当前组合框。|  
|[CComboBox::GetTopIndex](../Topic/CComboBox::GetTopIndex.md)|返回第一个可视项的索引在组合框中的列表框部分。|  
|[CComboBox::InitStorage](../Topic/CComboBox::InitStorage.md)|预分配块项目和字符串的内存组合框的列表框部分。|  
|[CComboBox::InsertString](../Topic/CComboBox::InsertString.md)|插入到组合框的列表框中。|  
|[CComboBox::LimitText](../Topic/CComboBox::LimitText.md)|限制用户可以输入组合框编辑控件的文本的长度。|  
|[CComboBox::MeasureItem](../Topic/CComboBox::MeasureItem.md)|调用由框架确定组合框维度，在一个所有者描述的组合框中创建。|  
|[CComboBox::Paste](../Topic/CComboBox::Paste.md)|从剪贴板中的数据到当前光标的编辑控件中确定的插入。  数据，仅当剪贴板在 **CF\_TEXT** 格式，包含数据插入。|  
|[CComboBox::ResetContent](../Topic/CComboBox::ResetContent.md)|从列表框中移除所有项和组合框的编辑控件。|  
|[CComboBox::SelectString](../Topic/CComboBox::SelectString.md)|搜索在组合框的列表框中的字符串和，因此，如果找到该字符串，选择列表框中的字符串并复制该字符串到编辑控件。|  
|[CComboBox::SetCueBanner](../Topic/CComboBox::SetCueBanner.md)|设置为组合框控件中显示的提示文本。|  
|[CComboBox::SetCurSel](../Topic/CComboBox::SetCurSel.md)|选择在组合框的列表框中的字符串。|  
|[CComboBox::SetDroppedWidth](../Topic/CComboBox::SetDroppedWidth.md)|设置组合框的下拉式列表框部分的最小值允许的宽度。|  
|[CComboBox::SetEditSel](../Topic/CComboBox::SetEditSel.md)|选择在组合框中编辑控件的字符。|  
|[CComboBox::SetExtendedUI](../Topic/CComboBox::SetExtendedUI.md)|对于 **CBS\_DROPDOWN** 或 **CBS\_DROPDOWNLIST** 样式中的组合框中选择默认的用户界面或扩展的用户界面。|  
|[CComboBox::SetHorizontalExtent](../Topic/CComboBox::SetHorizontalExtent.md)|将像素宽度组合框的列表框部分可以水平滚动。|  
|[CComboBox::SetItemData](../Topic/CComboBox::SetItemData.md)|将32位值与在组合框中的指定项。|  
|[CComboBox::SetItemDataPtr](../Topic/CComboBox::SetItemDataPtr.md)|将32位指针与在组合框中的指定项。|  
|[CComboBox::SetItemHeight](../Topic/CComboBox::SetItemHeight.md)|设置高度列表在组合框中的项或组合框的编辑控件\(或静态文本\)部分的高度。|  
|[CComboBox::SetLocale](../Topic/CComboBox::SetLocale.md)|设置组合框的区域设置标识符。|  
|[CComboBox::SetMinVisibleItems](../Topic/CComboBox::SetMinVisibleItems.md)|设置可见项的最小值在下拉列表当前组合框。|  
|[CComboBox::SetTopIndex](../Topic/CComboBox::SetTopIndex.md)|调用组合框的列表框部分显示具有指定索引的项目位于顶部。|  
|[CComboBox::ShowDropDown](../Topic/CComboBox::ShowDropDown.md)|显示或隐藏具有 **CBS\_DROPDOWN** 或 **CBS\_DROPDOWNLIST** 样式组合框的列表框。|  
  
## 备注  
 组合框包含列表框将与静态控件或编辑控件。  当用户在控件旁边时，选择下拉箭头将控件的列表框部分可能一直显示或只能拉。  
  
 当前选定项（如果有）在列表框在静态显示或编辑控件。  此外，在中，如果组合框线下拉列表样式，用户可以键入初始字符一个列表中的项，并且，列表框，因此，如果可见，将显示与初始字符的下一项。  
  
 下表比较了三个组合框 [样式](../../mfc/reference/combo-box-styles.md)。  
  
|样式|何时为列表框中可见?|静态或编辑控件?|  
|--------|----------------|--------------|  
|简单|始终|Edit|  
|下拉列表|在下拉|Edit|  
|下拉列表|在下拉|Static|  
  
 您可以创建一 `CComboBox` 对象从对话框模板或直接在代码。  在这两种情况下，首次调用构造函数 `CComboBox` 构造 `CComboBox` 对象;然后调用 [创建](../Topic/CComboBox::Create.md) 成员函数创建控件并将其附加到 `CComboBox` 对象。  
  
 如果希望处理Windows组合框发送的通知消息到其父\(通常从 `CDialog`派生的选件类\)中，添加一个消息映射项和消息处理程序成员函数为每个消息的父选件类。  
  
 每个消息映射项采用以下形式:  
  
 **ON\_**通知**\(**`id`**,**`memberFxn`**\)**  
  
 其中 `id` 指定发送组合框控件的子窗口ID通知和 `memberFxn` 是您处理编写通知父成员函数的名称。  
  
 父的函数原型如下所示:  
  
 **afx\_msg** `void` `memberFxn` **\(**\);  
  
 某些通知要发送的顺序并不可预知。  具体而言，**CBN\_SELCHANGE** 通知可以在 **CBN\_CLOSEUP** 通知前后发生其中之一。  
  
 潜在的消息映射项如下:  
  
-   **ON\_CBN\_CLOSEUP** \(Windows 3.1和更高版本。）组合框的列表框关闭。  此通知信息不具有 [CBS\_SIMPLE](../../mfc/reference/combo-box-styles.md) 样式的组合框发送。  
  
-   **ON\_CBN\_DBLCLK** 用户双击在组合框的列表框中的字符串。  此通知信息对于 **CBS\_SIMPLE** 样式的组合框只发送。  对 [CBS\_DROPDOWN](../../mfc/reference/combo-box-styles.md) 或 [CBS\_DROPDOWNLIST](../../mfc/reference/combo-box-styles.md) 样式的组合框，因为单个单击隐藏列表框，在中，双击不能出现。  
  
-   **ON\_CBN\_DROPDOWN** 组合框的列表框将下拉\(使可见）。  此通知消息可能具有 **CBS\_DROPDOWN** 或 **CBS\_DROPDOWNLIST** 样式的组合框仅发生。  
  
-   **ON\_CBN\_EDITCHANGE** 用户获得的可能修改了在组合框中编辑控件部分文本的操作。  不同 **CBN\_EDITUPDATE** 消息，此信息在Windows更新后发送屏幕。  它，如果组合框包含 **CBS\_DROPDOWNLIST** 样式，不发送。  
  
-   **ON\_CBN\_EDITUPDATE** 组合框的编辑控件部分将显示修改后的文本。  发送此通知信息，控件格式化文本后，该但是，它显示文本之前。  它，如果组合框包含 **CBS\_DROPDOWNLIST** 样式，不发送。  
  
-   **ON\_CBN\_ERRSPACE** 组合框不能分配的内存量已经足以满足特定请求。  
  
-   **ON\_CBN\_SELENDCANCEL** \(Windows 3.1和更高版本。）指示应该移除用户的选择。  用户单击项并单击另一个窗口或控件隐藏组合框的列表框。  此通知发送消息，请在 **CBN\_CLOSEUP** 通知消息之前应忽略用户的选择。  发送 **CBN\_SELENDCANCEL** 或 **CBN\_SELENDOK** 通知信息，即使没有发送 **CBN\_CLOSEUP** 通知信息\(对于包含 **CBS\_SIMPLE** 样式的组合框）。  
  
-   **ON\_CBN\_SELENDOK** 用户选择一个项目然后按以下键或单击向下键隐藏组合框的列表框。  此通知发送消息，请在 **CBN\_CLOSEUP** 消息之前应考虑用户的选择活动。  发送 **CBN\_SELENDCANCEL** 或 **CBN\_SELENDOK** 通知信息，即使没有发送 **CBN\_CLOSEUP** 通知信息\(对于包含 **CBS\_SIMPLE** 样式的组合框）。  
  
-   **ON\_CBN\_KILLFOCUS** 组合框失去输入焦点。  
  
-   **ON\_CBN\_SELCHANGE** 在组合框的列表框中选择将因单击列表框或更改选择的用户通过使用箭头键。  当处理此消息时，组合框的编辑控件的文本可以通过 `GetLBText` 或另一个类似的功能仅检索。  无法使用 `GetWindowText`。  
  
-   **ON\_CBN\_SETFOCUS** 组合框接收输入焦点。  
  
 如果要创建在对话框中的一 `CComboBox` 对象\(通过对话框资源\)，自动销毁 `CComboBox` 对象，当用户关闭对话框时。  
  
 如果嵌入在另一个窗口对象中的一 `CComboBox` 对象，则不需要销毁它。  如果在堆栈上创建 `CComboBox` 对象，自动销毁它。  使用 **new** 功能，如果要创建在堆的 `CComboBox` 对象，则必须对对象的 **delete** 销毁它，当销毁时Windows组合框。  
  
 **Note**，如果希望处理 `WM_KEYDOWN` 和 `WM_CHAR` 消息，则必须子类组合框中编辑和列表框控件，从 `CEdit` 和 `CListBox`派生选件类，并将这些消息的处理程序添加到派生类。  有关更多信息，请参见 [http:\/\/support.microsoft.com\/default.aspx?scid\=kb;en\-us;Q174667](http://support.microsoft.com/default.aspx?scid=kb;en-us;Q174667) 和 [CWnd::SubclassWindow](../Topic/CWnd::SubclassWindow.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CComboBox`  
  
## 要求  
 **标头：**afxwin.h  
  
## 请参阅  
 [MFC示例CTRLBARS](../../top/visual-cpp-samples.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [CButton Class](../../mfc/reference/cbutton-class.md)   
 [CEdit Class](../../mfc/reference/cedit-class.md)   
 [CListBox Class](../../mfc/reference/clistbox-class.md)   
 [CScrollBar Class](../../mfc/reference/cscrollbar-class.md)   
 [CStatic Class](../../mfc/reference/cstatic-class.md)   
 [CDialog Class](../../mfc/reference/cdialog-class.md)
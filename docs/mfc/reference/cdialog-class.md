---
title: "CDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDialog class"
  - "MFC 对话框, 基类"
  - "有模式对话框, 创建"
  - "无模式对话框, 创建"
  - "无模式对话框, 显示"
ms.assetid: ca64b77e-2cd2-47e3-8eff-c2645ad578f9
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

用于显示在屏幕的对话框使用的基类。  
  
## 语法  
  
```  
class CDialog : public CWnd  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CDialog::CDialog](../Topic/CDialog::CDialog.md)|构造 `CDialog` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CDialog::Create](../Topic/CDialog::Create.md)|初始化 `CDialog` 对象。  创建无模式对话框并将它附加到 `CDialog` 对象。|  
|[CDialog::CreateIndirect](../Topic/CDialog::CreateIndirect.md)|在内存\(基于的不是资源从创建对话框模板的无模式对话框）。|  
|[CDialog::DoModal](../Topic/CDialog::DoModal.md)|调用模式对话框并返回，在执行。|  
|[CDialog::EndDialog](../Topic/CDialog::EndDialog.md)|关闭有模式对话框。|  
|[CDialog::GetDefID](../Topic/CDialog::GetDefID.md)|获取默认按钮控件的ID对话框中。|  
|[CDialog::GotoDlgCtrl](../Topic/CDialog::GotoDlgCtrl.md)|将焦点移到对话框中的指定对话框控件。|  
|[CDialog::InitModalIndirect](../Topic/CDialog::InitModalIndirect.md)|在内存\(基于的不是资源从创建对话框模板的模式对话框）。  存储参数，直到函数 `DoModal` 调用。|  
|[CDialog::MapDialogRect](../Topic/CDialog::MapDialogRect.md)|将矩形的对话框单位转换为屏幕单元。|  
|[CDialog::NextDlgCtrl](../Topic/CDialog::NextDlgCtrl.md)|将焦点移到对话框的下一个对话框控件。|  
|[CDialog::OnInitDialog](../Topic/CDialog::OnInitDialog.md)|增加对话框初始化的重写。|  
|[CDialog::OnSetFont](../Topic/CDialog::OnSetFont.md)|指定字体的重写对话框控件是使用时绘制文本。|  
|[CDialog::PrevDlgCtrl](../Topic/CDialog::PrevDlgCtrl.md)|将焦点移到对话框的前面对话框控件。|  
|[CDialog::SetDefID](../Topic/CDialog::SetDefID.md)|更改对话框的默认按钮控件与指定的普通按钮。|  
|[CDialog::SetHelpID](../Topic/CDialog::SetHelpID.md)|设置对话框的上下文相关帮助ID。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CDialog::OnCancel](../Topic/CDialog::OnCancel.md)|执行取消按钮或ESC键操作的重写。  该默认关闭对话框，并 **DoModal** 返回 **IDCANCEL**。|  
|[CDialog::OnOK](../Topic/CDialog::OnOK.md)|执行"确定"按钮事件的重写在一个模式对话框。  该默认关闭对话框，并 `DoModal` 返回 **IDOK**。|  
  
## 备注  
 对话框是两种类型:模式和无模式。  应用程序将继续之前，必须由用户关闭有模式对话框。  无模式对话框允许用户显示对话框并返回到另一个任务，而无需取消或移除对话框。  
  
 `CDialog` 对象是对话框模板并 `CDialog`派生类的组合。  使用对话框编辑器创建对话框模板并将它存储在资源，然后使用添加选件类向导"创建从 `CDialog`派生的选件类。  
  
 一个对话框，与其他窗口，接收来自Windows的消息。  在对话框中，您特别为了使从那时的处理对话框的控件的通知消息感兴趣用户与您的对话框交互。  使用消息您希望处理，并将其添加适当的消息映射项和消息处理程序成员函数在的选件类的"属性"窗口中选择。  只需在处理程序成员函数编写特定于应用程序的代码。  
  
 如果您愿意，始终可以编写消息映射项，成员手动函数。  
  
 存在，但最常用的对话框，您将成员变量添加到您的派生的对话框选件类添加到对话框的控件中输入的数据存储由用户或为用户显示数据。  可以使用将变量向导创建成员变量和将自身与控件。  同时，您选择值的变量类型和允许范围的每个变量的。  代码向导添加成员变量添加到您的派生的对话框选件类。  
  
 数据映射自动生成处理数据交换。成员变量和对话框控件的。  数据映射提供初始化对话框上的控件具有适当的值，检索数据，并验证数据的功能。  
  
 若要创建一个模式对话框，请选择"堆栈的对象使用您的派生的对话框选件类的构造函数然后调用 `DoModal` 创建对话框窗口及其控件。  如果要创建无模式对话框，则对您的对话框选件类构造函数的 **Create**。  
  
 要在内存中也可以创建模板使用 [DLGTEMPLATE](http://msdn.microsoft.com/library/windows/desktop/ms645394) 数据结构 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]如中所述。  在构造 `CDialog` 对象后，调用 [CreateIndirect](../Topic/CDialog::CreateIndirect.md) 创建无模式对话框或调用 [InitModalIndirect](../Topic/CDialog::InitModalIndirect.md) 和 [DoModal](../Topic/CDialog::DoModal.md) 创建一个模式对话框。  
  
 替换和验证数据映射即添加到您的新对话框选件类 `CWnd::DoDataExchange` 的重写中编写。  有关更多 `CWnd` 参见中的 [DoDataExchange](../Topic/CWnd::DoDataExchange.md) 成员函数在替换和验证功能。  
  
 程序员和框架通过调用间接调用 `DoDataExchange` 到 [CWnd::UpdateData](../Topic/CWnd::UpdateData.md)。  
  
 当用户单击"确定"按钮关闭有模式对话框时，框架调用 `UpdateData`。  （该数据不会检索，如果单击"取消"按钮。）[OnInitDialog](../Topic/CDialog::OnInitDialog.md) 的默认实现调用 `UpdateData` 设置控件的初始值。  通常可以重写 `OnInitDialog` 进一步初始化控件。  `OnInitDialog` 调用，则所有对话框创建控件后，因此，在对话框中显示前面。  
  
 可以在模式或无模式对话框时的执行在\+任何\+时间调用 `CWnd::UpdateData`。  
  
 如果您手动开发一个对话框，您将添加必要的成员变量添加到派生的对话框选件类，因此，您添加成员函数设置或获取这些值。  
  
 一个模式对话框自动关闭，当用户按OK \(确定\)或cancel \(取消\)按钮时，或者当代码调用 `EndDialog` 成员函数时。  
  
 在实现无模式对话框时，始终重写 `OnCancel` 成员函数并调用 `DestroyWindow` 从它的内部。  不要调用基类 `CDialog::OnCancel`，因为它调用 `EndDialog`，将使对话框不可见，但不会销毁它。  因为无模式对话框通常随 **new**，还应重写无模式对话框的 `PostNcDestroy` 以删除 **this**。  模式对话框在框架通常构造，不需要 `PostNcDestroy` 清除。  
  
 有关 `CDialog`的更多信息，请参见:  
  
-   [对话框](../../mfc/dialog-boxes.md)  
  
-   知识库文章Q262954:HOWTO:使用滚动条创建一Resizeable对话框  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CDialog`  
  
## 要求  
 **标头：**afxwin.h  
  
## 请参阅  
 [MFC DLGCBR32示例](../../top/visual-cpp-samples.md)   
 [MFC示例DLGTEMPL](../../top/visual-cpp-samples.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)
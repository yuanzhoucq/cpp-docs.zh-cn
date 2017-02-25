---
title: "CMFCEditBrowseCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCEditBrowseCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCEditBrowseCtrl class"
  - "CMFCEditBrowseCtrl constructor"
  - "CMFCEditBrowseCtrl::PreTranslateMessage method"
ms.assetid: 69cfd886-3d35-4bee-8901-7c88fcf9520f
caps.latest.revision: 33
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 35
---
# CMFCEditBrowseCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCEditBrowseCtrl` 选件类支持编辑浏览控件，该控件是可编辑的文本框选择包含一个浏览"按钮。  当用户单击"浏览"按钮时，该控件执行自定义操作或显示包含文件浏览器或一个文件夹浏览器的标准对话框。  
  
## 语法  
  
```  
class CMFCEditBrowseCtrl : public CEdit  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|`CMFCEditBrowseCtrl::CMFCEditBrowseCtrl`|默认构造函数。|  
|`CMFCEditBrowseCtrl::~CMFCEditBrowseCtrl`|析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCEditBrowseCtrl::EnableBrowseButton](../Topic/CMFCEditBrowseCtrl::EnableBrowseButton.md)|启用或禁用\(隐藏\)浏览"按钮。|  
|[CMFCEditBrowseCtrl::EnableFileBrowseButton](../Topic/CMFCEditBrowseCtrl::EnableFileBrowseButton.md)|启用浏览按钮并将编辑浏览 *文件浏览模式的* 控件。|  
|[CMFCEditBrowseCtrl::EnableFolderBrowseButton](../Topic/CMFCEditBrowseCtrl::EnableFolderBrowseButton.md)|启用浏览按钮并将编辑浏览 *文件夹浏览模式的* 控件。|  
|[CMFCEditBrowseCtrl::GetMode](../Topic/CMFCEditBrowseCtrl::GetMode.md)|返回当前浏览模式。|  
|[CMFCEditBrowseCtrl::OnAfterUpdate](../Topic/CMFCEditBrowseCtrl::OnAfterUpdate.md)|调用由框架，在编辑浏览后控制更新与浏览事件的结果。|  
|[CMFCEditBrowseCtrl::OnBrowse](../Topic/CMFCEditBrowseCtrl::OnBrowse.md)|调用机制，用于在用户单击浏览按钮之后。|  
|[CMFCEditBrowseCtrl::OnChangeLayout](../Topic/CMFCEditBrowseCtrl::OnChangeLayout.md)|重绘当前编辑浏览控件。|  
|[CMFCEditBrowseCtrl::OnDrawBrowseButton](../Topic/CMFCEditBrowseCtrl::OnDrawBrowseButton.md)|调用由框架绘制浏览"按钮。|  
|[CMFCEditBrowseCtrl::OnIllegalFileName](../Topic/CMFCEditBrowseCtrl::OnIllegalFileName.md)|调用由结构，当一个非法文件名在编辑控件中输入的。|  
|`CMFCEditBrowseCtrl::PreTranslateMessage`|在将调度到 [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) 和 [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows功能之前，将windows消息。  有关语法和更多信息，请参见 [CWnd::PreTranslateMessage](../Topic/CWnd::PreTranslateMessage.md)。|  
|[CMFCEditBrowseCtrl::SetBrowseButtonImage](../Topic/CMFCEditBrowseCtrl::SetBrowseButtonImage.md)|设置浏览按钮的自定义图像。|  
  
## 备注  
 使用该编辑器浏览控件选择文件或文件夹的名称。  或者，请使用控件执行自定义操作\(如显示对话框。  可以显示或不显示"浏览"按钮，因此，您可以将自定义标签或图像。按钮。  
  
 编辑的 *浏览模式* 浏览控件以确定它是否显示"浏览"按钮，以及事件发生，单击按钮时。  有关更多信息，请参见 [GetMode](../Topic/CMFCEditBrowseCtrl::GetMode.md) 方法。  
  
 `CMFCEditBrowseCtrl` 选件类支持以下模式。  
  
 `custom mode`  
 当用户单击"浏览"按钮时，自定义操作执行。  例如，可以显示特定的对话框。  
  
 `file mode`  
 当用户单击"浏览"按钮时，标准文件选择显示对话框。  
  
 `folder mode`  
 当用户单击"浏览"按钮时，标准文件夹选择对话框中显示。  
  
## 帮助主题:指定编辑浏览控件  
 执行以下步骤将编辑浏览在应用程序中的控件:  
  
1.  如果希望实现自定义浏览模式，从 `CMFCEditBrowseCtrl` 选件类派生您的类选件然后重写 [CMFCEditBrowseCtrl::OnBrowse](../Topic/CMFCEditBrowseCtrl::OnBrowse.md) 方法。  在重写的方法中，执行自定义浏览事件并更新编辑浏览与该结果的控件。  
  
2.  嵌入或 `CMFCEditBrowseCtrl` 对象或派生的编辑控件对象浏览到父窗口对象。  
  
3.  如果使用 **选件类向导** 创建对话框中，添加编辑控件\(`CEdit`\)添加到对话框窗体。  另外，将添加一个变量访问在您的标头文件的控件。  在您的标头文件，从 `CEdit` 将变量的类型。`CMFCEditBrowseCtrl`。  编辑浏览控件将自动创建。  如果不使用 **选件类向导**，添加一个 `CMFCEditBrowseCtrl` 变量到您的标头文件然后调用其 `Create` 方法。  
  
4.  如果您添加一个编辑浏览控件添加到对话框，使用 **类向导** 工具设置数据交换。  
  
5.  调用 [EnableFolderBrowseButton](../Topic/CMFCEditBrowseCtrl::EnableFolderBrowseButton.md)、 [EnableFileBrowseButton](../Topic/CMFCEditBrowseCtrl::EnableFileBrowseButton.md)或 [EnableBrowseButton](../Topic/CMFCEditBrowseCtrl::EnableBrowseButton.md) 方法设置浏览模式并显示浏览"按钮。  调用 [GetMode](../Topic/CMFCEditBrowseCtrl::GetMode.md) 方法获取当前浏览模式。  
  
6.  用于浏览按钮若要提供自定义图像，请调用 [SetBrowseButtonImage](../Topic/CMFCEditBrowseCtrl::SetBrowseButtonImage.md) 方法或重写 [OnDrawBrowseButton](../Topic/CMFCEditBrowseCtrl::OnDrawBrowseButton.md) 方法。  
  
7.  从编辑器中移除浏览按钮浏览控件，调用与 `bEnable` 参数的 [EnableBrowseButton](../Topic/CMFCEditBrowseCtrl::EnableBrowseButton.md) 方法设置为 `FALSE`。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CEdit](../../mfc/reference/cedit-class.md)  
  
 [CMFCEditBrowseCtrl](../../mfc/reference/cmfceditbrowsectrl-class.md)  
  
## 示例  
 下面的示例在 `CMFCEditBrowseCtrl` 选件类演示如何使用这两种方法: `EnableFolderBrowseButton` 和 `EnableFileBrowseButton`。  此示例是 [新的控件示例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_NewControls#6](../../mfc/reference/codesnippet/CPP/cmfceditbrowsectrl-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#7](../../mfc/reference/codesnippet/CPP/cmfceditbrowsectrl-class_2.cpp)]  
  
## 要求  
 **标头:** afxeditbrowsectrl.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)
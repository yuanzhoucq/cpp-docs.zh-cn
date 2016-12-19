---
title: "CToolBar Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CToolBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - " [C++], button controls"
  - "按钮 [C++], MFC toolbars"
  - "control bars [C++], CToolBar class"
  - "CToolBar class"
  - "工具栏 [C++], CToolBar class"
  - "Windows common controls [C++], CToolBar class"
  - "Windows toolbar common controls [C++]"
ms.assetid: e868da26-5e07-4607-9651-e2f863ad9059
caps.latest.revision: 26
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CToolBar Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

控件具有多个副本的按钮和选项分隔符行条。  
  
## 语法  
  
```  
class CToolBar : public CControlBar  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CToolBar::CToolBar](../Topic/CToolBar::CToolBar.md)|构造 `CToolBar` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CToolBar::CommandToIndex](../Topic/CToolBar::CommandToIndex.md)|返回一个按钮的索引具有特定命令ID的.|  
|[CToolBar::Create](../Topic/CToolBar::Create.md)|创建Windows工具栏并将它附加到 `CToolBar` 对象。|  
|[CToolBar::CreateEx](../Topic/CToolBar::CreateEx.md)|使用嵌入 `CToolBarCtrl` 对象的附加样式创建一 `CToolBar` 对象。|  
|[CToolBar::GetButtonInfo](../Topic/CToolBar::GetButtonInfo.md)|检索按钮的ID、样式和图像数字。|  
|[CToolBar::GetButtonStyle](../Topic/CToolBar::GetButtonStyle.md)|检索按钮的样式。|  
|[CToolBar::GetButtonText](../Topic/CToolBar::GetButtonText.md)|检索将显示在按钮的文本。|  
|[CToolBar::GetItemID](../Topic/CToolBar::GetItemID.md)|返回按钮或分隔符的命令ID在给定索引。|  
|[CToolBar::GetItemRect](../Topic/CToolBar::GetItemRect.md)|检索该项的显示矩形在给定索引。|  
|[CToolBar::GetToolBarCtrl](../Topic/CToolBar::GetToolBarCtrl.md)|允许直接访问基础公共控件。|  
|[CToolBar::LoadBitmap](../Topic/CToolBar::LoadBitmap.md)|加载包含位图按钮图像的位图。|  
|[CToolBar::LoadToolBar](../Topic/CToolBar::LoadToolBar.md)|填充资源编辑器创建的一个工具栏资源。|  
|[CToolBar::SetBitmap](../Topic/CToolBar::SetBitmap.md)|设置一个数字复制的图像。|  
|[CToolBar::SetButtonInfo](../Topic/CToolBar::SetButtonInfo.md)|将按钮的ID、样式和图像数字。|  
|[CToolBar::SetButtons](../Topic/CToolBar::SetButtons.md)|设置按钮样式和按钮图像索引在位图中。|  
|[CToolBar::SetButtonStyle](../Topic/CToolBar::SetButtonStyle.md)|设置按钮的样式。|  
|[CToolBar::SetButtonText](../Topic/CToolBar::SetButtonText.md)|设置要显示在按钮的文本。|  
|[CToolBar::SetHeight](../Topic/CToolBar::SetHeight.md)|设置工具栏按钮的高度。|  
|[CToolBar::SetSizes](../Topic/CToolBar::SetSizes.md)|将按钮及其位图的大小。|  
  
## 备注  
 按钮可以象普通按钮、复选框按钮、单选按钮。  `CToolBar` 对象通常是框架窗口对象的嵌入成员从选件类派生的 [CFrameWnd](../../mfc/reference/cframewnd-class.md) 或 [CMDIFrameWnd](../../mfc/reference/cmdiframewnd-class.md)。  
  
 [CToolBar::GetToolBarCtrl](../Topic/CToolBar::GetToolBarCtrl.md)，成员函数新MFC 4.0，使您可以利用公共控件为"自定义工具栏和其他功能支持的Windows。  `CToolBar` 成员函数最提供了Windows公共控件的功能;但是，那么，当您调用 `GetToolBarCtrl`时，可以为工具栏Windows 95的特性\/98工具栏。  当您调用 `GetToolBarCtrl`，它将返回对 `CToolBarCtrl` 对象。  使用Windows公共控件，请参见 [CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md) 有关设计工具栏的更多信息。  有关公共控件的信息，请参见 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的 [公共控件](http://msdn.microsoft.com/library/windows/desktop/bb775493)。  
  
 Visual C\+\+提供了两个方法创建工具栏。  使用资源编辑器，若要创建工具栏资源，请执行以下步骤:  
  
1.  创建一个工具栏资源。  
  
2.  构造 `CToolBar` 对象。  
  
3.  调用 [创建](../Topic/CToolBar::Create.md) \(或 [CreateEx](../Topic/CToolBar::CreateEx.md)\)函数创建Windows工具栏并将其附加到 `CToolBar` 对象。  
  
4.  调用 [LoadToolBar](../Topic/CToolBar::LoadToolBar.md) 加载工具栏资源。  
  
 否则，请执行以下步骤：  
  
1.  构造 `CToolBar` 对象。  
  
2.  调用 [创建](../Topic/CToolBar::Create.md) \(或 [CreateEx](../Topic/CToolBar::CreateEx.md)\)函数创建Windows工具栏并将其附加到 `CToolBar` 对象。  
  
3.  调用 [LoadBitmap](../Topic/CToolBar::LoadBitmap.md) 加载包含工具栏按钮图像的位图。  
  
4.  调用 [SetButtons](../Topic/CToolBar::SetButtons.md) 设置按钮样式和将每个按钮与位图的图像。  
  
 在工具栏的所有按钮图像从一个位图执行，必须包含每个按钮的图像。  所有图像必须大小相同;默认值为宽16像素、高15像素的。  图像必须是与位图。  
  
 `SetButtons` 函数采用指向该数组指定元素的数量的控件ID和整数。  函数将每个按钮的ID设置为数组的对应元素的值并将每个按钮图像索引，在位图指定按钮的图像位置。  如果数组的元素具有值 **ID\_SEPARATOR**，图像索引未指派。  
  
 图像的顺序在位图中通常是它们在屏幕上绘制的顺序，但是，可以使用 [SetButtonInfo](../Topic/CToolBar::SetButtonInfo.md) 功能更改图像序列和绘图命令之间的关系。  
  
 在工具栏中的任何按钮大小相同。  默认值为24 x 22像素，且 *Windows软件设计接口的准则匹配*。  在图像和按钮维数之间的任何其他的空间用于在图像周围窗体边框。  
  
 每个按钮都有一个图像。  各种按钮状态和样式\(按下，下，禁用，禁用滚动，并且不确定\)从一个图像生成。  虽然位图可以是任何颜色，可以在使用图像的最佳结果以灰色黑色和亮度。  
  
> [!WARNING]
>  `CToolBar` 支持具有最多的位图16种颜色。  在加载图像到工具栏编辑器中，如有必要，Visual Studio会自动将图像转换为16色位图，并显示警告消息已转换，则图像。  如果使用具有16个以上的颜色的图像\(使用编辑的外部编辑图像\)，应用程序可能意外行为。  
  
 默认情况下工具栏按钮按普通按钮。  但是，工具栏按钮也可以遵循复选框按钮或单选按钮。  复选框按钮有三种状态:检查，清除，并且不确定。  单选按钮只有两个状态:检查和清除。  
  
 若要设置单个按钮或分隔符样式，而无需指向数组，请调用 [GetButtonStyle](../Topic/CToolBar::GetButtonStyle.md) 检索该样式，然后调用 [SetButtonStyle](../Topic/CToolBar::SetButtonStyle.md) 而不是 `SetButtons`。  在要更改按钮的样式在运行时，`SetButtonStyle` 最为有用。  
  
 若要分配文本显示在按钮，请调用 [GetButtonText](../Topic/CToolBar::GetButtonText.md) 检索文本显示在按钮，然后调用 [SetButtonText](../Topic/CToolBar::SetButtonText.md) 设置文本。  
  
 若要创建复选框按钮，请将其分配为样式 **TBBS\_CHECKBOX** 或使用 `CCmdUI` 对象的 `SetCheck` 成员函数在 `ON_UPDATE_COMMAND_UI` 处理程序。  调用 `SetCheck` 具有普通按钮变成复选框按钮。  通过 `SetCheck` 参数0取消选中，1检查的或2不确定。  
  
 若要创建单选按钮，请调用 [CCmdUI](../../mfc/reference/ccmdui-class.md) 对象的 [SetRadio](../Topic/CCmdUI::SetRadio.md) 从 `ON_UPDATE_COMMAND_UI` 处理程序的成员函数。  通过 `SetRadio` 参数0无检查或非零的检查的。  为了提供无线组的互斥的行为，必须在具有所有的 `ON_UPDATE_COMMAND_UI` 处理程序按钮。  
  
 有关使用 `CToolBar`的更多信息，请参见文章 [MFC工具栏实现](../../mfc/mfc-toolbar-implementation.md) 和 [技术说明31:控制条](../../mfc/tn031-control-bars.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CControlBar](../../mfc/reference/ccontrolbar-class.md)  
  
 `CToolBar`  
  
## 要求  
 **Header:** afxext.h  
  
## 请参阅  
 [MFC示例CTRLBARS](../../top/visual-cpp-samples.md)   
 [MFC DLGCBR32示例](../../top/visual-cpp-samples.md)   
 [MFC DOCKTOOL示例](../../top/visual-cpp-samples.md)   
 [CControlBar Class](../../mfc/reference/ccontrolbar-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CToolBarCtrl Class](../../mfc/reference/ctoolbarctrl-class.md)   
 [CControlBar Class](../../mfc/reference/ccontrolbar-class.md)   
 [CToolBar::Create](../Topic/CToolBar::Create.md)   
 [CToolBar::LoadBitmap](../Topic/CToolBar::LoadBitmap.md)   
 [CToolBar::SetButtons](../Topic/CToolBar::SetButtons.md)   
 [CCmdUI::SetCheck](../Topic/CCmdUI::SetCheck.md)   
 [CCmdUI::SetRadio](../Topic/CCmdUI::SetRadio.md)
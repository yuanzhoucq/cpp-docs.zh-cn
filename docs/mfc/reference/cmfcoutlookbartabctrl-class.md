---
title: "CMFCOutlookBarTabCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCOutlookBarTabCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCOutlookBarTabCtrl class"
ms.assetid: b1f2b3f7-cc59-49a3-99d8-7ff9b37c044b
caps.latest.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 28
---
# CMFCOutlookBarTabCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

具有 **导航窗格** 可视外观Microsoft Outlook的可选控件。  
  
## 语法  
  
```  
class CMFCOutlookBarTabCtrl : public CMFCBaseTabCtrl  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|`CMFCOutlookBarTabCtrl::CMFCOutlookBarTabCtrl`|默认构造函数。|  
|`CMFCOutlookBarTabCtrl::~CMFCOutlookBarTabCtrl`|析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCOutlookBarTabCtrl::AddControl](../Topic/CMFCOutlookBarTabCtrl::AddControl.md)|添加一个Windows控件为Outlook栏的新选项卡。|  
|`CMFCOutlookBarTabCtrl::CalcRectEdit`|调用由框架确定显示编辑框的尺寸当用户对一个选项重命名。  （重写 `CMFCBaseTabCtrl::CalcRectEdit`。）|  
|[CMFCOutlookBarTabCtrl::CanShowFewerPageButtons](../Topic/CMFCOutlookBarTabCtrl::CanShowFewerPageButtons.md)|调用由框架在调整操作期间确定少Outlook栏选项页"按钮是否可以显示比当前的可见。|  
|[CMFCOutlookBarTabCtrl::CanShowMorePageButtons](../Topic/CMFCOutlookBarTabCtrl::CanShowMorePageButtons.md)|调用由框架在调整操作期间确定更多Outlook栏选项页"按钮是否可以显示比当前的可见。|  
|[CMFCOutlookBarTabCtrl::Create](../Topic/CMFCOutlookBarTabCtrl::Create.md)|创建Outlook栏选项卡控件。|  
|`CMFCOutlookBarTabCtrl::CreateObject`|用于由框架创建此选件类类型动态实例。|  
|[CMFCOutlookBarTabCtrl::EnableAnimation](../Topic/CMFCOutlookBarTabCtrl::EnableAnimation.md)|指定将在活动选项卡之间切换期间的动画是否启用。|  
|[CMFCOutlookBarTabCtrl::EnableInPlaceEdit](../Topic/CMFCOutlookBarTabCtrl::EnableInPlaceEdit.md)|指定用户是否可以修改在Outlook栏的选项按钮的文本标签。  （重写 [CMFCBaseTabCtrl::EnableInPlaceEdit](../Topic/CMFCBaseTabCtrl::EnableInPlaceEdit.md)。）|  
|[CMFCOutlookBarTabCtrl::EnableScrollButtons](../Topic/CMFCOutlookBarTabCtrl::EnableScrollButtons.md)|调用由框架启用允许用户通过在Outlook栏窗格的按钮移动的按钮。|  
|`CMFCOutlookBarTabCtrl::FindTargetWnd`|确定包含指定的点窗格。  （重写 [CMFCBaseTabCtrl::FindTargetWnd](../Topic/CMFCBaseTabCtrl::FindTargetWnd.md)。）|  
|[CMFCOutlookBarTabCtrl::GetBorderSize](../Topic/CMFCOutlookBarTabCtrl::GetBorderSize.md)|返回Outlook选项卡控件的边框大小。|  
|`CMFCOutlookBarTabCtrl::GetTabArea`|检索选项卡控件的选项范围的大小和位置。  （重写 [CMFCBaseTabCtrl::GetTabArea](../Topic/CMFCBaseTabCtrl::GetTabArea.md)。）|  
|`CMFCOutlookBarTabCtrl::GetThisClass`|用于由框架获取指向与此选件类类型的 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 对象。|  
|[CMFCOutlookBarTabCtrl::GetVisiblePageButtons](../Topic/CMFCOutlookBarTabCtrl::GetVisiblePageButtons.md)||  
|[CMFCOutlookBarTabCtrl::IsAnimation](../Topic/CMFCOutlookBarTabCtrl::IsAnimation.md)|确定发生在活动选项卡之间切换期间的动画是否启用。|  
|[CMFCOutlookBarTabCtrl::IsMode2003](../Topic/CMFCOutlookBarTabCtrl::IsMode2003.md)|确定Outlook栏选项卡控件是否在模拟Microsoft Outlook 2003中的模式。|  
|`CMFCOutlookBarTabCtrl::IsPtInTabArea`|确定一个点是否位于可选区域内。  （重写 [CMFCBaseTabCtrl::IsPtInTabArea](../Topic/CMFCBaseTabCtrl::IsPtInTabArea.md)。）|  
|`CMFCOutlookBarTabCtrl::IsTabDetachable`|确定选择是可拆的。  （重写 [CMFCBaseTabCtrl::IsTabDetachable](../Topic/CMFCBaseTabCtrl::IsTabDetachable.md)。）|  
|`CMFCOutlookBarTabCtrl::OnChangeTabs`|调用由结构，在插入选项或移除。  （重写 `CMFCBaseTabCtrl::OnChangeTabs`。）|  
|[CMFCOutlookBarTabCtrl::OnShowFewerPageButtons](../Topic/CMFCOutlookBarTabCtrl::OnShowFewerPageButtons.md)|调用由框架选项有所减少可见的页按钮数。|  
|[CMFCOutlookBarTabCtrl::OnShowMorePageButtons](../Topic/CMFCOutlookBarTabCtrl::OnShowMorePageButtons.md)|调用由框架增加选项可见的页按钮数。|  
|[CMFCOutlookBarTabCtrl::OnShowOptions](../Topic/CMFCOutlookBarTabCtrl::OnShowOptions.md)|显示 **导航窗格选项** 对话框。|  
|`CMFCOutlookBarTabCtrl::RecalcLayout`|计算选项卡控件的内部格式。  （重写 [CMFCBaseTabCtrl::RecalcLayout](../Topic/CMFCBaseTabCtrl::RecalcLayout.md)。）|  
|[CMFCOutlookBarTabCtrl::SetActiveTab](../Topic/CMFCOutlookBarTabCtrl::SetActiveTab.md)|设置活动选项卡。  （重写 [CMFCBaseTabCtrl::SetActiveTab](../Topic/CMFCBaseTabCtrl::SetActiveTab.md)。）|  
|[CMFCOutlookBarTabCtrl::SetBorderSize](../Topic/CMFCOutlookBarTabCtrl::SetBorderSize.md)|设置Outlook选项卡控件的边框大小。|  
|[CMFCOutlookBarTabCtrl::SetPageButtonTextAlign](../Topic/CMFCOutlookBarTabCtrl::SetPageButtonTextAlign.md)|设置文本标签的对齐方式在Outlook栏的选项按钮的。|  
|[CMFCOutlookBarTabCtrl::SetToolbarImageList](../Topic/CMFCOutlookBarTabCtrl::SetToolbarImageList.md)|设置包含该图标在Outlook栏底部显示在Outlook 2003架构的位图\(请参见 [CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md)）。|  
|[CMFCOutlookBarTabCtrl::SetVisiblePageButtons](../Topic/CMFCOutlookBarTabCtrl::SetVisiblePageButtons.md)||  
  
## 备注  
 若要创建Outlook请禁止封送处理停靠支持，使用 `CMFCOutlookBar` 对象承载Outlook栏选项卡控件。  有关更多信息，请参见 [CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md)。  
  
## 示例  
 下面的示例演示如何初始化 `CMFCOutlookBarTabCtrl` 对象，并使用各种方法在 `CMFCOutlookBarTabCtrl` 类中。  此示例演示如何启用就地编辑在Outlook栏的选项卡页按钮的文本标签，启用动画，启用使用户可以通过在Outlook栏窗格的按钮移动，设置Outlook选项卡控件的边框大小，并将文本标签对齐在Outlook栏的选项按钮的滚动处理。  此代码段是 [Outlook演示示例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_OutlookDemo#1](../../mfc/reference/codesnippet/CPP/cmfcoutlookbartabctrl-class_1.cpp)]  
[!code-cpp[NVC_MFC_OutlookDemo#2](../../mfc/reference/codesnippet/CPP/cmfcoutlookbartabctrl-class_2.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md)  
  
 [CMFCOutlookBarTabCtrl](../../mfc/reference/cmfcoutlookbartabctrl-class.md)  
  
## 要求  
 **标头:** afxoutlookbartabctrl.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCBaseTabCtrl Class](../../mfc/reference/cmfcbasetabctrl-class.md)   
 [CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md)   
 [CMFCOutlookBarPane Class](../../mfc/reference/cmfcoutlookbarpane-class.md)
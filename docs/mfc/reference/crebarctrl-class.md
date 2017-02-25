---
title: "CReBarCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CReBarCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CReBarCtrl class"
  - "rebar controls, control bar"
  - "rebar controls, CReBarCtrl class"
ms.assetid: 154570d7-e48c-425d-8c7e-c64542bcb4cc
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CReBarCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

封装rebar控件的功能，是子窗口的容器。  
  
## 语法  
  
```  
class CReBarCtrl : public CWnd  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CReBarCtrl::CReBarCtrl](../Topic/CReBarCtrl::CReBarCtrl.md)|构造 `CReBarCtrl` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CReBarCtrl::BeginDrag](../Topic/CReBarCtrl::BeginDrag.md)|将rebar控件拖放到模式。|  
|[CReBarCtrl::Create](../Topic/CReBarCtrl::Create.md)|创建rebar控件并将它附加到 `CReBarCtrl` 对象。|  
|[CReBarCtrl::CreateEx](../Topic/CReBarCtrl::CreateEx.md)|使用指定的Windows扩展的样式创建一个rebar控件并将它附加到 `CReBarCtrl` 对象。|  
|[CReBarCtrl::DeleteBand](../Topic/CReBarCtrl::DeleteBand.md)|从rebar控件删除带区。|  
|[CReBarCtrl::DragMove](../Topic/CReBarCtrl::DragMove.md)|在调用后更新在rebar控件的位置拖动到 `BeginDrag`。|  
|[CReBarCtrl::EndDrag](../Topic/CReBarCtrl::EndDrag.md)|停止rebar控件中的拖放操作。|  
|[CReBarCtrl::GetBandBorders](../Topic/CReBarCtrl::GetBandBorders.md)|检索带区的边框。|  
|[CReBarCtrl::GetBandCount](../Topic/CReBarCtrl::GetBandCount.md)|检索当前计数带区rebar控件的。|  
|[CReBarCtrl::GetBandInfo](../Topic/CReBarCtrl::GetBandInfo.md)|检索有关指定的条带的信息rebar控件的。|  
|[CReBarCtrl::GetBandMargins](../Topic/CReBarCtrl::GetBandMargins.md)|检索带区的边距。|  
|[CReBarCtrl::GetBarHeight](../Topic/CReBarCtrl::GetBarHeight.md)|检索rebar控件的高度。|  
|[CReBarCtrl::GetBarInfo](../Topic/CReBarCtrl::GetBarInfo.md)|检索有关rebar控件的信息，而图像列表它使用。|  
|[CReBarCtrl::GetBkColor](../Topic/CReBarCtrl::GetBkColor.md)|检索rebar控件的默认背景色。|  
|[CReBarCtrl::GetColorScheme](../Topic/CReBarCtrl::GetColorScheme.md)|检索 [COLORSCHEME](http://msdn.microsoft.com/library/windows/desktop/bb775502) 结构与rebar控件。|  
|[CReBarCtrl::GetDropTarget](../Topic/CReBarCtrl::GetDropTarget.md)|检索rebar控件的 `IDropTarget` 接口指针。|  
|[CReBarCtrl::GetExtendedStyle](../Topic/CReBarCtrl::GetExtendedStyle.md)|获取当前rebar控件的扩展样式。|  
|[CReBarCtrl::GetImageList](../Topic/CReBarCtrl::GetImageList.md)|检索图像列表与rebar控件。|  
|[CReBarCtrl::GetPalette](../Topic/CReBarCtrl::GetPalette.md)|检索rebar控件的当前调色板。|  
|[CReBarCtrl::GetRect](../Topic/CReBarCtrl::GetRect.md)|检索特定带区的边框rebar控件的。|  
|[CReBarCtrl::GetRowCount](../Topic/CReBarCtrl::GetRowCount.md)|检索带区的行数在rebar控件的。|  
|[CReBarCtrl::GetRowHeight](../Topic/CReBarCtrl::GetRowHeight.md)|检索指定的行的高度\(以rebar控件的。|  
|[CReBarCtrl::GetTextColor](../Topic/CReBarCtrl::GetTextColor.md)|检索rebar控件的默认文本颜色。|  
|[CReBarCtrl::GetToolTips](../Topic/CReBarCtrl::GetToolTips.md)|检索处理的所有工具提示控件与rebar控件。|  
|[CReBarCtrl::HitTest](../Topic/CReBarCtrl::HitTest.md)|确定rebar带区的哪一部分是在给定的点在屏幕上，rebar带区，如果当时存在。|  
|[CReBarCtrl::IDToIndex](../Topic/CReBarCtrl::IDToIndex.md)|将带区标识符\(ID\)为rebar控件的一个带区索引。|  
|[CReBarCtrl::InsertBand](../Topic/CReBarCtrl::InsertBand.md)|插入新的条带在rebar控件。|  
|[CReBarCtrl::MaximizeBand](../Topic/CReBarCtrl::MaximizeBand.md)|调整rebar控件的一个带区到它的最大大小。|  
|[CReBarCtrl::MinimizeBand](../Topic/CReBarCtrl::MinimizeBand.md)|调整rebar控件的一个带区为其最小大小。|  
|[CReBarCtrl::MoveBand](../Topic/CReBarCtrl::MoveBand.md)|从索引将带区到另一个。|  
|[CReBarCtrl::PushChevron](../Topic/CReBarCtrl::PushChevron.md)|以编程方式驱动器V形。|  
|[CReBarCtrl::RestoreBand](../Topic/CReBarCtrl::RestoreBand.md)|调整rebar控件的一个带区到其需要的范围。|  
|[CReBarCtrl::SetBandInfo](../Topic/CReBarCtrl::SetBandInfo.md)|将现有带区的属性rebar控件的。|  
|[CReBarCtrl::SetBandWidth](../Topic/CReBarCtrl::SetBandWidth.md)|设置指定的停靠的带区在变宽当前rebar控件的。|  
|[CReBarCtrl::SetBarInfo](../Topic/CReBarCtrl::SetBarInfo.md)|设置rebar控件的属性。|  
|[CReBarCtrl::SetBkColor](../Topic/CReBarCtrl::SetBkColor.md)|设置rebar控件的默认背景色。|  
|[CReBarCtrl::SetColorScheme](../Topic/CReBarCtrl::SetColorScheme.md)|设置按钮的配色方案在rebar控件。|  
|[CReBarCtrl::SetExtendedStyle](../Topic/CReBarCtrl::SetExtendedStyle.md)|设置当前rebar控件的扩展样式。|  
|[CReBarCtrl::SetImageList](../Topic/CReBarCtrl::SetImageList.md)|设置rebar控件的图像列表。|  
|[CReBarCtrl::SetOwner](../Topic/CReBarCtrl::SetOwner.md)|设置rebar控件的所有者窗口。|  
|[CReBarCtrl::SetPalette](../Topic/CReBarCtrl::SetPalette.md)|设置rebar控件的当前调色板。|  
|[CReBarCtrl::SetTextColor](../Topic/CReBarCtrl::SetTextColor.md)|设置rebar控件的默认文本颜色。|  
|[CReBarCtrl::SetToolTips](../Topic/CReBarCtrl::SetToolTips.md)|关联工具提示控件与rebar控件。|  
|[CReBarCtrl::SetWindowTheme](../Topic/CReBarCtrl::SetWindowTheme.md)|设置rebar控件的视觉样式。|  
|[CReBarCtrl::ShowBand](../Topic/CReBarCtrl::ShowBand.md)|显示或隐藏rebar控件的特定带区。|  
|[CReBarCtrl::SizeToRect](../Topic/CReBarCtrl::SizeToRect.md)|有关rebar控件移动到指定的矩形。|  
  
## 备注  
 rebar控件所在的应用程序分配rebar控件中包含的子窗口为rebar带区。  子窗口通常是另一个公共控件。  
  
 Rebar控件包含一个或多个带区。  每个带区可以包含手柄栏、位图、文本标签和子窗口的组合。  带区只能包含一个项目中的每一个。  
  
 rebar控件可以显示在指定的背景位图的子窗口。  所有rebar控件大小可调整大小，但所使用 **RBBS\_FIXEDSIZE** 样式的类型。  因为您重新定位或调整一个rebar控件大小，rebar控件管理子窗口的大小和位置分配给该条带。  调整或更改命令带区在控件中，单击中的并将带区的手柄条。  
  
 下图显示了带有三个带区的一个rebar控件:  
  
-   带区0包含平缓，透明工具栏控件。  
  
-   带区1包含透明标准和透明下拉式按钮。  
  
-   带区2包含组合框和四个标准按钮。  
  
     ![Rebar 菜单示例](../../mfc/reference/media/vc4scc1.png "vc4SCC1")  
  
## Rebar控件  
 Rebar控件支持的:  
  
-   图像列表。  
  
-   消息处理。  
  
-   自定义绘制功能。  
  
-   除了标准窗口样式以外的各种控件样式。  有关这些样式列表，请参见。[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的 [Rebar控件样式](http://msdn.microsoft.com/library/windows/desktop/bb774377)。  
  
 有关更多信息，请参见 [使用CReBarCtrl](../../mfc/using-crebarctrl.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CReBarCtrl`  
  
## 要求  
 **Header:** afxcmn.h  
  
## 请参阅  
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)
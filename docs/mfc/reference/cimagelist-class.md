---
title: "CImageList Class | Microsoft Docs"
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
  - "CImageList"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CImageList class"
  - "image lists [C++], CImageList class"
  - "Windows common controls [C++], CImageList"
ms.assetid: b6d1a704-1c82-4548-8a8f-77972adc98a5
caps.latest.revision: 19
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CImageList Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供常见图像列表控件Windows的功能。  
  
## 语法  
  
```  
class CImageList : public CObject  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CImageList::CImageList](../Topic/CImageList::CImageList.md)|构造 `CImageList` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CImageList::Add](../Topic/CImageList::Add.md)|添加一个图像或对图形图像列表。|  
|[CImageList::Attach](../Topic/CImageList::Attach.md)|附加图像列表。`CImageList` 对象。|  
|[CImageList::BeginDrag](../Topic/CImageList::BeginDrag.md)|将图像的Begins。|  
|[CImageList::Copy](../Topic/CImageList::Copy.md)|复制在 `CImageList` 对象中的图像。|  
|[CImageList::Create](../Topic/CImageList::Create.md)|初始化图像列表并将它附加到 `CImageList` 对象。|  
|[CImageList::DeleteImageList](../Topic/CImageList::DeleteImageList.md)|删除图像列表。|  
|[CImageList::DeleteTempMap](../Topic/CImageList::DeleteTempMap.md)|调用 [CWinApp](../../mfc/reference/cwinapp-class.md) 空闲时间处理程序删除 `FromHandle`创建的任何临时 `CImageList` 对象。|  
|[CImageList::Detach](../Topic/CImageList::Detach.md)|离散图形列表从 `CImageList` 对象的对象并将处理返回到图像列表。|  
|[CImageList::DragEnter](../Topic/CImageList::DragEnter.md)|在拖动操作并显示期间锁更新拖动图像在指定的位置。|  
|[CImageList::DragLeave](../Topic/CImageList::DragLeave.md)|打开窗口并隐藏拖动图像，使窗口可以进行更新。|  
|[CImageList::DragMove](../Topic/CImageList::DragMove.md)|将在拖放操作过程中拖动的图像。|  
|[CImageList::DragShowNolock](../Topic/CImageList::DragShowNolock.md)|显示或隐藏拖动图像在拖动操作过程中，不锁定窗口。|  
|[CImageList::Draw](../Topic/CImageList::Draw.md)|绘制在拖放操作过程中拖动的图像。|  
|[CImageList::DrawEx](../Topic/CImageList::DrawEx.md)|在指定的设备上下文绘制图像列表项。  函数使用指定的绘制的样式并与指定的颜色相混合图像。|  
|[CImageList::DrawIndirect](../Topic/CImageList::DrawIndirect.md)|从图像绘制图像列表。|  
|[CImageList::EndDrag](../Topic/CImageList::EndDrag.md)|关闭拖动操作。|  
|[CImageList::ExtractIcon](../Topic/CImageList::ExtractIcon.md)|创建基于图像的图标，并在图像的掩码列表。|  
|[CImageList::FromHandle](../Topic/CImageList::FromHandle.md)|返回指向 `CImageList` 对象，同时使处理图像列表。  如果一 `CImageList` 对象未附加到句柄，一个临时 `CImageList` 对象创建并附加。|  
|[CImageList::FromHandlePermanent](../Topic/CImageList::FromHandlePermanent.md)|返回指向 `CImageList` 对象，同时使处理图像列表。  如果一 `CImageList` 对象不依赖于处理，**NULL** 返回。|  
|[CImageList::GetBkColor](../Topic/CImageList::GetBkColor.md)|检索图像的当前背景色列表。|  
|[CImageList::GetDragImage](../Topic/CImageList::GetDragImage.md)|获取用于将使用的临时图像列表。|  
|[CImageList::GetImageCount](../Topic/CImageList::GetImageCount.md)|检索图像数在图像的列表。|  
|[CImageList::GetImageInfo](../Topic/CImageList::GetImageInfo.md)|检索有关图像的信息。|  
|[CImageList::GetSafeHandle](../Topic/CImageList::GetSafeHandle.md)|检索 **m\_hImageList**。|  
|[CImageList::Read](../Topic/CImageList::Read.md)|读取一个图像从存档列表。|  
|[CImageList::Remove](../Topic/CImageList::Remove.md)|从图像移除图像列表。|  
|[CImageList::Replace](../Topic/CImageList::Replace.md)|替换图像中的一个图像列表与新图像。|  
|[CImageList::SetBkColor](../Topic/CImageList::SetBkColor.md)|设置图像的背景颜色列表。|  
|[CImageList::SetDragCursorImage](../Topic/CImageList::SetDragCursorImage.md)|生成一个新的拖动图像。|  
|[CImageList::SetImageCount](../Topic/CImageList::SetImageCount.md)|重置计数图像中的图像列表。|  
|[CImageList::SetOverlayImage](../Topic/CImageList::SetOverlayImage.md)|添加图像的从零开始的索引。要使用的图像列表复盖率掩码。|  
|[CImageList::Write](../Topic/CImageList::Write.md)|图像列表到存档的写访问权。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CImageList::operator HIMAGELIST](../Topic/CImageList::operator%20HIMAGELIST.md)|返回 `HIMAGELIST` 附加到 `CImageList`。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CImageList::m\_hImageList](../Topic/CImageList::m_hImageList.md)|包含图像的处理列表附加到该对象。|  
  
## 备注  
 “图像列表”相同大小图像的集合，每个可由其从零开始的索引来引用。  图像列表使用有效地管理大量图标或位图。  在图像的任何图像列表在单个宽，位图包含在屏幕设备格式。  图像列表可能还包含用于掩码透明地绘制图像中的单色位图\(图标\)样式。  Microsoft Win32应用程序编程接口\(API\)提供图像列表允许您绘制图像，创建，并销毁图像列表，添加和移除图像，替换图像，将图像，并将图像的功能。  
  
 此控件\(并 `CImageList` 选件类\)若要在运行Windows 95 \/98和Windows NT 3.51版下的程序可用和更高版本。  
  
 有关使用 `CImageList`的更多信息，请参见 [控件](../../mfc/controls-mfc.md) 和 [使用CImageList](../../mfc/using-cimagelist.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CImageList`  
  
## 要求  
 **Header:** afxcmn.h  
  
## 请参阅  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CListCtrl Class](../../mfc/reference/clistctrl-class.md)   
 [CTabCtrl Class](../../mfc/reference/ctabctrl-class.md)
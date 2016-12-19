---
title: "CMFCDynamicLayout 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
ms.assetid: c2df2976-f049-47fc-9cf0-abe3e01948bc
caps.latest.revision: 16
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCDynamicLayout 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定窗口中的控件如何随着用户重设窗口大小而移动和重设大小。  
  
## 语法  
  
```  
class CMFCDynamicLayout : public CObject  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|`CMFCDynamicLayout::CMFCDynamicLayout`|构造 `CMFCDynamicLayout` 对象。|  
|`CMFCDynamicLayout::~CMFCDynamicLayout`|析构函数。|  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[CMFCDynamicLayout::AddItem](../Topic/CMFCDynamicLayout::AddItem.md)|将子窗口（通常是控件）添加到由动态布局管理器控制的窗口的列表。|  
|[CMFCDynamicLayout::Adjust](../Topic/CMFCDynamicLayout::Adjust.md)|将子窗口（通常是控件）添加到由动态布局管理器控制的窗口的列表。|  
|[CMFCDynamicLayout::Create](../Topic/CMFCDynamicLayout::Create.md)|存储并验证主机窗口。|  
|[CMFCDynamicLayout::GetHostWnd](../Topic/CMFCDynamicLayout::GetHostWnd.md)|返回指向主机窗口的指针。|  
|[CMFCDynamicLayout::GetMinSize](../Topic/CMFCDynamicLayout::GetMinSize.md)|返回窗口大小，低于此大小则不调整布局。|  
|[CMFCDynamicLayout::GetWindowRect](../Topic/CMFCDynamicLayout::GetWindowRect.md)|检索窗口的当前工作区的矩形。|  
|[CMFCDynamicLayout::HasItem](../Topic/CMFCDynamicLayout::HasItem.md)|检查子控件是否已添加到动态布局。|  
|[CMFCDynamicLayout::IsEmpty](../Topic/CMFCDynamicLayout::IsEmpty.md)|检查动态布局是否未添加任何子窗口。|  
|[CMFCDynamicLayout::LoadResource](../Topic/CMFCDynamicLayout::LoadResource.md)|从 AFX\_DIALOG\_LAYOUT 资源读取动态布局，然后将该布局应用到主机窗口。|  
|静态 [CMFCDynamicLayout::MoveHorizontal](../Topic/CMFCDynamicLayout::MoveHorizontal.md)|获取一个 [MoveSettings](../Topic/CMFCDynamicLayout::MoveSettings%20Structure.md) 值，该值定义在用户调整其承载窗口大小时水平移动子控件的距离。|  
|静态 [CMFCDynamicLayout::MoveHorizontalAndVertical](../Topic/CMFCDynamicLayout::MoveHorizontalAndVertical.md)|获取一个 [MoveSettings](../Topic/CMFCDynamicLayout::MoveSettings%20Structure.md) 值，该值定义在用户调整其承载窗口大小时水平移动子控件的距离。|  
|静态 [CMFCDynamicLayout::MoveNone](../Topic/CMFCDynamicLayout::MoveNone.md)|获取一个 [MoveSettings](../Topic/CMFCDynamicLayout::MoveSettings%20Structure.md) 值，该值表示子控件不移动（垂直或水平）。|  
|静态 [CMFCDynamicLayout::MoveVertical](../Topic/CMFCDynamicLayout::MoveVertical.md)|获取一个 [MoveSettings](../Topic/CMFCDynamicLayout::MoveSettings%20Structure.md) 值，该值定义在用户调整其承载窗口大小时垂直移动子控件的距离。|  
|[CMFCDynamicLayout::SetMinSize](../Topic/CMFCDynamicLayout::SetMinSize.md)|设置窗口大小，低于此大小则不调整布局。|  
|静态 [CMFCDynamicLayout::SizeHorizontal](../Topic/CMFCDynamicLayout::SizeHorizontal.md)|获取一个 [SizeSettings](../Topic/CMFCDynamicLayout::SizeSettings%20Structure.md) 值，该值定义在用户调整其承载窗口大小时水平调整子控件的程度。|  
|静态 [CMFCDynamicLayout::SizeHorizontalAndVertical](../Topic/CMFCDynamicLayout::SizeHorizontalAndVertical.md)|获取一个 [SizeSettings](../Topic/CMFCDynamicLayout::SizeSettings%20Structure.md) 值，该值定义在用户调整其承载窗口大小时水平调整子控件的程度。|  
|静态 [CMFCDynamicLayout::SizeNone](../Topic/CMFCDynamicLayout::SizeNone.md)|获取一个 [SizeSettings](../Topic/CMFCDynamicLayout::SizeSettings%20Structure.md) 值，该值表示子控件的大小不会更改。|  
|静态 [CMFCDynamicLayout::SizeVertical](../Topic/CMFCDynamicLayout::SizeVertical.md)|获取一个 [SizeSettings](../Topic/CMFCDynamicLayout::SizeSettings%20Structure.md) 值，该值定义在用户调整其承载窗口大小时垂直调整子控件的程度。|  
  
## 嵌套类型  
  
|名称|描述|  
|--------|--------|  
|[CMFCDynamicLayout::MoveSettings 结构](../Topic/CMFCDynamicLayout::MoveSettings%20Structure.md)|封装动态布局中控件的移动数据。|  
|[CMFCDynamicLayout::SizeSettings 结构](../Topic/CMFCDynamicLayout::SizeSettings%20Structure.md)|封装动态布局中控件的大小更改数据。|  
  
## 备注  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCDynamicLayout](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
## 要求  
 **标头：**afxlayout.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)
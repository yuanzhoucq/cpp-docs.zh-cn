---
title: "CMFCPropertySheet Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCPropertySheet"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCPropertySheet class"
  - "CMFCPropertySheet::OnInitDialog method"
  - "CMFCPropertySheet::PreTranslateMessage method"
ms.assetid: 01d93573-9698-440f-a6a4-5bebbee879dc
caps.latest.revision: 35
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 37
---
# CMFCPropertySheet Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCPropertySheet` 类支持每个属性页由页选项卡、工具栏按钮、树控件节点或列表项表示的属性表。  
  
## 语法  
  
```  
class CMFCPropertySheet : public CPropertySheet  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMFCPropertySheet::CMFCPropertySheet](../Topic/CMFCPropertySheet::CMFCPropertySheet.md)|构造 `CMFCPropertySheet` 对象。|  
|`CMFCPropertySheet::~CMFCPropertySheet`|析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCPropertySheet::AddPage](../Topic/CMFCPropertySheet::AddPage.md)|向属性表添加页面。|  
|[CMFCPropertySheet::AddPageToTree](../Topic/CMFCPropertySheet::AddPageToTree.md)|向树控件添加新的属性页。|  
|[CMFCPropertySheet::AddTreeCategory](../Topic/CMFCPropertySheet::AddTreeCategory.md)|向树控件添加新节点。|  
|[CMFCPropertySheet::EnablePageHeader](../Topic/CMFCPropertySheet::EnablePageHeader.md)|在每个页面顶部保留一定空间，用于绘制自定义页眉。|  
|[CMFCPropertySheet::GetHeaderHeight](../Topic/CMFCPropertySheet::GetHeaderHeight.md)|检索当前页眉的高度。|  
|[CMFCPropertySheet::GetLook](../Topic/CMFCPropertySheet::GetLook.md)|检索一个枚举值，该值指定当前属性表的外观。|  
|[CMFCPropertySheet::GetNavBarWidth](../Topic/CMFCPropertySheet::GetNavBarWidth.md)|检索导航栏的宽度（以像素为单位）。|  
|[CMFCPropertySheet::GetTab](../Topic/CMFCPropertySheet::GetTab.md)|检索支持当前属性表控件的内部选项卡控件对象。|  
|`CMFCPropertySheet::GetThisClass`|由框架用于获取指向与此类类型关联的 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 对象的指针。|  
|[CMFCPropertySheet::InitNavigationControl](../Topic/CMFCPropertySheet::InitNavigationControl.md)|初始化当前属性表控件的外观。|  
|[CMFCPropertySheet::OnActivatePage](../Topic/CMFCPropertySheet::OnActivatePage.md)|当属性页处于启用状态时由框架调用。|  
|[CMFCPropertySheet::OnDrawPageHeader](../Topic/CMFCPropertySheet::OnDrawPageHeader.md)|由框架调用，用于绘制自定义属性页页眉。|  
|`CMFCPropertySheet::OnInitDialog`|处理 [WM\_INITDIALOG](http://msdn.microsoft.com/library/windows/desktop/ms645428) 消息。  （替代 [CPropertySheet::OnInitDialog](../Topic/CPropertySheet::OnInitDialog.md)。）|  
|[CMFCPropertySheet::OnRemoveTreePage](../Topic/CMFCPropertySheet::OnRemoveTreePage.md)|由框架调用，用于从树控件中删除属性页。|  
|`CMFCPropertySheet::PreTranslateMessage`|在窗口消息被分派到 [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) 和 [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows 函数之前，对其进行转换。  （重写 `CPropertySheet::PreTranslateMessage`。）|  
|[CMFCPropertySheet::RemoveCategory](../Topic/CMFCPropertySheet::RemoveCategory.md)|从树控件中删除节点。|  
|[CMFCPropertySheet::RemovePage](../Topic/CMFCPropertySheet::RemovePage.md)|从属性表中删除属性页。|  
|[CMFCPropertySheet::SetIconsList](../Topic/CMFCPropertySheet::SetIconsList.md)|指定用于 Outlook 窗格的导航控件的图像列表。|  
|[CMFCPropertySheet::SetLook](../Topic/CMFCPropertySheet::SetLook.md)|指定属性表的外观。|  
  
## 备注  
 `CMFCPropertySheet` 类表示属性表，也称为选项卡对话框。  `CMFCPropertySheet` 类可以用多种方式显示属性页。  
  
 执行以下步骤，以便在应用程序中使用 `CMFCPropertySheet` 类：  
  
1.  从 `CMFCPropertySheet` 类派生一个类，并对其命名，例如，CMyPropertySheet。  
  
2.  为每个属性页构造一个 [CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md) 对象。  
  
3.  调用 CMyPropertySheet 构造函数中的 [CMFCPropertySheet::SetLook](../Topic/CMFCPropertySheet::SetLook.md) 方法。  该方法的参数指定属性页的显示方式：属性表顶部或左侧的选项卡；Microsoft OneNote 属性表样式的选项卡；Microsoft Outlook 工具栏控件上的按钮；树控件上的节点；或属性表左侧的项列表。  
  
4.  如果创建 Microsoft Outlook 工具栏样式的属性表，则调用 [CMFCPropertySheet::SetIconsList](../Topic/CMFCPropertySheet::SetIconsList.md) 方法将一个图像列表与属性页关联。  
  
5.  为每个属性页调用 [CMFCPropertySheet::AddPage](../Topic/CMFCPropertySheet::AddPage.md) 方法。  
  
6.  创建 `CMFCPropertySheet` 控件并调用其 `DoModal` 方法。  
  
## 图示  
 下图描绘了一个采用嵌入式 Microsoft Outlook 工具栏样式的属性表。  该 Outlook 工具栏显示在属性表左侧。  
  
 ![CMFCPropertySheet 颜色控件](../../mfc/reference/media/cmfcpropertysheet_color.png "cmfcpropertysheet\_color")  
  
 下图描绘了一个包含 [CMFCPropertyGridCtrl Class](../../mfc/reference/cmfcpropertygridctrl-class.md) 对象的属性表。  该对象是一个采用标准常用控件属性表样式的属性表。  
  
 ![CMFCPropertySheet 列表和属性控件](../../mfc/reference/media/cmfcpropertysheet_list.png "cmfcpropertysheet\_list")  
  
 下图描绘了一个采用树控件样式的属性表。  
  
 ![属性树](../../mfc/reference/media/proptree.png "PropTree")  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CPropertySheet](../../mfc/reference/cpropertysheet-class.md)  
  
 [CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md)  
  
## 要求  
 **标头：**afxpropertysheet.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCPropertyPage Class](../../mfc/reference/cmfcpropertypage-class.md)   
 [CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md)
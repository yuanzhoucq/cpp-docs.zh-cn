---
title: "CMFCRibbonSeparator Class | Microsoft Docs"
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
  - "GetThisClass"
  - "CMFCRibbonSeparator::GetThisClass"
  - "CMFCRibbonSeparator.CreateObject"
  - "CMFCRibbonSeparator::CreateObject"
  - "CMFCRibbonSeparator"
  - "CreateObject"
  - "CMFCRibbonSeparator.GetThisClass"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonSeparator class"
  - "CreateObject method"
  - "GetThisClass method"
ms.assetid: bedb1a53-cb07-4c3c-be12-698c5409e7cf
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCRibbonSeparator Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

实现功能区分隔符。  
  
## 语法  
  
```  
class CMFCRibbonSeparator : public CMFCRibbonBaseElement  
```  
  
## 成员  
  
### 公共构造函数  
  
|||  
|-|-|  
|名称|说明|  
|[CMFCRibbonSeparator::CMFCRibbonSeparator](../Topic/CMFCRibbonSeparator::CMFCRibbonSeparator.md)|构造 `CMFCRibbonSeparator` 对象。|  
  
### 公共方法  
  
|||  
|-|-|  
|名称|说明|  
|[CMFCRibbonSeparator::AddToListBox](../Topic/CMFCRibbonSeparator::AddToListBox.md)|在 **自定义** 对话框添加一个分隔符到 **命令** 列表。  （重写 [CMFCRibbonBaseElement::AddToListBox](../Topic/CMFCRibbonBaseElement::AddToListBox.md)。）|  
|`CMFCRibbonSeparator::CreateObject`|用于由框架创建此选件类类型动态实例。|  
|`CMFCRibbonSeparator::GetThisClass`|用于由框架获取指向与此选件类类型的 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 对象。|  
  
### 受保护的方法  
  
|||  
|-|-|  
|名称|说明|  
|[CMFCRibbonSeparator::CopyFrom](../Topic/CMFCRibbonSeparator::CopyFrom.md)|设置分隔符的从其他对象的成员变量的副本方法。|  
|[CMFCRibbonSeparator::GetRegularSize](../Topic/CMFCRibbonSeparator::GetRegularSize.md)|返回分隔符的大小。|  
|[CMFCRibbonSeparator::IsSeparator](../Topic/CMFCRibbonSeparator::IsSeparator.md)|指示这是分隔符。|  
|[CMFCRibbonSeparator::IsTabStop](../Topic/CMFCRibbonSeparator::IsTabStop.md)|指示这是制表位。|  
|[CMFCRibbonSeparator::OnDraw](../Topic/CMFCRibbonSeparator::OnDraw.md)|调用由系统绘制功能区上或快速访问工具栏的分隔符。|  
|[CMFCRibbonSeparator::OnDrawOnList](../Topic/CMFCRibbonSeparator::OnDrawOnList.md)|调用由系统绘制在 **命令** 的分隔符列表。|  
  
## 备注  
 功能区分隔符是逻辑分离功能区元素的垂直或水平线条。  分隔符在功能区控件、主应用程序菜单、功能区状态栏和快速访问工具栏可以绘制。  
  
 若要使用分隔符在您的应用程序，请构造新的对象并将其添加到主应用程序菜单如下所示:  
  
```  
CMFCRibbonMainPanel* pMainPanel = m_wndRibbonBar.AddMainCategory(_T("Main Menu"), IDB_FILESMALL, IDB_FILELARGE);   
...  
pMainPanel->Add(new CMFCRibbonSeparator(TRUE));  
```  
  
 调用 [CMFCRibbonPanel::AddSeparator](../Topic/CMFCRibbonPanel::AddSeparator.md) 分隔符添加到功能区面板。  `AddSeparator` 方法内部分配分隔符并添加。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonSeparator](../../mfc/reference/cmfcribbonseparator-class.md)  
  
## 要求  
 **标头:** afxbaseribbonelement.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)
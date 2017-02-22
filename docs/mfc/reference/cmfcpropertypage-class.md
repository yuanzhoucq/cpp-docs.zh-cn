---
title: "CMFCPropertyPage Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCPropertyPage"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCPropertyPage class"
  - "CMFCPropertyPage::CreateObject method"
  - "CMFCPropertyPage::OnSetActive method"
  - "CMFCPropertyPage::PreTranslateMessage method"
ms.assetid: d279d7f2-2d81-418d-9f23-6147d6e8df09
caps.latest.revision: 30
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 32
---
# CMFCPropertyPage Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCPropertyPage` 选件类支持弹出菜单显示在属性页中。  
  
## 语法  
  
```  
class CMFCPropertyPage : public CPropertyPage  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMFCPropertyPage::CMFCPropertyPage](../Topic/CMFCPropertyPage::CMFCPropertyPage.md)|构造 `CMFCPropertyPage` 对象。|  
|`CMFCPropertyPage::~CMFCPropertyPage`|析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|`CMFCPropertyPage::CreateObject`|用于由框架创建此选件类类型动态实例。|  
|`CMFCPropertyPage::GetThisClass`|用于由框架获取指向与此选件类类型的 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 对象。|  
|`CMFCPropertyPage::OnSetActive`|当页由用户选择并成为活动页时，此成员函数由框架调用。  （重写 [CPropertyPage::OnSetActive](../Topic/CPropertyPage::OnSetActive.md)。）|  
|`CMFCPropertyPage::PreTranslateMessage`|在将调度到 [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) 和 [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows功能之前，将windows消息。  有关更多信息和方法语法，请参见 [CWnd::PreTranslateMessage](../Topic/CWnd::PreTranslateMessage.md)。  （重写 `CPropertyPage::PreTranslateMessage`。）|  
  
## 备注  
 `CMFCPropertyPage` 选件类表示属性表的各个页，也称为"选项"对话框。  
  
 与 [CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md) 选件类一起使用 `CMFCPropertyPage` 选件类。  若要在特性中使用菜单中的。`CMFCPropertyPage` 选件类调用，替换 `CPropertyPage` 选件类的所有匹配项。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CPropertyPage](../../mfc/reference/cpropertypage-class.md)  
  
 [CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)  
  
## 要求  
 **标头:** afxpropertypage.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCPropertySheet Class](../../mfc/reference/cmfcpropertysheet-class.md)
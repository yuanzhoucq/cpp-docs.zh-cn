---
title: "CMFCRibbonMainPanel Class | Microsoft Docs"
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
  - "CMFCRibbonMainPanel"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonMainPanel class"
ms.assetid: 1af78798-5e75-4365-9c81-a54aa5679602
caps.latest.revision: 23
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCRibbonMainPanel Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

实现了一个功能区面板何时单击 [CMFCRibbonApplicationButton](../../mfc/reference/cmfcribbonapplicationbutton-class.md)。  
  
## 语法  
  
```  
class CMFCRibbonMainPanel : public CMFCRibbonPanel  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|`CMFCRibbonMainPanel::CMFCRibbonMainPanel`|默认构造函数。|  
|`CMFCRibbonMainPanel::~CMFCRibbonMainPanel`|析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCRibbonMainPanel::Add](../Topic/CMFCRibbonMainPanel::Add.md)|添加一个功能区元素到应用程序按钮面板的左窗格上。  （重写 [CMFCRibbonPanel::Add](../Topic/CMFCRibbonPanel::Add.md)。）|  
|[CMFCRibbonMainPanel::AddRecentFilesList](../Topic/CMFCRibbonMainPanel::AddRecentFilesList.md)|添加文本字符串到最近使用的文件的列表菜单。|  
|[CMFCRibbonMainPanel::AddToBottom](../Topic/CMFCRibbonMainPanel::AddToBottom.md)|添加一个功能区元素到功能区应用程序面板的底部窗格中。|  
|[CMFCRibbonMainPanel::AddToRight](../Topic/CMFCRibbonMainPanel::AddToRight.md)|添加一个功能区元素到应用程序按钮面板的右窗格中。|  
|`CMFCRibbonMainPanel::CreateObject`|用于由框架创建此选件类类型动态实例。|  
|[CMFCRibbonMainPanel::GetCommandsFrame](../Topic/CMFCRibbonMainPanel::GetCommandsFrame.md)|返回表示功能区面板主要区域的矩形。|  
|`CMFCRibbonMainPanel::GetThisClass`|用于由框架获取指向与此选件类类型的 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 对象。|  
  
## 备注  
 当您打开应用程序面板时，框架显示 `CMFCRibbonMainPanel`。  它包含三个窗格:  
  
-   左窗格包含命令与文件，如 **打开**、 **保存**、 **打印**和 **关闭**。  若要将命令添加到此窗格，请调用 [CMFCRibbonMainPanel::Add](../Topic/CMFCRibbonMainPanel::Add.md)。  
  
-   右窗格包含修改命令在左窗格中单击的选项。  例如，因此，如果单击从左窗格中 **保存** ，右窗格可以显示可用的文件类型。  若要将项添加到此窗格，请调用 [CMFCRibbonMainPanel::AddToRight](../Topic/CMFCRibbonMainPanel::AddToRight.md)。  
  
-   下窗格包含允许您更改应用程序的设置并退出程序的按钮。  若要将项添加到此窗格，请调用 [CMFCRibbonMainPanel::AddToBottom](../Topic/CMFCRibbonMainPanel::AddToBottom.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonPanel](../../mfc/reference/cmfcribbonpanel-class.md)  
  
 [CMFCRibbonMainPanel](../../mfc/reference/cmfcribbonmainpanel-class.md)  
  
## 要求  
 **标头:** afxRibbonMainPanel.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonPanel Class](../../mfc/reference/cmfcribbonpanel-class.md)
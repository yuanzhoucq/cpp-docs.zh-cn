---
title: "CMFCRibbonApplicationButton Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCRibbonApplicationButton"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonApplicationButton class"
ms.assetid: beb81757-fabd-4641-9130-876ba8505b78
caps.latest.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 27
---
# CMFCRibbonApplicationButton Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

实现位于应用程序窗口的左上角特定按钮。  当单击按钮，打开通常包含与 **打开**、 **保存**和 **退出**的常见 **文件** 命令的菜单。  
  
## 语法  
  
```  
class CMFCRibbonApplicationButton : public CMFCRibbonButton  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMFCRibbonApplicationButton::CMFCRibbonApplicationButton](../Topic/CMFCRibbonApplicationButton::CMFCRibbonApplicationButton.md)|构造和初始化 `CMFCRibbonApplicationButton` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|`CMFCRibbonApplicationButton::CreateObject`|用于由框架创建此选件类类型动态实例。|  
|`CMFCRibbonApplicationButton::GetThisClass`|用于由框架获取指向与此选件类类型的 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 对象。|  
|[CMFCRibbonApplicationButton::SetImage](../Topic/CMFCRibbonApplicationButton::SetImage.md)|分配图像到功能区应用程序按钮。|  
  
## 示例  
 下面的示例在 `CMFCRibbonApplicationButton` 选件类演示如何使用各种方法。  此示例演示如何分配图像到应用程序按钮以及如何设置其工具提示。  此代码段是 [绘制客户端示例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_DrawClient#4](../../mfc/reference/codesnippet/CPP/cmfcribbonapplicationbutton-class_1.h)]  
[!code-cpp[NVC_MFC_DrawClient#5](../../mfc/reference/codesnippet/CPP/cmfcribbonapplicationbutton-class_2.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonApplicationButton](../../mfc/reference/cmfcribbonapplicationbutton-class.md)  
  
## 要求  
 **标头:** afxRibbonBar.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonButton Class](../../mfc/reference/cmfcribbonbutton-class.md)
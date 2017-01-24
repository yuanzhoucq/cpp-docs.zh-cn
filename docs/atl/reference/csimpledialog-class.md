---
title: "CSimpleDialog Class | Microsoft Docs"
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
  - "ATL::CSimpleDialog"
  - "CSimpleDialgo"
  - "CSimpleDialog"
  - "ATL.CSimpleDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSimpleDialog class"
  - "CSimpleDialog class, modal dialog boxes in ATL"
  - "对话框, 有模式"
  - "有模式对话框, ATL"
ms.assetid: 2ae65cc9-4f32-4168-aecd-200b4a480fdf
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSimpleDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类实现基本模式对话框。  
  
## 语法  
  
```  
  
      template <  
   WORD t_wDlgTemplateID,  
   BOOL t_bCenter = TRUE  
>  
class CSimpleDialog :  
   public CDialogImplBase  
```  
  
#### 参数  
 *t\_wDlgTemplateID*  
  
 对话框模板资源的ID。  
  
 *t\_bCenter*  
 **TRUE**，如果对话框对象将对所有者窗口;否则 **FALSE**。  
  
## 成员  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[CSimpleDialog::DoModal](../Topic/CSimpleDialog::DoModal.md)|创建一个模式对话框。|  
  
## 备注  
 实现具有基本功能的模式对话框。  `CSimpleDialog` 提供仅限Windows公共控件支持。  若要创建并显示模式对话框，请创建该选件类实例，提供了一个现有资源模板的名称为对话框。  对话框关闭对象，当用户单击与预定义值的所有控件\(例如IDOK或IDCANCEL\)。  
  
 `CSimpleDialog` 允许您创建仅模式对话框。  `CSimpleDialog` 对话框提供程序，则使用默认消息映射处理消息的适当处理程序。  
  
 请参见 [实现对话框](../../atl/implementing-a-dialog-box.md) 有关更多信息。  
  
## 继承层次结构  
 `CDialogImplBase`  
  
 `CSimpleDialog`  
  
## 要求  
 **Header:** atlwin.h  
  
## 请参阅  
 [Class Overview](../../atl/atl-class-overview.md)
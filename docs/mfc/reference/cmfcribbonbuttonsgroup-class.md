---
title: "CMFCRibbonButtonsGroup 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCRibbonButtonsGroup"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonButtonsGroup 类"
ms.assetid: b993d93e-fc1a-472f-a87f-1d7b7b499845
caps.latest.revision: 34
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 36
---
# CMFCRibbonButtonsGroup 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCRibbonButtonsGroup` 选件类允许您组织功能区按钮添加到组。  所有按钮的组中的水平直接在手指围绕并用在边框。  
  
## 语法  
  
```  
class CMFCRibbonButtonsGroup : public CMFCRibbonBaseElement  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[CMFCRibbonButtonsGroup::CMFCRibbonButtonsGroup](../Topic/CMFCRibbonButtonsGroup::CMFCRibbonButtonsGroup.md)|构造 `CMFCRibbonButtonsGroup` 对象。|  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[CMFCRibbonButtonsGroup::AddButton](../Topic/CMFCRibbonButtonsGroup::AddButton.md)|将一个按钮添加到组。|  
|[CMFCRibbonButtonsGroup::AddButtons](../Topic/CMFCRibbonButtonsGroup::AddButtons.md)|添加按钮列表添加到组。|  
|[CMFCRibbonButtonsGroup::GetButton](../Topic/CMFCRibbonButtonsGroup::GetButton.md)|返回指向位于指定索引的按钮。|  
|[CMFCRibbonButtonsGroup::GetCount](../Topic/CMFCRibbonButtonsGroup::GetCount.md)|在组中返回按钮数。|  
|[CMFCRibbonButtonsGroup::GetImageSize](../Topic/CMFCRibbonButtonsGroup::GetImageSize.md)|功能区上的组中返回常规映像的图像大小 \(重写 [CMFCRibbonBaseElement::GetImageSize](../Topic/CMFCRibbonBaseElement::GetImageSize.md)。\)|  
|[CMFCRibbonButtonsGroup::GetRegularSize](../Topic/CMFCRibbonButtonsGroup::GetRegularSize.md)|返回功能区元素的常规大小 \(重写 [CMFCRibbonBaseElement::GetRegularSize](../Topic/CMFCRibbonBaseElement::GetRegularSize.md)。\)|  
|[CMFCRibbonButtonsGroup::HasImages](../Topic/CMFCRibbonButtonsGroup::HasImages.md)|报表 `CMFCRibbonButtonsGroup` 对象是否包含工具栏图像。|  
|[CMFCRibbonButtonsGroup::OnDrawImage](../Topic/CMFCRibbonButtonsGroup::OnDrawImage.md)|绘制一个指定的按钮的相应图像，根据按钮是否正常，显示或禁用。|  
|[CMFCRibbonButtonsGroup::RemoveAll](../Topic/CMFCRibbonButtonsGroup::RemoveAll.md)|从 `CMFCRibbonButtonsGroup` 对象中移除所有按钮。|  
|[CMFCRibbonButtonsGroup::SetImages](../Topic/CMFCRibbonButtonsGroup::SetImages.md)|分配图像添加到组。|  
|[CMFCRibbonButtonsGroup::SetParentCategory](../Topic/CMFCRibbonButtonsGroup::SetParentCategory.md)|在其中设置 `CMFCRibbonButtonsGroup` 对象的父 `CMFCRibbonCategory` 和所有按钮 \(重写 [CMFCRibbonBaseElement::SetParentCategory](../Topic/CMFCRibbonBaseElement::SetParentCategory.md)。\)|  
  
## 备注  
 组从 [CMFCBaseRibbonElement](../../mfc/reference/cmfcribbonbaseelement-class.md) 派生，并且可以象处理单个实体。  在所有面板或弹出菜单可以确定组。  
  
## 示例  
 下面的示例在 `CMFCRibbonButtonsGroup` 选件类演示如何使用各种方法。  此示例演示如何构造 `CMFCRibbonButtonsGroup` 对象，分配图像到功能区按钮组和将按钮添加到功能区按钮组。  此代码段是 [绘制客户端示例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_DrawClient#2](../../mfc/reference/codesnippet/CPP/cmfcribbonbuttonsgroup-class_1.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButtonsGroup](../../mfc/reference/cmfcribbonbuttonsgroup-class.md)  
  
## 要求  
 **标头：** afxribbonbuttonsgroup.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)
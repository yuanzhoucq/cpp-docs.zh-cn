---
title: "CSnapInPropertyPageImpl Class | Microsoft Docs"
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
  - "CSnapInPropertyPageImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSnapInPropertyPageImpl class"
  - "属性页, ATL"
  - "snap-ins"
  - "snap-ins, 属性页"
ms.assetid: 75bdce5a-985e-4166-bd44-493132e023c4
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSnapInPropertyPageImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类为实现管理单元属性页对象的方法。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
CSnapInPropertyPageImpl : public CDialogImplBase  
  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CSnapInPropertyPageImpl::CSnapInPropertyPageImpl](../Topic/CSnapInPropertyPageImpl::CSnapInPropertyPageImpl.md)|构造函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CSnapInPropertyPageImpl::CancelToClose](../Topic/CSnapInPropertyPageImpl::CancelToClose.md)|更改 **好** 和 **Cancel** 按钮的状态。|  
|[CSnapInPropertyPageImpl::Create](../Topic/CSnapInPropertyPageImpl::Create.md)|初始化新创建的 `CSnapInPropertyPageImpl` 对象。|  
|[CSnapInPropertyPageImpl::OnApply](../Topic/CSnapInPropertyPageImpl::OnApply.md)|调用由结构，当用户单击 **现在应用** 按钮，当使用一个向导类型的属性表时。|  
|[CSnapInPropertyPageImpl::OnHelp](../Topic/CSnapInPropertyPageImpl::OnHelp.md)|调用由结构，当用户单击 **Help** 按钮，当使用一个向导类型的属性表时。|  
|[CSnapInPropertyPageImpl::OnKillActive](../Topic/CSnapInPropertyPageImpl::OnKillActive.md)|调用由结构，在当前页不再处于活动状态。|  
|[CSnapInPropertyPageImpl::OnQueryCancel](../Topic/CSnapInPropertyPageImpl::OnQueryCancel.md)|调用由结构，当用户单击"取消"按钮，因此，在该取消操作之前。|  
|[CSnapInPropertyPageImpl::OnReset](../Topic/CSnapInPropertyPageImpl::OnReset.md)|调用由结构，当用户单击重置按钮，当使用一个向导类型的属性表时。|  
|[CSnapInPropertyPageImpl::OnSetActive](../Topic/CSnapInPropertyPageImpl::OnSetActive.md)|调用由结构，在当前页变为活动状态。|  
|[CSnapInPropertyPageImpl::OnWizardBack](../Topic/CSnapInPropertyPageImpl::OnWizardBack.md)|调用由结构，当用户单击**Back** 按钮，当使用一个向导类型的属性表时。|  
|[CSnapInPropertyPageImpl::OnWizardFinish](../Topic/CSnapInPropertyPageImpl::OnWizardFinish.md)|调用由结构，当用户单击 **Finish** 按钮，当使用一个向导类型的属性表时。|  
|[CSnapInPropertyPageImpl::OnWizardNext](../Topic/CSnapInPropertyPageImpl::OnWizardNext.md)|调用由结构，当用户单击 `Next` 按钮，当使用一个向导类型的属性表时。|  
|[CSnapInPropertyPageImpl::QuerySiblings](../Topic/CSnapInPropertyPageImpl::QuerySiblings.md)|向前为属性表的任何页面的当前消息。|  
|[CSnapInPropertyPageImpl::SetModified](../Topic/CSnapInPropertyPageImpl::SetModified.md)|调用激活或停用 **现在应用** 按钮。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CSnapInPropertyPageImpl::m\_psp](../Topic/CSnapInPropertyPageImpl::m_psp.md)|`CSnapInPropertyPageImpl` 对象使用的Windows **PROPSHEETPAGE** 结构。|  
  
## 备注  
 `CSnapInPropertyPageImpl` 用于管理格属性页对象提供了一个基本的实现。  使用几种不同的接口和映射类型，管理单元属性页的基本功能实现。  
  
## 继承层次结构  
 `CDialogImplBase`  
  
 `CSnapInPropertyPageImpl`  
  
## 要求  
 **Header:** atlsnap.h  
  
## 请参阅  
 [Class Overview](../../atl/atl-class-overview.md)
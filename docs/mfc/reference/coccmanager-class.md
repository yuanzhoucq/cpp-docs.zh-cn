---
title: "COccManager Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COccManager"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX 控件容器 [C++], control site"
  - "CNoTrackObject class"
  - "COccManager class"
  - "自定义控件 [MFC], sites"
ms.assetid: 7d47aeed-d1ab-48e3-b4cf-d429718e370a
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# COccManager Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

管理多个自定义控件站点;实现由 `COleControlContainer` 和 `COleControlSite` 对象。  
  
## 语法  
  
```  
class COccManager : public CNoTrackObject  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[COccManager::CreateContainer](../Topic/COccManager::CreateContainer.md)|创建一 **COleContainer** 对象。|  
|[COccManager::CreateDlgControls](../Topic/COccManager::CreateDlgControls.md)|创建ActiveX控件，承载的关联的 `COleContainer` 对象。|  
|[COccManager::CreateSite](../Topic/COccManager::CreateSite.md)|创建一个 `COleClientSite` 对象。|  
|[COccManager::GetDefBtnCode](../Topic/COccManager::GetDefBtnCode.md)|检索默认按钮的代码。|  
|[COccManager::IsDialogMessage](../Topic/COccManager::IsDialogMessage.md)|确定对话框消息的目标。|  
|[COccManager::IsLabelControl](../Topic/COccManager::IsLabelControl.md)|确定指定的控件是否标签控件。|  
|[COccManager::IsMatchingMnemonic](../Topic/COccManager::IsMatchingMnemonic.md)|确定当前助记键是否满足指定控件的助记键。|  
|[COccManager::OnEvent](../Topic/COccManager::OnEvent.md)|要处理的尝试指定的操作。|  
|[COccManager::PostCreateDialog](../Topic/COccManager::PostCreateDialog.md)|释放在对话框创建时分配的资源。|  
|[COccManager::PreCreateDialog](../Topic/COccManager::PreCreateDialog.md)|处理ActiveX控件中的对话框模板。|  
|[COccManager::SetDefaultButton](../Topic/COccManager::SetDefaultButton.md)|切换为指定控件的默认状态。|  
|[COccManager::SplitDialogTemplate](../Topic/COccManager::SplitDialogTemplate.md)|在指定的对话框模板的公共控件分隔任何现有的ActiveX控件。|  
  
## 备注  
 基类，**CNoTrackObject**，是未记录的基类\(位于AFXTLS.H）。  设计应用程序结构使用，从 **CNoTrackObject** 选件类派生的选件类从内存泄漏检测是执行。  建议不要直接从 **CNoTrackObject**派生。  
  
## 继承层次结构  
 `CNoTrackObject`  
  
 `COccManager`  
  
## 要求  
 **Header:** afxocc.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleControlSite Class](../../mfc/reference/colecontrolsite-class.md)   
 [COleControlContainer Class](../../mfc/reference/colecontrolcontainer-class.md)
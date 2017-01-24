---
title: "CMFCCmdUsageCount Class | Microsoft Docs"
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
  - "CMFCCmdUsageCount"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCCmdUsageCount class"
ms.assetid: 9c33b783-37c0-43ea-9f31-3c75e246c841
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCCmdUsageCount Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

当用户选择一个项目从菜单时，跟踪使用计数Windows消息，例如。  
  
## 语法  
  
```  
class CMFCCmdUsageCount : public CObject  
```  
  
## 成员  
  
### 公共构造函数  
  
|||  
|-|-|  
|名称|说明|  
|`CMFCCmdUsageCount::CMFCCmdUsageCount`|默认构造函数。|  
|`CMFCCmdUsageCount::~CMFCCmdUsageCount`|析构函数。|  
  
### 公共方法  
  
|||  
|-|-|  
|名称|说明|  
|[CMFCCmdUsageCount::AddCmd](../Topic/CMFCCmdUsageCount::AddCmd.md)|由一个递增的方式与该特定命令的计数器。|  
|[CMFCCmdUsageCount::GetCount](../Topic/CMFCCmdUsageCount::GetCount.md)|检索与给定的命令ID.的使用计数|  
|[CMFCCmdUsageCount::HasEnoughInformation](../Topic/CMFCCmdUsageCount::HasEnoughInformation.md)|确定此对象是否收集最小量跟踪数据。|  
|[CMFCCmdUsageCount::IsFreqeuntlyUsedCmd](../Topic/CMFCCmdUsageCount::IsFreqeuntlyUsedCmd.md)|确定是否通常使用给定的命令。|  
|[CMFCCmdUsageCount::Reset](../Topic/CMFCCmdUsageCount::Reset.md)|清除使用计数所有命令。|  
|[CMFCCmdUsageCount::Serialize](../Topic/CMFCCmdUsageCount::Serialize.md)|读取存档或写入的此对象到存档。  （重写 [CObject::Serialize](../Topic/CObject::Serialize.md)。）|  
|[CMFCCmdUsageCount::SetOptions](../Topic/CMFCCmdUsageCount::SetOptions.md)|一组共享 `CMFCCmdUsageCount` 选件类数据成员的值。|  
  
### 数据成员  
  
|||  
|-|-|  
|名称|说明|  
|`m_CmdUsage`|`CMap` 对象对它们的用法的映射命令计数。|  
|`m_nMinUsagePercentage`|命令的最小使用百分比通常能够使用。|  
|`m_nStartCount`|用于确定的启动计数器此对象是否收集最小量跟踪数据。|  
|`m_nTotalUsage`|显示所有跟踪的命令。|  
  
### 备注  
 `CMFCCmdUsageCount` 选件类映射每个数字Windows消息标识符为32位无符号整数计数器。  `CMFCToolBar` 使用此选件类公开常用的工具栏项。  有关 `CMFCToolBar`的更多信息，请参见[CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md)。  
  
 可以保留之间的数据运行您的程序的 `CMFCCmdUsageCount` 选件类。  使用 [CMFCCmdUsageCount::Serialize](../Topic/CMFCCmdUsageCount::Serialize.md) 方法序列化选件类成员数据和 [CMFCCmdUsageCount::SetOptions](../Topic/CMFCCmdUsageCount::SetOptions.md) 方法设置共享成员数据。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCCmdUsageCount](../../mfc/reference/cmfccmdusagecount-class.md)  
  
## 要求  
 **标头:** afxcmdusagecount.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md)
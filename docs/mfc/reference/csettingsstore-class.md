---
title: "CSettingsStore Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CSettingsStore"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSettingsStore class"
ms.assetid: 0ea181de-a13e-4b29-b560-7c43838223ff
caps.latest.revision: 29
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 31
---
# CSettingsStore Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

包装Windows API函数，提供用于访问注册表的一个面向对象的接口。  
  
## 语法  
  
```  
class CSettingsStore : public CObject  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CSettingsStore::CSettingsStore](../Topic/CSettingsStore::CSettingsStore.md)|构造 `CSettingsStore` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CSettingsStore::Close](../Topic/CSettingsStore::Close.md)|关闭打开注册表项。|  
|[CSettingsStore::CreateKey](../Topic/CSettingsStore::CreateKey.md)|如果不存在，打开指定的键或创建它。|  
|[CSettingsStore::DeleteKey](../Topic/CSettingsStore::DeleteKey.md)|删除指定的密钥及其所有子级。|  
|[CSettingsStore::DeleteValue](../Topic/CSettingsStore::DeleteValue.md)|删除打开键的指定值。|  
|[CSettingsStore::Open](../Topic/CSettingsStore::Open.md)|打开指定的键。|  
|[CSettingsStore::Read](../Topic/CSettingsStore::Read.md)|检索数据为指定的键值。|  
|[CSettingsStore::Write](../Topic/CSettingsStore::Write.md)|写入注册表的值在打开项下。|  
  
## 备注  
 成员函数 `CreateKey` 和 `Open` 非常相似。  如果注册表项已存在，`CreateKey` 和类似地 `Open` 功能。  但是，因此，如果注册表项不存在，`CreateKey` 将创建它，而 `Open` 将返回false值。  
  
## 示例  
 下面的示例演示如何使用打开并读取 `CSettingsStore` 选件类的方法。  此代码段是 [工具提示演示示例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_ToolTipDemo#1](../../mfc/reference/codesnippet/CPP/csettingsstore-class_1.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CSettingsStore](../../mfc/reference/csettingsstore-class.md)  
  
## 要求  
 **标头:** afxsettingsstore.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CWinAppEx Class](../../mfc/reference/cwinappex-class.md)
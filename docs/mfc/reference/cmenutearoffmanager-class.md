---
title: "CMenuTearOffManager Class | Microsoft Docs"
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
  - "CMenuTearOffManager"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMenuTearOffManager class"
ms.assetid: ab7ca272-ce42-4678-95f7-6ad75038f5a0
caps.latest.revision: 31
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMenuTearOffManager Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

管理拖曳菜单。  拖曳菜单是在菜单栏上的菜单。  用户可以从菜单栏移除拖曳菜单，从而拖曳菜单浮动。  
  
## 语法  
  
```  
class CMenuTearOffManager : public CObject  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMenuTearOffManager::CMenuTearOffManager](../Topic/CMenuTearOffManager::CMenuTearOffManager.md)|构造 `CMenuTearOffManager` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMenuTearOffManager::Build](../Topic/CMenuTearOffManager::Build.md)||  
|[CMenuTearOffManager::GetRegPath](../Topic/CMenuTearOffManager::GetRegPath.md)||  
|[CMenuTearOffManager::Initialize](../Topic/CMenuTearOffManager::Initialize.md)|初始化 `CMenuTearOffManager` 对象。|  
|[CMenuTearOffManager::IsDynamicID](../Topic/CMenuTearOffManager::IsDynamicID.md)||  
|[CMenuTearOffManager::Parse](../Topic/CMenuTearOffManager::Parse.md)||  
|[CMenuTearOffManager::Reset](../Topic/CMenuTearOffManager::Reset.md)||  
|[CMenuTearOffManager::SetInUse](../Topic/CMenuTearOffManager::SetInUse.md)||  
|[CMenuTearOffManager::SetupTearOffMenus](../Topic/CMenuTearOffManager::SetupTearOffMenus.md)||  
  
## 备注  
 为了使用请拖曳在应用程序的菜单，您必须具有 `CMenuTearOffManager` 对象。  在大多数情况下，可能不会直接创建也不会初始化一 `CMenuTearOffManager` 对象。  在调用 [CWinAppEx::EnableTearOffMenus](../Topic/CWinAppEx::EnableTearOffMenus.md) 函数时，这对于已处理。  
  
## 示例  
 下面的示例演示如何通过调用 `CWinAppEX::EnableTearOffMenus` 方法来构造和初始化 `CMenuTearOffManager` 对象。  此代码段是 [Word填充示例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_WordPad#12](../../mfc/reference/codesnippet/CPP/cmenutearoffmanager-class_1.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMenuTearOffManager](../../mfc/reference/cmenutearoffmanager-class.md)  
  
## 要求  
 **标头:** afxmenutearoffmanager.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CWinAppEx Class](../../mfc/reference/cwinappex-class.md)
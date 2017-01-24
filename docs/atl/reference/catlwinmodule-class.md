---
title: "CAtlWinModule Class | Microsoft Docs"
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
  - "ATL::CAtlWinModule"
  - "ATL.CAtlWinModule"
  - "CAtlWinModule"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAtlWinModule class"
ms.assetid: 7ec844af-0f68-4a34-b0c8-9de50a025df0
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAtlWinModule Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类提供ATL多窗口元素支持。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
class CAtlWinModule : public _ATL_WIN_MODULE  
  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CAtlWinModule::CAtlWinModule](../Topic/CAtlWinModule::CAtlWinModule.md)|构造函数。|  
|[CAtlWinModule::~CAtlWinModule](../Topic/CAtlWinModule::~CAtlWinModule.md)|该析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CAtlWinModule::AddCreateWndData](../Topic/CAtlWinModule::AddCreateWndData.md)|添加数据对象。|  
|[CAtlWinModule::ExtractCreateWndData](../Topic/CAtlWinModule::ExtractCreateWndData.md)|返回指向窗口模块数据对象。|  
  
## 备注  
 此选件类提供对需要多窗口函数的所有ATL选件类支持。  
  
## 继承层次结构  
 [\_ATL\_WIN\_MODULE](../Topic/_ATL_WIN_MODULE.md)  
  
 `CAtlWinModule`  
  
## 要求  
 **Header:** atlbase.h  
  
## 请参阅  
 [\_ATL\_WIN\_MODULE](../Topic/_ATL_WIN_MODULE.md)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [Module 类](../../atl/atl-module-classes.md)
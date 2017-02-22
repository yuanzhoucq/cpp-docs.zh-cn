---
title: "CWinTraitsOR Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CWinTraitsOR"
  - "ATL::CWinTraitsOR"
  - "CWinTraitsOR"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CWinTraitsOR class"
  - "window styles, default values for ATL"
ms.assetid: 1eb7b1e8-a9bd-411b-a30a-35a8a10af989
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CWinTraitsOR Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在创建windows对象时，此选件类出于标准化使用的样式提供方法。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
      template <  
DWORD t_dwStyle= 0,  
DWORDt_dwExStyle= 0,  
class TWinTraits = CControlWinTraits   
>  
class CWinTraitsOR  
```  
  
#### 参数  
 `t_dwStyle`  
 默认窗口样式。  
  
 `t_dwExStyle`  
 默认扩展窗口样式。  
  
## 成员  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[CWinTraitsOR::GetWndExStyle](../Topic/CWinTraitsOR::GetWndExStyle.md)|检索 `CWinTraitsOR` 对象的扩展样式。|  
|[CWinTraitsOR::GetWndStyle](../Topic/CWinTraitsOR::GetWndStyle.md)|检索 `CWinTraitsOR` 对象的标准样式。|  
  
## 备注  
 此 [窗口特征](../../atl/understanding-window-traits.md) 选件类出于标准化用于ATL窗口创建该对象的样式提供简单的方法。  使用此选件类的专用化作为模板参数传递到 [CWindowImpl](../../atl/reference/cwindowimpl-class.md) 或其他ATL的窗口选件类指定最小为该窗口选件类实例将使用的一组标准和扩展样式。  
  
 请使用此模板的专用化，如果要确保特定样式为windows选件类的所有实例设置，并允许其他样式设置基于在调用每个基类型到 [CWindowImpl::Create](../Topic/CWindowImpl::Create.md)时。  
  
 如果要提供默认值将使用的windows样式，仅当其他样式到 `CWindowImpl::Create`时的调用未指定，请使用 [CWinTraits](../../atl/reference/cwintraits-class.md)。  
  
## 要求  
 **Header:** atlwin.h  
  
## 请参阅  
 [Class Overview](../../atl/atl-class-overview.md)   
 [Understanding Window Traits](../../atl/understanding-window-traits.md)
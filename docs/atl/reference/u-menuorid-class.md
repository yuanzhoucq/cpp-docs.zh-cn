---
title: "_U_MENUorID Class | Microsoft Docs"
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
  - "ATL._U_MENUorID"
  - "ATL::_U_MENUorID"
  - "_U_MENUorID"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_U_MENUorID class"
  - "U_MENUorID class"
ms.assetid: cfc8032b-61b4-4a68-ba3a-92b82500ccae
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _U_MENUorID Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类。**CreateWindow** 和 **CreateWindowEx**提供包装。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
class _U_MENUorID  
  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[\_U\_MENUorID::\_U\_MENUorID](../Topic/_U_MENUorID::_U_MENUorID.md)|构造函数。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[\_U\_MENUorID::m\_hMenu](../Topic/_U_MENUorID::m_hMenu.md)|对菜单的句柄。|  
  
## 备注  
 此参数适配器选件类允许ID \(**UINT**属于\)或菜单句柄\(`HMENU`属于\)将传递给函数，而不需要显式强制转换在被调用方。  
  
 此选件类为实现特定的Windows API、 [CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679) 和 [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) 功能的包装模型，这两个接受 `HMENU` 参数可以是子窗口标识符\(**UINT**\)而不是"菜单句柄。  例如，您可以看到此选件类正在使用作为参数传递给 [CWindowImpl::Create](../Topic/CWindowImpl::Create.md)。  
  
 选件类定义两个构造函数重载:一 **UINT** 接受参数，另一个接受 `HMENU` 参数。  **UINT** 参数转换为在选件类的单个数据成员和结果的 `HMENU` 存储的构造函数，[m\_hMenu](../Topic/_U_MENUorID::m_hMenu.md)。  为 `HMENU` 构造函数的参数存储直接，不进行转换。  
  
## 要求  
 **Header:** atlwin.h  
  
## 请参阅  
 [Class Overview](../../atl/atl-class-overview.md)
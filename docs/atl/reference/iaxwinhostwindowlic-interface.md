---
title: "IAxWinHostWindowLic Interface | Microsoft Docs"
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
  - "IAxWinHostWindowLic"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IAxWinHostWindowLic interface"
ms.assetid: 750f1520-6bce-428c-aca0-fccbe3f063c7
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IAxWinHostWindowLic Interface
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此接口用于操作一个授权控件与其宿主对象的方法。  
  
## 语法  
  
```  
  
interface IAxWinHostWindowLic : IAxWinHostWindow  
  
```  
  
## 成员  
  
### 方法  
  
|||  
|-|-|  
|[CreateControlLic](../Topic/IAxWinHostWindowLic::CreateControlLic.md)|创建一个授权控件并将它附加到宿主对象。|  
|[CreateControlLicEx](../Topic/IAxWinHostWindowLic::CreateControlLicEx.md)|创建一个授权控件，附加到宿主对象并选择性地将事件处理程序。|  
  
## 备注  
 `IAxWinHostWindowLic` 从 [IAxWinHostWindow](../../atl/reference/iaxwinhostwindow-interface.md) 继承并添加支持授权控件的创建方法。  
  
 使用此接口成员的示例 [承载使用ATL AXHost的ActiveX控件](../../atl/hosting-activex-controls-using-atl-axhost.md) 参见。  
  
## 要求  
 此接口的定义可用作IDL或C\+\+，如下所示。  
  
|定义类型|文件|  
|----------|--------|  
|IDL|ATLIFace.idl|  
|C\+\+|ATLIFace.h \(也包括在ATLBase.h\)|
---
title: "IAxWinHostWindow Interface | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "IAxWinHostWindow"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IAxWinHostWindow interface"
ms.assetid: 9821c035-cd52-4c46-b58a-9278064f09b4
caps.latest.revision: 21
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IAxWinHostWindow Interface
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此接口用于操作控件与其宿主对象的方法。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]执行的应用程序。  
  
## 语法  
  
```  
  
interface IAxWinHostWindow : IUnknown  
  
```  
  
## 成员  
  
### 方法  
  
|||  
|-|-|  
|[AttachControl](../Topic/IAxWinHostWindow::AttachControl.md)|将现有控件绑定到宿主对象。|  
|[CreateControl](../Topic/IAxWinHostWindow::CreateControl.md)|创建控件并将其附加到宿主对象。|  
|[CreateControlEx](../Topic/IAxWinHostWindow::CreateControlEx.md)|创建一个控件，将其附加到宿主对象并选择性地将事件处理程序。|  
|[QueryControl](../Topic/IAxWinHostWindow::QueryControl.md)|返回接口指针传递给承载控件。|  
|[SetExternalDispatch](../Topic/IAxWinHostWindow::SetExternalDispatch.md)|设置外部 `IDispatch` 接口。|  
|[SetExternalUIHandler](../Topic/IAxWinHostWindow::SetExternalUIHandler.md)|设置外部 `IDocHostUIHandlerDispatch` 接口。|  
  
## 备注  
 此接口由ATL的承载对象的ActiveX控件显示。  当承载浏览器时，请调用此接口的方法创建和\/或控件附加到宿主对象，以便从承载的控件的接口，或将外部调度接口或UI处理程序中使用。  
  
## 要求  
 此接口的定义可用作IDL或C\+\+，如下所示。  
  
|定义类型|文件|  
|----------|--------|  
|IDL|ATLIFace.idl|  
|C\+\+|ATLIFace.h \(也包括在ATLBase.h\)|  
  
## 请参阅  
 [IAxWinAmbientDispatch Interface](../../atl/reference/iaxwinambientdispatch-interface.md)   
 [CAxWindow::QueryHost](../Topic/CAxWindow::QueryHost.md)   
 [AtlAxGetHost](../Topic/AtlAxGetHost.md)
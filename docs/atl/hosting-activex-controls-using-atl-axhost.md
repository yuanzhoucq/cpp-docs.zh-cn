---
title: "Hosting ActiveX Controls Using ATL AXHost | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX 控件 [C++], hosting"
  - "AXHost method"
  - "Calendar control (ActiveX)"
  - "Calendar control (ActiveX), hosting with ATL AXHost"
  - "CAxWindow2T class"
  - "承载 ActiveX 控件"
ms.assetid: 2c1200ec-effb-4814-820a-509519699468
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Hosting ActiveX Controls Using ATL AXHost
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用各种ATL功能，本主题中的示例演示如何创建AXHost以及如何承载ActiveX控件。  它还演示如何访问控件和接收事件\(使用 [IDispEventImpl](../atl/reference/idispeventimpl-class.md)\)与承载控件。  该示例承载日历控件在一个主窗口或在子窗口。  
  
 请注意 `USE_METHOD` 符号的定义。  可以更改此符号值更改介于1和8.之间。  符号的值决定控件如何将创建:  
  
-   为创建宿主子类的 `USE_METHOD`，调用偶数值窗口并将其强制转换为宿主控件。  为奇数值，则代码将创建为宿主的子窗口。  
  
-   对于 `USE_METHOD` 的值介于1和4之间的，则对该控件的访问和接收事件在同时创建宿主调用完成。  在5和8之间的值查询接口的宿主并将该接收器。  
  
 这是摘要:  
  
|USE\_METHOD|主机|控件访问和事件接收|将演示的功能|  
|-----------------|--------|---------------|------------|  
|1|子窗口|一个步骤|CreateControlLicEx|  
|2|主窗口|一个步骤|AtlAxCreateControlLicEx|  
|3|子窗口|一个步骤|CreateControlEx|  
|4|主窗口|一个步骤|AtlAxCreateControlEx|  
|5|子窗口|多个步骤|CreateControlLic|  
|6|主窗口|多个步骤|AtlAxCreateControlLic|  
|7|子窗口|多个步骤|CreateControl|  
|8|主窗口|多个步骤|AtlAxCreateControl|  
  
 [!code-cpp[NVC_ATL_AxHost#1](../atl/codesnippet/CPP/hosting-activex-controls-using-atl-axhost_1.cpp)]  
  
## 请参阅  
 [控件包含常见问题](../atl/atl-control-containment-faq.md)   
 [AtlAxCreateControl](../Topic/AtlAxCreateControl.md)   
 [AtlAxCreateControlEx](../Topic/AtlAxCreateControlEx.md)   
 [AtlAxCreateControlLic](../Topic/AtlAxCreateControlLic.md)   
 [AtlAxCreateControlLicEx](../Topic/AtlAxCreateControlLicEx.md)   
 [CAxWindow2T Class](../atl/reference/caxwindow2t-class.md)   
 [IAxWinHostWindowLic Interface](../atl/reference/iaxwinhostwindowlic-interface.md)